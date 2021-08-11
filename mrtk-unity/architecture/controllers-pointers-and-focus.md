---
title: Controladores, ponteiros e foco
description: Interagindo com controladores, ponteiros e foco.
author: cDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Ponteiros, Controladores
ms.openlocfilehash: 00bc0641182c566b045f959dfa361e1311b3cd224fc998f154010ad2996679ae
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115196286"
---
# <a name="controllers-pointers-and-focus"></a>Controladores, ponteiros e foco

Controladores, ponteiros e foco são conceitos de nível superior que se baseam na base estabelecida pelo sistema de entrada principal. Juntos, eles fornecem uma grande parte do mecanismo para interagir com objetos na cena.

## <a name="controllers"></a>Controladores

Controladores são representações de um controlador físico (6 graus de liberdade, mão articulada etc.). Eles são criados por gerenciadores de dispositivos e são responsáveis por se comunicar com o sistema subjacente correspondente e traduzir esses dados em eventos e dados em forma de MRTK.a

Por exemplo, na plataforma Windows Mixed Reality, o é um controlador responsável por fazer a interfação com as APIs de acompanhamento de mão Windows subjacentes para obter informações sobre as junções, a pose e outras propriedades da [`WindowsMixedRealityArticulatedHand`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityArticulatedHand) mão. [](/uwp/api/windows.ui.input.spatial.spatialinteractionsourcestate) Ele é responsável por transformar esses dados em eventos relevantes do MRTK (por exemplo, chamando RaisePoseInputChanged ou RaiseHandJointsUpdated) e atualizando seu próprio estado interno para que as consultas para retornem dados [`TryGetJointPose`](xref:Microsoft.MixedReality.Toolkit.Input.HandJointUtils.TryGetJointPose%2A) corretos.

Em geral, o ciclo de vida de um controlador envolverá:

1. Um controlador é criado por um gerenciador de dispositivos após a detecção de uma nova fonte (por exemplo, o gerenciador de dispositivos detecta e começa a rastrear uma mão).

2. No loop Update() do controlador, ele chama em seu sistema de API subjacente.

3. No mesmo loop de atualização, ele gera alterações de evento de entrada chamando diretamente no próprio sistema de entrada principal (por exemplo, inging HandMeshUpdated ou HandJointsUpdated).

## <a name="pointers-and-focus"></a>Ponteiros e foco

Ponteiros são usados para interagir com objetos de jogo. Esta seção descreve como os ponteiros são criados, como eles são atualizados e como eles determinam os objetos que estão em foco. Ele também abrange os diferentes tipos de ponteiros existentes e os cenários em que eles estão ativos.

### <a name="pointer-categories"></a>Categorias de ponteiro

Os ponteiros geralmente se enquadram em uma das seguintes categorias:

- **Ponteiros distantes**

  Esses tipos de ponteiros são usados para interagir com objetos que estão longe do usuário (distante é definido como simplesmente "não próximo"). Esses tipos de ponteiros geralmente lançam linhas que podem ir muito longe no mundo e permitir que o usuário interaja e manipule objetos que não estão imediatamente ao lado deles.

- **Ponteiros próximos**

  Esses tipos de ponteiros são usados para interagir com objetos próximos o suficiente do usuário para pegar, tocar e manipular. Em geral, esses tipos de ponteiros interagem com objetos procurando objetos nas proximidades (seja fazendo o raycast em distâncias pequenas, fazendo a transmissão esférica procurando objetos nas proximidades ou enumerando listas de objetos que são considerados acessíveis/tocáveis).

- **Ponteiros de teletransporte**

  Esses tipos de ponteiros se conectam ao sistema de transporte para lidar com a movimentação do usuário para o local de destino do ponteiro.

## <a name="pointer-mediation"></a>Ponteiro de ponteiro

Como um único controlador pode ter vários ponteiros (por exemplo, a mão articulada pode ter ponteiros de interação próximos e distantes), existe um componente que é responsável por mediar qual ponteiro deve estar ativo.

Por exemplo, conforme a mão do usuário se aproxima de um botão pressionável, o deve parar de aparecer [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) e o deve ser [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) envolvido.

Isso é tratado pelo , que é responsável por determinar quais ponteiros estão ativos, com [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) base no estado de todos os ponteiros. Uma das principais coisas que isso faz é desabilitar ponteiros distantes quando um ponteiro próximo estiver próximo a um objeto (consulte [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) ).

É possível fornecer uma implementação alternativa do mediador de ponteiro alterando a [`PointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile.PointerMediator) propriedade no perfil do ponteiro.

### <a name="how-to-disable-pointers"></a>Como desabilitar ponteiros

Como o mediador de ponteiro executa cada quadro, ele acaba controlando o estado ativo/inativo de todos os ponteiros. Portanto, se você definir a propriedade IsInteractionEnabled de um ponteiro no código, ela será substituída pelo mediador de ponteiro a cada quadro. Em vez disso, você pode especificar [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) o para controlar se os ponteiros devem estar ativas ou desligados por conta própria. Observe que isso só funcionará se você estiver usando o padrão [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) e [`DefaultPointerMediator`](xref:Microsoft.MixedReality.Toolkit.Input.DefaultPointerMediator) no MRTK.

#### <a name="example-disable-hand-rays-in-mrtk"></a>Exemplo: Desabilitar raios de mão no MRTK

O código a seguir desligará os raios de mão no MRTK:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Turn off hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);
```

O código a seguir retornará raios de mão para seu comportamento padrão no MRTK:

```c#
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.Default);
```

O código a seguir forçará a adoção de raios de mão, independentemente de estar próximo a um grabbable:

```c#
// Turn off all hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOn);
```

Consulte [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) e para obter mais [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) exemplos.

### <a name="focusprovider"></a>FocusProvider

O é o trabalhador responsável por iterar na lista de todos os ponteiros e descobrir qual é o objeto focalizado [`FocusProvider`](xref:Microsoft.MixedReality.Toolkit.Input.FocusProvider) para cada ponteiro.

Em cada `Update()` chamada, isso vai:

1. Atualize todos os ponteiros, raycasting e fazendo a detecção de acertos conforme configurado pelo próprio ponteiro (por exemplo, o ponteiro de esfera pode especificar SphereOverlap raycastMode, portanto, FocusProvider fará uma colisão baseada em esfera)

2. Atualize o objeto focalizado por ponteiro (ou seja, se um objeto ganhasse foco, ele também dispararia eventos para esse objeto, se um objeto tivesse perdido o foco, ele dispararia a perda de foco etc.).

### <a name="pointer-configuration-and-lifecycle"></a>Configuração e ciclo de vida do ponteiro

[Os ponteiros podem ser configurados](../features/input/pointers.md) na seção *Ponteiros* do perfil do sistema de entrada.

O tempo de vida de um ponteiro geralmente é o seguinte:

1. Um gerenciador de dispositivos detectará a presença de um controlador. Esse gerenciador de dispositivos criará o conjunto de ponteiros associados ao controlador por meio de uma chamada para [`RequestPointers`](xref:Microsoft.MixedReality.Toolkit.Input.BaseInputDeviceManager) .

2. O FocusProvider, em seu loop Update(), iterará em todos os ponteiros válidos e fará a lógica de detecção de raycast ou de hit associada. Isso é usado para determinar o objeto focalizado por cada ponteiro específico.

    - Como é possível ter várias fontes de entrada ativas ao mesmo tempo (por exemplo, duas mãos ativas presentes), também é possível ter vários objetos que têm foco ao mesmo tempo.

3. O gerenciador de dispositivos, ao descobrir que uma origem do controlador foi perdida, destruirá os ponteiros associados ao controlador perdido.