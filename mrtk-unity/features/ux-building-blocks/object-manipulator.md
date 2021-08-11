---
title: Manipulador de objetos
description: Como usar o objeto manipulador no MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, manipulação de objetos,
ms.openlocfilehash: 4c43a35e164d3e66e662afc927d28f84463e1586250e9847a2d88c219ba27f23
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115191592"
---
# <a name="object-manipulator"></a>Manipulador de objetos

![Manipulador de objetos](../images/manipulation-handler/MRTK_Manipulation_Main.png)

O *Objectmanipuletor* é o novo componente para o comportamento de manipulação, encontrado anteriormente em *ManipulationHandler*. O objeto manipulador faz uma série de aprimoramentos e simplificações. Esse componente é uma substituição para o manipulador de manipulação, que será preterido.

O script *Objectmanipuletor* torna um objeto móvel, escalonável e rotatable usando uma ou duas mãos. O objeto manipulador pode ser configurado para controlar como o objeto responderá a várias entradas. o script deve funcionar com a maioria das formas de interação, como HoloLens duas mãos, HoloLens raios de duas mãos, HoloLens 1 olhar e gestos e entrada do controlador de movimento do headset de imersão.

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a>Como usar o objeto manipulador

Para usar o objeto manipulador, primeiro adicione o `ObjectManipulator` componente script a um gameobject. Certifique-se também de adicionar um colisor ao objeto, correspondendo seus limites de captura.

Para fazer com que o objeto responda à entrada de mão articulada Near, adicione o `NearInteractionGrabbable` script também.

O comportamento da física pode ser habilitado para o objeto manipulador adicionando um componente rigidbody ao objeto. O comportamento de física habilitado adicionando esse componente é discutido com mais detalhes em [*física e colisões*](#physics-and-collisions).

Assim, a manipulação pode ser restrita com a adição de componentes de [restrição de manipulação](constraint-manager.md#transform-constraints) ao objeto. Esses são componentes especiais que funcionam com a manipulação e alteram o comportamento de manipulação de alguma forma.

![Usando o manipulador de manipulação no editor do Unity](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a>Propriedades e campos do Inspetor

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a>Propriedades gerais

#### <a name="host-transform"></a>Transformação de host

A transformação do objeto que será manipulada. O padrão é o objeto do componente.

#### <a name="manipulation-type"></a>Tipo de manipulação

Especifica se o objeto pode ser manipulado usando uma ou duas mãos. Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.

- *Uma mão*: habilita a manipulação de uma mão, se selecionada.
- *Duas mãos*: habilita a manipulação de duas mãos, se selecionada.

#### <a name="allow-far-manipulation"></a>Permitir manipulação distante

Especifica se a manipulação pode ser feita usando a interação de longe com ponteiros.

### <a name="one-handed-manipulation-properties"></a>Propriedades de manipulação de uma mão

#### <a name="one-hand-rotation-mode-near"></a>Modo de rotação de um lado próximo

Especifica como o objeto se comportará quando estiver sendo capturado com uma mão perto de. Essas opções funcionam apenas para as mãos articuladas.

- *Girar sobre o centro de objetos*: o objeto gira usando a rotação da mão, mas sobre o ponto central de objetos. O objeto parecerá ficar menos à medida que gira, mas pode haver uma sensação de desconexão entre a mão e o objeto. Mais útil para interações distantes.
- *Girar sobre o ponto de captura*: gire o objeto com a mão sobre o ponto de captura entre o polegar e o dedo do índice. Deve parecer que o objeto está sendo mantido por mão.

#### <a name="one-hand-rotation-mode-far"></a>Modo de rotação unidirecional distante

Especifica como o objeto se comportará quando estiver sendo capturado com uma mão à distância. Essas opções funcionam apenas para as mãos articuladas.

- *Girar sobre a central de objetos*: girar o objeto usando a rotação da mão, mas sobre o ponto central de objetos. Útil para inspecionar em uma distância sem que o centro de objetos se mova enquanto o objeto gira.
- *Girar sobre o ponto de captura*: girar o objeto usando a rotação da mão, mas sobre o ponto de acesso do ponteiro Ray. Útil para inspeção.

### <a name="two-handed-manipulation-properties"></a>Duas propriedades de manipulação de mão

#### <a name="two-handed-manipulation-type"></a>Tipo de manipulação de duas mãos

Especifica como a manipulação de duas mãos pode transformar um objeto. Como essa propriedade é um sinalizador, qualquer número de opções pode ser selecionado.

- *Mover*: a movimentação é permitida se selecionada.
- *Escala*: o dimensionamento é permitido se selecionado.
- *Girar*: a rotação é permitida se selecionada.

![Manipulador de manipulação](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a>Restrições

#### <a name="enable-constraints"></a>Habilitar restrições

Essa configuração habilitará o [Gerenciador de restrição](constraint-manager.md)vinculado. As alterações de transformação serão processadas por restrições registradas para o [Gerenciador de restrição](constraint-manager.md)selecionado.

#### <a name="constraint-manager"></a>Gerenciador de restrição

A lista suspensa permite selecionar qualquer um dos [gerenciadores de restrição](constraint-manager.md)anexados. O objeto manipulador garante que há um [Gerenciador de restrição](constraint-manager.md) anexado em todos os momentos.
Observe que vários componentes do mesmo tipo serão exibidos com o mesmo nome no Unity. Para facilitar a distinção entre vários gerenciadores de restrição no mesmo objeto, as opções disponíveis mostrarão uma dica na configuração do Gerenciador de restrição selecionado (seleção de restrição manual ou automática).

#### <a name="go-to-component"></a>Ir para o componente

A seleção do Gerenciador de restrição vem com um botão *ir para componente* . Esse botão fará com que o Inspetor role para o componente selecionado para que ele possa ser configurado.

### <a name="physics"></a>Física

Configurações nesta seção aparecerão somente quando o objeto tiver um componente RigidBody.

#### <a name="release-behavior"></a>Comportamento da versão

Especifique quais propriedades físicas um objeto manipulado deve manter após a liberação. Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.

- *Manter a velocidade*: quando o objeto for liberado, se essa opção for selecionada, ela manterá sua velocidade linear.
- *manter Angular velocidade*: quando o objeto for liberado, se essa opção for selecionada, ela manterá sua velocidade Angular.

#### <a name="use-forces-for-near-manipulation"></a>Usar forças para manipulação próxima

Se as forças de física são usadas para mover o objeto ao executar quase as manipulações. Definir isso como *false* fará com que o objeto se sinta mais diretamente conectado à mão dos usuários. Definir como *true* vai respeitar a massa e a inércia do objeto, mas pode parecer que o objeto está conectado por uma mola. O padrão é *false*.

### <a name="smoothing"></a>Suavização

#### <a name="smoothing-far"></a>Suavizando a distância

Se a suavização independente de taxa de quadros está habilitada para interações distantes. A suavização está habilitada por padrão.

#### <a name="smoothing-near"></a>Suavizando ao lado

Se a suavização independente de taxa de quadros está habilitada para interações próximas. A suavização próxima é desabilitada por padrão porque o efeito pode ser percebido como "desconectado" da mão.

#### <a name="smoothing-active"></a>Suavizando ativos

Obsoleto e será removido em uma versão futura. Os aplicativos devem usar SmoothingFar, SmoothingNear ou uma combinação dos dois.

#### <a name="move-lerp-time"></a>Mover tempo Lerp

Quantidade de suavização a ser aplicada ao movimento. A suavização de 0 significa sem suavização. Valor máximo significa nenhuma alteração no valor.

#### <a name="rotate-lerp-time"></a>Girar Lerp tempo

Quantidade de suavização a ser aplicada à rotação. A suavização de 0 significa sem suavização. Valor máximo significa nenhuma alteração no valor.

#### <a name="scale-lerp-time"></a>Tempo de Lerp de escala

Quantidade de suavização a ser aplicada à escala. Suavização de 0 significa nenhuma suavização. Valor máximo significa nenhuma alteração no valor.

### <a name="manipulation-events"></a>Eventos de manipulação

O manipulador de manipulação fornece os seguintes eventos:

- *OnManipulationStarted:* acionado quando a manipulação é iniciada.
- *OnManipulationEnded:* é a incêndio quando a manipulação termina.
- *OnHoverStarted:* é a incêndio quando uma mão/controlador passar o mouse no manipulador, próximo ou distante.
- *OnHoverEnded:* é a incêndio quando uma mão/controlador destoca o manipulador, próximo ou distante.

A ordem de a incêndio do evento para manipulação é:

*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*

Se não houver manipulação, você ainda obterá eventos de foco com a seguinte ordem de incêndio:

*OnHoverStarted*  ->  *OnHoverEnded*

## <a name="physics-and-collisions"></a>Física e colisões

O comportamento da física pode ser habilitado adicionando um componente rigidbody ao mesmo objeto que um manipulador de objetos. Isso não apenas habilita a configuração [do comportamento de versão](#release-behavior) acima, mas também permite colisões. Sem um componente rigidbody, as colisões não se comportam corretamente durante a manipulação:

- Colisões entre um objeto manipulado e um colisor estático (ou seja, um objeto com um colisor, mas nenhum corpo rígido) não funcionam, o objeto manipulado passa diretamente pelo colisor estático não afetado.
- Colisões entre um objeto manipulado e um rigidbody (ou seja, um objeto com um colisor e um rigidbody) faz com que o rigidbody tenha uma resposta de colisão, mas a resposta é rápida e meso. Também não há resposta de colisão no objeto manipulado.

Quando um rigidbody é adicionado, as colisões devem funcionar corretamente.

### <a name="without-rigidbody"></a>Sem rigidbody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a>Com rigidbody

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a>Elástico (experimental)

Os elásticos podem ser usados ao manipular objetos por meio do manipulador de objetos. Observe que o [sistema elástico ainda](../experimental/elastic-system.md) está em estado experimental. Para habilitar o elástico, vincule um componente existente do Elastics Manager ou crie e vincule um novo gerenciador de elásticos por meio do `Add Elastics Manager` botão.

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a>Confira também

- [Controle de limites](bounds-control.md)
- [Gerenciador de restrição](constraint-manager.md)
- [Janela de migração](../tools/migration-window.md)
- [Sistema elástico (Experimental)](../experimental/elastic-system.md)
