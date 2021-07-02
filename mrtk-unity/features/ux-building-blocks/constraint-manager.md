---
title: Gerenciador de restrições
description: Visão geral sobre o Gerenciador de Restrições no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 7036bb552952a0e45a8ba465d769a8952e48bc36
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177553"
---
# <a name="constraint-manager"></a>Gerenciador de restrições

O gerenciador de restrições permite aplicar um conjunto de componentes de restrição a uma transformação. Componentes do [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) tipo anexados ao objeto de jogo podem ser considerados.
Por padrão, o gerenciador de restrições coletará automaticamente todos os componentes [de](#transform-constraints) restrição anexados ao objeto de jogo e os aplicará às transformação processadas.
No entanto, os usuários podem optar por configurar a lista de restrições aplicadas manualmente e permitir que apenas um subconjunto de restrições anexadas seja aplicado.

Atualmente, os seguintes elementos de UX do MRTK estão dando suporte ao gerenciador de restrições:

- [Controle de limites](bounds-control.md)
- [Manipulador de objetos](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a>Propriedades e campos do inspetor

O gerenciador de restrições pode ser operado em dois modos:

- Seleção de restrição automática
- Seleção manual de restrição

### <a name="auto-constraint-selection"></a>Seleção de restrição automática

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

O modo padrão do gerenciador de restrições, seleção de restrição automática, fornecerá uma lista de todos os [componentes](#go-to-component) de restrição anexados, bem como os botões e um [botão adicionar restrição](#add-constraint-to-game-object).

#### <a name="add-constraint-to-game-object"></a>Adicionar restrição ao objeto de jogo

Esse botão permite que um componente de restrição seja adicionado diretamente do inspetor do gerenciador de restrições. Todos os tipos de restrição em um projeto devem estar visíveis aqui. Confira [restrições de transformação](#transform-constraints) para obter mais informações.

#### <a name="go-to-component"></a>Ir para o componente

Todas as restrições encontradas no objeto serão listadas aqui com um *botão Ir para o componente.* Esse botão fará com que o inspetor role até o componente de restrição selecionado para que ele possa ser configurado.

### <a name="manual-constraint-selection"></a>Seleção manual de restrição

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

Se o gerenciador de restrições for definido como modo manual, somente as restrições vinculadas na lista de restrições serão processadas e aplicadas à transformação. A lista exibida mostrará apenas as restrições [](#go-to-component) selecionadas pelo usuário, bem como os botões ou opções para remover ou adicionar entradas.
Ao habilizar o modo manual pela primeira vez, o gerenciador de restrições preencherá a lista todos os componentes disponíveis como um ponto de partida para selecionar componentes de restrição anexados.

### <a name="remove-entry"></a>Remover entrada

Isso remove a entrada da lista selecionada manualmente. Observe que essa opção não removerá o componente de restrição do objeto do jogo. Os componentes de restrição sempre precisam ser removidos manualmente para garantir que nenhum outro componente que se refere a esse componente seja acidentalmente quebrado.

### <a name="add-entry"></a>Adicionar entrada

Adicionar entrada abrirá um menu suspenso mostrando todos os componentes de restrição disponíveis que ainda não estão na lista manual. Clicando em qualquer uma das entradas que o componente será adicionado à seleção de restrição manual.

### <a name="add-new-constraint"></a>Adicionar nova restrição

Essa opção adicionará um componente do tipo selecionado ao objeto de jogo e adicionará o componente de restrição recém-criado à lista de restrições manual.

## <a name="transform-constraints"></a>Transformar restrições

Restrições podem ser usadas para limitar a manipulação de alguma forma. Por exemplo, alguns aplicativos podem exigir rotação, mas também exigem que o objeto permaneça retíntegro. Nesse caso, um pode ser adicionado ao objeto e usado para limitar a rotação ao `RotationAxisConstraint` eixo y. O MRTK fornece várias restrições, todas elas descritas abaixo.

Também é possível definir novas restrições e usá-las para criar um comportamento de manipulação exclusivo que pode ser necessário para alguns aplicativos. Para fazer isso, crie um script que herda de e implemente a [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) propriedade `ConstraintType` abstrata e o método `ApplyConstraint` abstrato. Ao adicionar uma nova restrição ao objeto, ela deve restringir a manipulação da maneira que foi definida. Essa nova restrição também deve aparecer na seleção [automática](#auto-constraint-selection) do gerenciador de restrições ou [adicionar o](#add-entry) menu suspenso de entrada no modo manual.

Todas as restrições fornecidas pelo MRTK compartilham as seguintes propriedades:

#### <a name="hand-type"></a>Tipo de mão

Especifica se a restrição é usada para uma mão, duas mãos ou ambos os tipos de manipulação. Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.

- *Uma mão:* a restrição será usada durante a manipulação de uma mão, se selecionada.
- *Duas mãos:* a restrição será usada durante a manipulação de duas mãos, se selecionada.

#### <a name="proximity-type"></a>Tipo de proximidade

Especifica se a restrição é usada para manipulação próxima, distante ou de ambos os tipos. Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.

- *Próximo:* a restrição será usada durante a manipulação próxima, se selecionada.
- *Distante:* a restrição será usada durante a manipulação distante, se selecionada.

### <a name="faceuserconstraint"></a>FaceUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

Quando essa restrição é anexada a um objeto , a rotação será limitada para que o objeto sempre seja face ao usuário. Isso é útil para slates ou painéis. As propriedades para `FaceUserConstraint` são as a seguir:

#### <a name="face-away"></a>Face away

O objeto faces para fora do usuário, se for true.

### <a name="fixeddistanceconstraint"></a>FixedDistanceConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

Essa restrição corrige a distância entre o objeto manipulado e outra transformação de objeto no início da manipulação. Isso é útil para comportamentos como corrigir a distância do objeto manipulado para a transformação de cabeça. As propriedades para `FixedDistanceConstraint` são as a seguir:

#### <a name="constraint-transform"></a>Transformação de restrição

Essa é a outra transformação à que o objeto manipulado terá uma distância fixa. O padrão é a transformação da câmera.

### <a name="fixedrotationtouserconstraint"></a>FixedRotationToUserConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

Essa restrição corrige a rotação relativa entre o usuário e o objeto manipulado enquanto ele está sendo manipulado. Isso é útil para slates ou painéis, pois garante que o objeto manipulado sempre mostre a mesma face para o usuário como fez no início da manipulação. O `FixedRotationToUserConstraint` não tem nenhuma propriedade exclusiva.

### <a name="fixedrotationtoworldconstraint"></a>FixedRotationToWorldConstraint

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

Essa restrição corrige a rotação global do objeto manipulado enquanto ele está sendo manipulado. Isso pode ser útil em casos em que nenhuma rotação deve ser imada pela manipulação. O `FixedRotationToWorldConstraint` não tem nenhuma propriedade exclusiva:

### <a name="maintainapparentsizeconstraint"></a>MaintainApparentSizeConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

Quando essa restrição é anexada a um objeto, não importa a distância do objeto do usuário, ela manterá o mesmo tamanho aparente para o usuário (ou seja, ele assumirá a mesma proporção do campo de exibição do usuário). Isso pode ser usado para garantir que um painel de texto ou slate permaneça acessível durante a manipulação. O `MaintainApparentSizeConstraint` não tem nenhuma propriedade exclusiva:

### <a name="moveaxisconstraint"></a>MoveAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

Essa restrição pode ser usada para corrigir em quais eixos um objeto manipulado pode ser movido. Isso pode ser útil para manipular objetos sobre a superfície de um plano ou ao longo de uma linha. As propriedades para `MoveAxisConstraint` são as a seguir:

#### <a name="constraint-on-movement"></a>Restrição na movimentação

Especifica em quais eixos impedir a movimentação. Por padrão, esses eixos serão globais em vez de locais, mas isso pode ser alterado abaixo. Como essa propriedade é um sinalizador, qualquer número de opções pode ser selecionado.

- *Eixo X:* a movimentação ao longo do eixo x é restrita se selecionada.
- *Eixo Y:* a movimentação ao longo do eixo y será restrita se selecionada.
- *Eixo Z:* a movimentação ao longo do eixo z será restrita se selecionada.

#### <a name="use-local-space-for-constraint"></a>Usar espaço local para restrição

Restringirá os eixos de transformação local do objeto manipulado se for true. Falso por padrão.

### <a name="rotationaxisconstraint"></a>RotationAxisConstraint

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

Essa restrição pode ser usada para corrigir sobre quais eixos um objeto manipulado pode ser girado. Isso pode ser útil para manter um objeto manipulado parado, mas ainda permitir rotações de eixo y, por exemplo. As propriedades para `RotationAxisConstraint` são as a seguir:

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
