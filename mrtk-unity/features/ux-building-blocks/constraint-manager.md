---
title: Gerenciador de restrição
description: Visão geral sobre o Gerenciador de restrições no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f32f7321ec30f337e03d006f47fa92639796a74156483917331304811ea86a45
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198458"
---
# <a name="constraint-manager"></a>Gerenciador de restrição

O Gerenciador de restrição permite aplicar um conjunto de componentes de restrição a uma transformação. Os componentes do tipo [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) anexados ao objeto do jogo podem ser levados em consideração.
Por padrão, o Gerenciador de restrição coletará automaticamente todos os [componentes de restrição](#transform-constraints) anexados ao objeto de jogo e os aplicará a transformações processadas.
No entanto, os usuários podem optar por configurar a lista de restrições aplicadas manualmente e permitir que apenas um subconjunto de restrições anexadas seja aplicado.

Atualmente, os seguintes elementos do MRTK UX têm suporte para o Gerenciador de restrição:

- [Controle de limites](bounds-control.md)
- [Manipulador de objetos](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>Propriedades e campos do Inspetor

O Gerenciador de restrição pode ser operado em dois modos:

- Seleção de restrição automática
- Seleção de restrição manual

### <a name="auto-constraint-selection"></a>Seleção de restrição automática

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

O modo padrão de Gerenciador de restrição, seleção de restrição automática, fornecerá uma lista de todos os componentes de restrição anexados, bem como os [botões](#go-to-component) e um [botão Adicionar restrição](#add-constraint-to-game-object).

#### <a name="add-constraint-to-game-object"></a>Adicionar restrição ao objeto de jogo

Esse botão permite que um componente de restrição seja adicionado diretamente do Inspetor do Gerenciador de restrição. Todos os tipos de restrição em um projeto devem ser visíveis aqui. Consulte [transformar restrições](#transform-constraints) para obter mais informações.

#### <a name="go-to-component"></a>Ir para o componente

Todas as restrições encontradas no objeto colocará ser listadas aqui com um botão *ir para componente* . Esse botão fará com que o Inspetor role para o componente de restrição selecionado para que ele possa ser configurado.

### <a name="manual-constraint-selection"></a>Seleção de restrição manual

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

Se o Gerenciador de restrição estiver definido como modo manual, somente as restrições vinculadas na lista de restrições serão processadas e aplicadas à transformação. A lista exibida mostrará apenas as restrições selecionadas pelo usuário, bem como [ir para botões](#go-to-component) ou opções para remover ou adicionar entradas.
Ao habilitar o modo manual pela primeira vez, o Gerenciador de restrição preencherá a lista todos os componentes disponíveis como um ponto de partida para selecionar componentes de restrição anexados.

### <a name="remove-entry"></a>Remover entrada

Isso remove a entrada da lista selecionada manualmente. Observe que essa opção não removerá o componente de restrição do objeto Game. Os componentes de restrição sempre precisam ser removidos manualmente para garantir que não quebre acidentalmente nenhum outro componente que se refira a esse componente.

### <a name="add-entry"></a>Adicionar entrada

Adicionar entrada abrirá uma lista suspensa mostrando todos os componentes de restrição disponíveis que ainda não estão na lista manual. Ao clicar em qualquer uma das entradas, o componente será adicionado à seleção de restrição manual.

### <a name="add-new-constraint"></a>Adicionar nova restrição

Esta opção adicionará um componente do tipo selecionado ao objeto de jogo e adicionará o componente de restrição recém-criado à lista de restrições manual.

## <a name="transform-constraints"></a>Restrições de transformação

As restrições podem ser usadas para limitar a manipulação de alguma forma. Por exemplo, alguns aplicativos podem exigir rotação, mas também exigem que o objeto permaneça em posição vertical. Nesse caso, um `RotationAxisConstraint` pode ser adicionado ao objeto e usado para limitar a rotação à rotação do eixo y. O MRTK fornece várias restrições, todas descritas abaixo.

Também é possível definir novas restrições e usá-las para criar um comportamento de manipulação exclusivo que pode ser necessário para alguns aplicativos. Para fazer isso, crie um script que herde de [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) e implemente a `ConstraintType` Propriedade abstract e o método abstract `ApplyConstraint` . Ao adicionar uma nova restrição ao objeto, ele deve restringir a manipulação da maneira definida. Essa nova restrição também deve ser mostrada na [seleção automática](#auto-constraint-selection) do Gerenciador de restrição ou na lista suspensa [Adicionar entrada](#add-entry) no modo manual.

Todas as restrições fornecidas pelo MRTK compartilham as seguintes propriedades:

#### <a name="hand-type"></a>Tipo de mão

Especifica se a restrição é usada para uma única, duas mãos ou ambos os tipos de manipulação. Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.

- *Uma das mãos*: a restrição será usada durante uma manipulação de mão, se selecionado.
- *Duas mãos*: a restrição será usada durante a manipulação de duas mãos, se selecionado.

#### <a name="proximity-type"></a>Tipo de proximidade

Especifica se a restrição é usada para quase, longe ou ambos os tipos de manipulação. Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.

- *Próximo*: a restrição será usada durante a manipulação próxima se selecionada.
- *Longe*: a restrição será usada durante a manipulação extrema, se selecionada.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

Quando essa restrição é anexada a um objeto, a rotação será limitada, de modo que o objeto sempre irá encarar o usuário. Isso é útil para slates ou painéis. As propriedades para `FaceUserConstraint` são as seguintes:

#### <a name="face-away"></a>Face para fora

O objeto se afasta do usuário se for verdadeiro.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

Essa restrição corrige a distância entre o objeto manipulado e outra transformação de objeto no início da manipulação. Isso é útil para comportamentos, como corrigir a distância do objeto manipulado para a transformação de cabeçalho. As propriedades para `FixedDistanceConstraint` são as seguintes:

#### <a name="constraint-transform"></a>Transformação de restrição

Essa é a outra transformação à qual o objeto manipulado terá uma distância fixa. O padrão é a transformação da câmera.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

Essa restrição corrige a rotação relativa entre o usuário e o objeto manipulado enquanto ele está sendo manipulado. Isso é útil para slates ou painéis, pois garante que o objeto manipulado sempre mostre a mesma face ao usuário como fazia no início da manipulação. O `FixedRotationToUserConstraint` não tem nenhuma propriedade exclusiva.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

Essa restrição corrige a rotação global do objeto manipulado enquanto ele está sendo manipulado. Isso pode ser útil em casos em que nenhuma rotação deve ser imparte pela manipulação. O `FixedRotationToWorldConstraint` não tem nenhuma propriedade exclusiva:

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

Quando essa restrição é anexada a um objeto, não importa o quanto o objeto é do usuário, ele manterá o mesmo tamanho aparente para o usuário (ou seja, ele ocupará a mesma proporção do campo de exibição do usuário). Isso pode ser usado para garantir que um Tablet ou painel de texto permaneça legível durante a manipulação. O `MaintainApparentSizeConstraint` não tem nenhuma propriedade exclusiva:

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

Essa restrição pode ser usada para corrigir ao longo de quais eixos um objeto manipulado pode ser movido. Isso pode ser útil para manipular objetos na superfície de um plano ou ao longo de uma linha. As propriedades para `MoveAxisConstraint` são as seguintes:

#### <a name="constraint-on-movement"></a>Restrição no movimento

Especifica em quais eixos o movimento deve ser impedido. Por padrão, esses eixos serão globais em vez de locais, mas isso pode ser alterado abaixo. Como essa propriedade é um sinalizador, qualquer número de opções pode ser selecionado.

- *Eixo x*: a movimentação ao longo do eixo x é restrita se selecionada.
- *Eixo y*: a movimentação ao longo do eixo y é restrita se selecionada.
- *Eixo z*: a movimentação ao longo do eixo z é restrita se selecionada.

#### <a name="use-local-space-for-constraint"></a>Usar espaço local para restrição

Restringirá os eixos de transformação local do objeto manipulado, se for verdadeiro. Falso por padrão.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

Essa restrição pode ser usada para corrigir sobre quais eixos um objeto manipulado pode ser girado. Isso pode ser útil para manter um objeto manipulado verticalmente, mas ainda permitindo rotações do eixo y, por exemplo. As propriedades para `RotationAxisConstraint` são as seguintes:

#### <a name="constraint-on-rotation"></a>Restrição na rotação

Especifica sobre quais eixos evitar a rotação. Por padrão, esses eixos serão globais em vez de locais, mas isso pode ser alterado abaixo. Como essa propriedade é um sinalizador, qualquer número de opções pode ser selecionado.

- *Eixo Y:* a rotação sobre o eixo y é restrita se selecionada.
- *Eixo Z:* a rotação sobre o eixo z é restrita se selecionada.
- *Eixo X:* a rotação sobre o eixo x é restrita se selecionada.

#### <a name="use-local-space-for-constraint"></a>Usar espaço local para restrição

Restringirá os eixos de transformação local do objeto manipulado se for true. Falso por padrão.

### <a name="minmaxscaleconstraint"></a>MinMaxScaleConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

Essa restrição permite que os valores mínimo e máximo sejam definidos para a escala do objeto manipulado. Isso é útil para impedir que os usuários dimensionem um objeto muito pequeno ou muito grande. As propriedades para `MinMaxScaleConstraint` são as a seguir:

#### <a name="scale-minimum"></a>Dimensionar o mínimo

O valor de escala mínimo durante a manipulação.

#### <a name="scale-maximum"></a>Dimensionar o máximo

O valor de escala máximo durante a manipulação.

#### <a name="relative-to-initial-state"></a>Relativo ao estado inicial

Se true, os valores acima serão interpretados como relativos à escala inicial dos objetos. Caso contrário, eles serão interpretados como valores de escala absolutos.
