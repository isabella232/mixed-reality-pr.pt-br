---
title: Menu lateral
description: Cenário de exemplo de menu à mão em MRTK
author: cre8ivepark
ms.author: dongpark
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, HandMenu,
ms.openlocfilehash: 9bb0276c048912b4f463dd93d3303c9a3af8fe29
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177521"
---
# <a name="hand-menu"></a>Menu lateral

![Exemplo de UX do menu do manual](../images/solver/MRTK_UX_HandMenu.png)

Os menus à mão permitem que os usuários tragam rapidamente a interface do usuário conectada à mão para funções usadas com frequência. Para evitar a ativação falsa ao interagir com outros objetos, o menu à mão fornece opções como ' exigir Flatly ' e ' Use olhar Activation '. É recomendável usar essas opções para impedir a ativação indesejada.

## <a name="hand-menu-examples"></a>Exemplos de menu do lado

A cena **HandMenuExamples. Unity** está sob a ``MRTK/Examples/Demos/HandTracking/Scenes`` pasta. Quando estiver em execução, a cena só ativará o tipo de menu selecionado no momento.
<br/><img src="../images/hand-menu/MRTK_HandMenu_ExampleScene.png" width="600px" alt="HandMenu_ExampleScene">

Você pode encontrar esses menus pré-fabricados na ``MRTK/Examples/Demos/HandTracking/Prefabs`` pasta.

### <a name="handmenu_small_hideonhanddrop-and-handmenu_medium_hideonhanddrop"></a>HandMenu_Small_HideOnHandDrop e HandMenu_Medium_HideOnHandDrop

Esses dois exemplos simplesmente ativam e desativam o objeto MenuContent para mostrar e ocultar o menu no evento **OnFirstHandDetected ()** e **OnLastHandLost ()** .
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example1.png" width="600" alt="HandMenu_ExampleScene 1">
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example2.png" width="600" alt="HandMenu_ExampleScene 2">

### <a name="handmenu_large_worldlock_on_grabandpull"></a>HandMenu_Large_WorldLock_On_GrabAndPull

Para menus mais complexos que exigem tempo de interação maior, é recomendável bloquear o mundo do menu. Neste exemplo, o usuário pode pegar e efetuar pull para o mundo bloquear o menu, além de ativar e desativar o MenuContent em eventos **OnFirstHandDetected ()** e **OnLastHandLost ()** .
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example3.png" width="600" alt="HandMenu_ExampleScene 3">

A placa traseira `ManipulationHandler` torna-a que é possível capturar e móvel. **Em evento de manipulação iniciada** , **SolverHandler. UpdateSolvers** é desativado para o mundo-bloqueia o menu. Além disso, ele mostra o **botão fechar** para permitir que o usuário feche o menu quando a tarefa for concluída. **No evento Manipulation finalizado** , ele chama **HandConstraintPalmUp. StartWorldLockReattachCheckCoroutine** para permitir que o usuário traga o menu de volta para a mão, levantando e observando o Palm.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example4.png" width="600" alt="HandMenu_ExampleScene 4">

O botão **fechar** reativa **SolverHandler. UpdateSolvers** e oculta o **MenuContent**.
<br/><img src="../images/hand-menu/MRTK_HandMenu_Example5.png" alt="HandMenu_ExampleScene 5">

### <a name="handmenu_large_autoworldlock_on_handdrop"></a>HandMenu_Large_AutoWorldLock_On_HandDrop

Este exemplo é semelhante a HandMenu_Large_WorldLock_On_GrabAndPull. A única diferença é que o menu será automaticamente bloqueado no lado do mundo. Isso é feito simplesmente não ocultando o evento MenuContent no **OnLastHandLost ()** . O comportamento de pull de & de captura é o mesmo que HandMenu_Large_WorldLock_On_GrabAndPull exemplo.

## <a name="scripts"></a>Scripts

O [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) comportamento fornece um solucionador que restringe o objeto rastreado a uma região segura para conteúdo restrito por mão (como interface do usuário, menus, etc.). regiões de Cofre são consideradas áreas que não fazem interseção com a mão. Uma classe derivada de [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) chamada [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) também é incluída para demonstrar um comportamento comum de ativar o objeto rastreador acompanhado quando a Palm está voltada para o usuário.

Consulte as dicas de ferramenta disponíveis para cada [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) propriedade para obter mais documentação. Algumas propriedades são definidas mais detalhadamente abaixo.

<img src="../images/solver/MRTK_Solver_HandConstraintPalmUp.png" width="450" alt="HandMenu_ExampleScene Palm up">

* **zona de Cofre**: a zona segura especifica em que ponto a mão deve restringir o conteúdo. É recomendável que o conteúdo seja colocado no lado do ulnar para evitar sobreposição com a mão e qualidade de interação aprimorada. as zonas de Cofre são calculadas por meio da orientação de mãos projetadas em um plano ortogonal à exibição da câmera e raycasting em uma caixa delimitadora ao lado das mãos. Cofre zonas são definidas para funcionar com o [`IMixedRealityHand`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityHand) , mas também funcionam com outros tipos de controlador. É recomendável explorar o que cada zona segura representa em diferentes tipos de controlador.

* **Seguir mão até a câmera oposta** Com este ativo, o Solver seguirá a rotação, até que o menu esteja suficientemente alinhado com o olhar, no ponto em que ele se faces da câmera. Isso funciona alterando o SolverRotationBehavior no HandConstraintSolver, de LookAtTrackedObject para LookAtMainCamera, pois o ângulo de GazeAlignment com o resolvedor varia.

<img src="../images/solver/MRTK_Solver_HandConstraintSafeZones.png" width="450" alt="HandMenu Safe Zones">

* **Eventos de ativação**: atualmente, o [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) dispara quatro eventos de ativação. Esses eventos podem ser usados em muitas combinações diferentes para criar [`HandConstraint`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraint) comportamentos exclusivos, consulte a cena HandBasedMenuExample em `MRTK/Examples/Demos/HandTracking/Scenes/` para obter exemplos desses comportamentos.

  * *OnHandActivate*: dispara quando uma mão satisfaz o método IsHandActive.
  * *OnHandDeactivate*: dispara quando o método IsHandActive não é mais satisfeito.
  * *OnFirstHandDetected*: ocorre quando o estado de acompanhamento da mão é alterado de sem hands no modo de exibição, para a primeira mão na exibição.
  * *OnLastHandLost*: ocorre quando o estado de acompanhamento da mão é alterado de pelo menos uma mão na exibição, para nenhuma exibição prática.

* **Lógica de desativação/ativação do Solver**: atualmente, a recomendação para ativar e desativar a [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) lógica é fazer isso por meio do uso do valor UpdateSolver do SolverHandler, em vez de desabilitar/habilitar o objeto. Isso pode ser visto na cena de exemplo por meio de ganchos baseados em editor disparados após os eventos de ManipulationHandler "OnManipulationStarted/encerrado" do menu anexado.

  * *Parando a lógica de restrição à mão*: ao tentar definir o objeto restrito à mão para parar (bem como não executar a lógica de ativação/desativação), defina UpdateSolver como false em vez de desabilitar HandConstraintPalmUp.
    * Se você quiser habilitar a lógica de reanexação baseada em olhar (ou até mesmo em não-olhar), isso será seguido chamando a função HandConstraintPalmUp. StartWorldLockReattachCheckCoroutine (). Isso disparará uma corrotina que continuará verificando se os critérios de "IsValidController" são atendidos e definirá UpdateSolver como true quando for (ou o objeto estiver desabilitado)
  * *Iniciando a lógica de restrição à mão*: ao tentar definir o objeto restrito à mão para começar a seguir novamente (com base em se ele atende aos critérios de ativação), defina UpdateSolver de SolverHandler como true.

* **Reanexar lógica**: no momento [`HandConstraintPalmUp`](xref:Microsoft.MixedReality.Toolkit.Utilities.Solvers.HandConstraintPalmUp) , é capaz de reanexar automaticamente o objeto de destino ao ponto rastreado, independentemente de o UpdateSolver do SolverHandler ser verdadeiro ou não. Isso é feito por meio da chamada da função StartWorldLockReattachCheckCoroutine () da HandConstraintPalmUp, depois que ela é bloqueada pelo mundo (que, nesse caso, está efetivamente definindo a UpdateSolver de SolverHandler como false).

## <a name="see-also"></a>Confira também

* [Botão](button.md)
* [Menu próximo](near-menu.md)
