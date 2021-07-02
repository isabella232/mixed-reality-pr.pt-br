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
# <a name="constraint-manager"></a><span data-ttu-id="e1db1-104">Gerenciador de restrições</span><span class="sxs-lookup"><span data-stu-id="e1db1-104">Constraint manager</span></span>

<span data-ttu-id="e1db1-105">O gerenciador de restrições permite aplicar um conjunto de componentes de restrição a uma transformação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-105">The constraint manager allows to apply a set of constraint components to a transform.</span></span> <span data-ttu-id="e1db1-106">Componentes do [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) tipo anexados ao objeto de jogo podem ser considerados.</span><span class="sxs-lookup"><span data-stu-id="e1db1-106">Components of type [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) that are attached to the game object can be taken into consideration.</span></span>
<span data-ttu-id="e1db1-107">Por padrão, o gerenciador de restrições coletará automaticamente todos os componentes [de](#transform-constraints) restrição anexados ao objeto de jogo e os aplicará às transformação processadas.</span><span class="sxs-lookup"><span data-stu-id="e1db1-107">Per default, constraint manager will automatically collect all [constraint components](#transform-constraints) attached to the game object and apply them to processed transforms.</span></span>
<span data-ttu-id="e1db1-108">No entanto, os usuários podem optar por configurar a lista de restrições aplicadas manualmente e permitir que apenas um subconjunto de restrições anexadas seja aplicado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-108">However users can opt for configuring the list of applied constraints manually and allowing only a subset of attached constraints to be applied.</span></span>

<span data-ttu-id="e1db1-109">Atualmente, os seguintes elementos de UX do MRTK estão dando suporte ao gerenciador de restrições:</span><span class="sxs-lookup"><span data-stu-id="e1db1-109">Currently the following MRTK UX elements are supporting constraint manager:</span></span>

- [<span data-ttu-id="e1db1-110">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="e1db1-110">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="e1db1-111">Manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="e1db1-111">Object manipulator</span></span>](object-manipulator.md)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="e1db1-112">Propriedades e campos do inspetor</span><span class="sxs-lookup"><span data-stu-id="e1db1-112">Inspector properties and fields</span></span>

<span data-ttu-id="e1db1-113">O gerenciador de restrições pode ser operado em dois modos:</span><span class="sxs-lookup"><span data-stu-id="e1db1-113">Constraint manager can be operated in two modes:</span></span>

- <span data-ttu-id="e1db1-114">Seleção de restrição automática</span><span class="sxs-lookup"><span data-stu-id="e1db1-114">Auto constraint selection</span></span>
- <span data-ttu-id="e1db1-115">Seleção manual de restrição</span><span class="sxs-lookup"><span data-stu-id="e1db1-115">Manual constraint selection</span></span>

### <a name="auto-constraint-selection"></a><span data-ttu-id="e1db1-116">Seleção de restrição automática</span><span class="sxs-lookup"><span data-stu-id="e1db1-116">Auto constraint selection</span></span>

<img src="../images/constraint-manager/AutoSelection.png" width="600" alt="Auto Selection">

<span data-ttu-id="e1db1-117">O modo padrão do gerenciador de restrições, seleção de restrição automática, fornecerá uma lista de todos os [componentes](#go-to-component) de restrição anexados, bem como os botões e um [botão adicionar restrição](#add-constraint-to-game-object).</span><span class="sxs-lookup"><span data-stu-id="e1db1-117">The default mode of constraint manager, auto constraint selection, will provide a list of all attached constraint components as well as [go to buttons](#go-to-component) and an [add constraint button](#add-constraint-to-game-object).</span></span>

#### <a name="add-constraint-to-game-object"></a><span data-ttu-id="e1db1-118">Adicionar restrição ao objeto de jogo</span><span class="sxs-lookup"><span data-stu-id="e1db1-118">Add constraint to game object</span></span>

<span data-ttu-id="e1db1-119">Esse botão permite que um componente de restrição seja adicionado diretamente do inspetor do gerenciador de restrições.</span><span class="sxs-lookup"><span data-stu-id="e1db1-119">This button allows a constraint component to be added directly from the constraint manager inspector.</span></span> <span data-ttu-id="e1db1-120">Todos os tipos de restrição em um projeto devem estar visíveis aqui.</span><span class="sxs-lookup"><span data-stu-id="e1db1-120">All constraint types in a project should be visible here.</span></span> <span data-ttu-id="e1db1-121">Confira [restrições de transformação](#transform-constraints) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="e1db1-121">See [transform constraints](#transform-constraints) for more info.</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="e1db1-122">Ir para o componente</span><span class="sxs-lookup"><span data-stu-id="e1db1-122">Go to component</span></span>

<span data-ttu-id="e1db1-123">Todas as restrições encontradas no objeto serão listadas aqui com um *botão Ir para o componente.*</span><span class="sxs-lookup"><span data-stu-id="e1db1-123">All constraints found on the object wil be listed here with a *Go to component* button.</span></span> <span data-ttu-id="e1db1-124">Esse botão fará com que o inspetor role até o componente de restrição selecionado para que ele possa ser configurado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-124">This button will cause the inspector to scroll to the selected constraint component so that it can be configured.</span></span>

### <a name="manual-constraint-selection"></a><span data-ttu-id="e1db1-125">Seleção manual de restrição</span><span class="sxs-lookup"><span data-stu-id="e1db1-125">Manual constraint selection</span></span>

<img src="../images/constraint-manager/ManualSelection.png" width="600" alt="Manual Selection">

<span data-ttu-id="e1db1-126">Se o gerenciador de restrições for definido como modo manual, somente as restrições vinculadas na lista de restrições serão processadas e aplicadas à transformação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-126">If constraint manager is set to manual mode, only constraints that are linked in the constraint list are processed and applied to the transform.</span></span> <span data-ttu-id="e1db1-127">A lista exibida mostrará apenas as restrições [](#go-to-component) selecionadas pelo usuário, bem como os botões ou opções para remover ou adicionar entradas.</span><span class="sxs-lookup"><span data-stu-id="e1db1-127">The list displayed will only show the user selected constraints as well as [go to buttons](#go-to-component) or options to remove or add entries.</span></span>
<span data-ttu-id="e1db1-128">Ao habilizar o modo manual pela primeira vez, o gerenciador de restrições preencherá a lista todos os componentes disponíveis como um ponto de partida para selecionar componentes de restrição anexados.</span><span class="sxs-lookup"><span data-stu-id="e1db1-128">When enabling manual mode for the first time, constraint manager will populate the list will all available components as a starting point for selecting attached constraint components.</span></span>

### <a name="remove-entry"></a><span data-ttu-id="e1db1-129">Remover entrada</span><span class="sxs-lookup"><span data-stu-id="e1db1-129">Remove entry</span></span>

<span data-ttu-id="e1db1-130">Isso remove a entrada da lista selecionada manualmente.</span><span class="sxs-lookup"><span data-stu-id="e1db1-130">This removes the entry from the manually selected list.</span></span> <span data-ttu-id="e1db1-131">Observe que essa opção não removerá o componente de restrição do objeto do jogo.</span><span class="sxs-lookup"><span data-stu-id="e1db1-131">Note that this option will not remove the constraint component from the game object.</span></span> <span data-ttu-id="e1db1-132">Os componentes de restrição sempre precisam ser removidos manualmente para garantir que nenhum outro componente que se refere a esse componente seja acidentalmente quebrado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-132">Constraint components always need to be removed manually to ensure not accidentally breaking any other component referring to this component.</span></span>

### <a name="add-entry"></a><span data-ttu-id="e1db1-133">Adicionar entrada</span><span class="sxs-lookup"><span data-stu-id="e1db1-133">Add entry</span></span>

<span data-ttu-id="e1db1-134">Adicionar entrada abrirá um menu suspenso mostrando todos os componentes de restrição disponíveis que ainda não estão na lista manual.</span><span class="sxs-lookup"><span data-stu-id="e1db1-134">Add entry will open a dropdown showing all available constraint components that are not in the manual list yet.</span></span> <span data-ttu-id="e1db1-135">Clicando em qualquer uma das entradas que o componente será adicionado à seleção de restrição manual.</span><span class="sxs-lookup"><span data-stu-id="e1db1-135">By clicking on any of the entries that component will be added to the manual constraint selection.</span></span>

### <a name="add-new-constraint"></a><span data-ttu-id="e1db1-136">Adicionar nova restrição</span><span class="sxs-lookup"><span data-stu-id="e1db1-136">Add new constraint</span></span>

<span data-ttu-id="e1db1-137">Essa opção adicionará um componente do tipo selecionado ao objeto de jogo e adicionará o componente de restrição recém-criado à lista de restrições manual.</span><span class="sxs-lookup"><span data-stu-id="e1db1-137">This option will add a component of the selected type to the game object and add the newly created constraint component to the manual constraint list.</span></span>

## <a name="transform-constraints"></a><span data-ttu-id="e1db1-138">Transformar restrições</span><span class="sxs-lookup"><span data-stu-id="e1db1-138">Transform constraints</span></span>

<span data-ttu-id="e1db1-139">Restrições podem ser usadas para limitar a manipulação de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="e1db1-139">Constraints can be used to limit manipulation in some way.</span></span> <span data-ttu-id="e1db1-140">Por exemplo, alguns aplicativos podem exigir rotação, mas também exigem que o objeto permaneça retíntegro.</span><span class="sxs-lookup"><span data-stu-id="e1db1-140">For example, some applications may require rotation, but also require that the object remain upright.</span></span> <span data-ttu-id="e1db1-141">Nesse caso, um pode ser adicionado ao objeto e usado para limitar a rotação ao `RotationAxisConstraint` eixo y.</span><span class="sxs-lookup"><span data-stu-id="e1db1-141">In this case, a `RotationAxisConstraint` can be added to the object and used to limit rotation to y-axis rotation.</span></span> <span data-ttu-id="e1db1-142">O MRTK fornece várias restrições, todas elas descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="e1db1-142">MRTK provides a number of constraints, all of which are described below.</span></span>

<span data-ttu-id="e1db1-143">Também é possível definir novas restrições e usá-las para criar um comportamento de manipulação exclusivo que pode ser necessário para alguns aplicativos.</span><span class="sxs-lookup"><span data-stu-id="e1db1-143">It is also possible to define new constraints and use them to create unique manipulation behaviour that may be needed for some applications.</span></span> <span data-ttu-id="e1db1-144">Para fazer isso, crie um script que herda de e implemente a [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) propriedade `ConstraintType` abstrata e o método `ApplyConstraint` abstrato.</span><span class="sxs-lookup"><span data-stu-id="e1db1-144">To do this, create a script that inherits from [`TransformConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.TransformConstraint) and implement the abstract `ConstraintType` property and the abstract `ApplyConstraint` method.</span></span> <span data-ttu-id="e1db1-145">Ao adicionar uma nova restrição ao objeto, ela deve restringir a manipulação da maneira que foi definida.</span><span class="sxs-lookup"><span data-stu-id="e1db1-145">Upon adding a new constraint to the object, it should constrain manipulation in the way that was defined.</span></span> <span data-ttu-id="e1db1-146">Essa nova restrição também deve aparecer na seleção [automática](#auto-constraint-selection) do gerenciador de restrições ou [adicionar o](#add-entry) menu suspenso de entrada no modo manual.</span><span class="sxs-lookup"><span data-stu-id="e1db1-146">This new constraint should also show in the constraint manager [auto selection](#auto-constraint-selection) or [add entry](#add-entry) dropdown in manual mode.</span></span>

<span data-ttu-id="e1db1-147">Todas as restrições fornecidas pelo MRTK compartilham as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="e1db1-147">All of the constraints provided by MRTK share the following properties:</span></span>

#### <a name="hand-type"></a><span data-ttu-id="e1db1-148">Tipo de mão</span><span class="sxs-lookup"><span data-stu-id="e1db1-148">Hand Type</span></span>

<span data-ttu-id="e1db1-149">Especifica se a restrição é usada para uma mão, duas mãos ou ambos os tipos de manipulação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-149">Specifies whether the constraint is used for one handed, two handed or both kinds of manipulation.</span></span> <span data-ttu-id="e1db1-150">Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.</span><span class="sxs-lookup"><span data-stu-id="e1db1-150">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="e1db1-151">*Uma mão:* a restrição será usada durante a manipulação de uma mão, se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-151">*One handed*: Constraint will be used during one handed manipulation if selected.</span></span>
- <span data-ttu-id="e1db1-152">*Duas mãos:* a restrição será usada durante a manipulação de duas mãos, se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-152">*Two handed*: Constraint will be used during two handed manipulation if selected.</span></span>

#### <a name="proximity-type"></a><span data-ttu-id="e1db1-153">Tipo de proximidade</span><span class="sxs-lookup"><span data-stu-id="e1db1-153">Proximity Type</span></span>

<span data-ttu-id="e1db1-154">Especifica se a restrição é usada para manipulação próxima, distante ou de ambos os tipos.</span><span class="sxs-lookup"><span data-stu-id="e1db1-154">Specifies whether the constraint is used for near, far or both kinds of manipulation.</span></span> <span data-ttu-id="e1db1-155">Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.</span><span class="sxs-lookup"><span data-stu-id="e1db1-155">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="e1db1-156">*Próximo:* a restrição será usada durante a manipulação próxima, se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-156">*Near*: Constraint will be used during near manipulation if selected.</span></span>
- <span data-ttu-id="e1db1-157">*Distante:* a restrição será usada durante a manipulação distante, se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-157">*Far*: Constraint will be used during far manipulation if selected.</span></span>

### <a name="faceuserconstraint"></a><span data-ttu-id="e1db1-158">FaceUserConstraint</span><span class="sxs-lookup"><span data-stu-id="e1db1-158">FaceUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FaceUser.gif" width="400" alt="Constraint Face User">

<span data-ttu-id="e1db1-159">Quando essa restrição é anexada a um objeto , a rotação será limitada para que o objeto sempre seja face ao usuário.</span><span class="sxs-lookup"><span data-stu-id="e1db1-159">When this constraint is attached to an object, rotation will be limited so that object will always face the user.</span></span> <span data-ttu-id="e1db1-160">Isso é útil para slates ou painéis.</span><span class="sxs-lookup"><span data-stu-id="e1db1-160">This is useful for slates or panels.</span></span> <span data-ttu-id="e1db1-161">As propriedades para `FaceUserConstraint` são as a seguir:</span><span class="sxs-lookup"><span data-stu-id="e1db1-161">The properties for `FaceUserConstraint` are as follows:</span></span>

#### <a name="face-away"></a><span data-ttu-id="e1db1-162">Face away</span><span class="sxs-lookup"><span data-stu-id="e1db1-162">Face away</span></span>

<span data-ttu-id="e1db1-163">O objeto faces para fora do usuário, se for true.</span><span class="sxs-lookup"><span data-stu-id="e1db1-163">Object faces away from the user if true.</span></span>

### <a name="fixeddistanceconstraint"></a><span data-ttu-id="e1db1-164">FixedDistanceConstraint</span><span class="sxs-lookup"><span data-stu-id="e1db1-164">FixedDistanceConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedDistance.gif" width="400" alt="Constraint Fixed distances">

<span data-ttu-id="e1db1-165">Essa restrição corrige a distância entre o objeto manipulado e outra transformação de objeto no início da manipulação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-165">This constraint fixes the distance between the manipulated object and another object transform on manipulation start.</span></span> <span data-ttu-id="e1db1-166">Isso é útil para comportamentos como corrigir a distância do objeto manipulado para a transformação de cabeça.</span><span class="sxs-lookup"><span data-stu-id="e1db1-166">This is useful for behaviour such as fixing the distance from the manipulated object to the head transform.</span></span> <span data-ttu-id="e1db1-167">As propriedades para `FixedDistanceConstraint` são as a seguir:</span><span class="sxs-lookup"><span data-stu-id="e1db1-167">The properties for `FixedDistanceConstraint` are as follows:</span></span>

#### <a name="constraint-transform"></a><span data-ttu-id="e1db1-168">Transformação de restrição</span><span class="sxs-lookup"><span data-stu-id="e1db1-168">Constraint transform</span></span>

<span data-ttu-id="e1db1-169">Essa é a outra transformação à que o objeto manipulado terá uma distância fixa.</span><span class="sxs-lookup"><span data-stu-id="e1db1-169">This is the other transform that the manipulated object will have a fixed distance to.</span></span> <span data-ttu-id="e1db1-170">O padrão é a transformação da câmera.</span><span class="sxs-lookup"><span data-stu-id="e1db1-170">Defaults to the camera transform.</span></span>

### <a name="fixedrotationtouserconstraint"></a><span data-ttu-id="e1db1-171">FixedRotationToUserConstraint</span><span class="sxs-lookup"><span data-stu-id="e1db1-171">FixedRotationToUserConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToUser.gif" width="400" alt="Fixed Rotation">

<span data-ttu-id="e1db1-172">Essa restrição corrige a rotação relativa entre o usuário e o objeto manipulado enquanto ele está sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-172">This constraint fixes the relative rotation between the user and the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="e1db1-173">Isso é útil para slates ou painéis, pois garante que o objeto manipulado sempre mostre a mesma face para o usuário como fez no início da manipulação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-173">This is useful for slates or panels as it ensures that the manipulated object always shows the same face to the user as it did at the start of manipulation.</span></span> <span data-ttu-id="e1db1-174">O `FixedRotationToUserConstraint` não tem nenhuma propriedade exclusiva.</span><span class="sxs-lookup"><span data-stu-id="e1db1-174">The `FixedRotationToUserConstraint` does not have any unique properties.</span></span>

### <a name="fixedrotationtoworldconstraint"></a><span data-ttu-id="e1db1-175">FixedRotationToWorldConstraint</span><span class="sxs-lookup"><span data-stu-id="e1db1-175">FixedRotationToWorldConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_FixedRotationToWorld.gif" width="400" alt="Fixed rotation to the world">

<span data-ttu-id="e1db1-176">Essa restrição corrige a rotação global do objeto manipulado enquanto ele está sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-176">This constraint fixes the global rotation of the manipulated object while it is being manipulated.</span></span> <span data-ttu-id="e1db1-177">Isso pode ser útil em casos em que nenhuma rotação deve ser imada pela manipulação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-177">This can be useful in cases where no rotation should be imparted by manipulation.</span></span> <span data-ttu-id="e1db1-178">O `FixedRotationToWorldConstraint` não tem nenhuma propriedade exclusiva:</span><span class="sxs-lookup"><span data-stu-id="e1db1-178">The `FixedRotationToWorldConstraint` does not have any unique properties:</span></span>

### <a name="maintainapparentsizeconstraint"></a><span data-ttu-id="e1db1-179">MaintainApparentSizeConstraint</span><span class="sxs-lookup"><span data-stu-id="e1db1-179">MaintainApparentSizeConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MaintainApparentSize.gif" width="400" alt="Maintain Apparent size">

<span data-ttu-id="e1db1-180">Quando essa restrição é anexada a um objeto, não importa a distância do objeto do usuário, ela manterá o mesmo tamanho aparente para o usuário (ou seja, ele assumirá a mesma proporção do campo de exibição do usuário).</span><span class="sxs-lookup"><span data-stu-id="e1db1-180">When this constraint is attached to an object, no matter how far the object is from the user, it will maintain the same apparent size to the user (i.e. it will take up the same proportion of the user's field of view).</span></span> <span data-ttu-id="e1db1-181">Isso pode ser usado para garantir que um painel de texto ou slate permaneça acessível durante a manipulação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-181">This can be used to ensure that a slate or text panel remains readable while manipulating.</span></span> <span data-ttu-id="e1db1-182">O `MaintainApparentSizeConstraint` não tem nenhuma propriedade exclusiva:</span><span class="sxs-lookup"><span data-stu-id="e1db1-182">The `MaintainApparentSizeConstraint` does not have any unique properties:</span></span>

### <a name="moveaxisconstraint"></a><span data-ttu-id="e1db1-183">MoveAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="e1db1-183">MoveAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MoveAxis.gif" width="400" alt="Constraint Move Axis">

<span data-ttu-id="e1db1-184">Essa restrição pode ser usada para corrigir em quais eixos um objeto manipulado pode ser movido.</span><span class="sxs-lookup"><span data-stu-id="e1db1-184">This constraint can be used to fix along which axes a manipulated object can be moved.</span></span> <span data-ttu-id="e1db1-185">Isso pode ser útil para manipular objetos sobre a superfície de um plano ou ao longo de uma linha.</span><span class="sxs-lookup"><span data-stu-id="e1db1-185">This can be useful for manipulating objects over the surface of a plane, or along a line.</span></span> <span data-ttu-id="e1db1-186">As propriedades para `MoveAxisConstraint` são as a seguir:</span><span class="sxs-lookup"><span data-stu-id="e1db1-186">The properties for `MoveAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-movement"></a><span data-ttu-id="e1db1-187">Restrição na movimentação</span><span class="sxs-lookup"><span data-stu-id="e1db1-187">Constraint on movement</span></span>

<span data-ttu-id="e1db1-188">Especifica em quais eixos impedir a movimentação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-188">Specifies which axes to prevent movement on.</span></span> <span data-ttu-id="e1db1-189">Por padrão, esses eixos serão globais em vez de locais, mas isso pode ser alterado abaixo.</span><span class="sxs-lookup"><span data-stu-id="e1db1-189">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="e1db1-190">Como essa propriedade é um sinalizador, qualquer número de opções pode ser selecionado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-190">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="e1db1-191">*Eixo X:* a movimentação ao longo do eixo x é restrita se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-191">*X Axis*: Movement along the x-axis is constrained if selected.</span></span>
- <span data-ttu-id="e1db1-192">*Eixo Y:* a movimentação ao longo do eixo y será restrita se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-192">*Y Axis*: Movement along the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="e1db1-193">*Eixo Z:* a movimentação ao longo do eixo z será restrita se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-193">*Z Axis*: Movement along the z-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="e1db1-194">Usar espaço local para restrição</span><span class="sxs-lookup"><span data-stu-id="e1db1-194">Use local space for constraint</span></span>

<span data-ttu-id="e1db1-195">Restringirá os eixos de transformação local do objeto manipulado se for true.</span><span class="sxs-lookup"><span data-stu-id="e1db1-195">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="e1db1-196">Falso por padrão.</span><span class="sxs-lookup"><span data-stu-id="e1db1-196">False by default.</span></span>

### <a name="rotationaxisconstraint"></a><span data-ttu-id="e1db1-197">RotationAxisConstraint</span><span class="sxs-lookup"><span data-stu-id="e1db1-197">RotationAxisConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_RotationAxis.gif" width="400" alt="Constraint Rotation Axis">

<span data-ttu-id="e1db1-198">Essa restrição pode ser usada para corrigir sobre quais eixos um objeto manipulado pode ser girado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-198">This constraint can be used to fix about which axes a manipulated object can be rotated.</span></span> <span data-ttu-id="e1db1-199">Isso pode ser útil para manter um objeto manipulado parado, mas ainda permitir rotações de eixo y, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="e1db1-199">This can be useful for keeping a manipulated object upright, but still allowing y-axis rotations, for example.</span></span> <span data-ttu-id="e1db1-200">As propriedades para `RotationAxisConstraint` são as a seguir:</span><span class="sxs-lookup"><span data-stu-id="e1db1-200">The properties for `RotationAxisConstraint` are as follows:</span></span>

#### <a name="constraint-on-rotation"></a><span data-ttu-id="e1db1-201">Restrição na rotação</span><span class="sxs-lookup"><span data-stu-id="e1db1-201">Constraint on rotation</span></span>

<span data-ttu-id="e1db1-202">Especifica sobre quais eixos evitar a rotação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-202">Specifies which axes to prevent rotation about.</span></span> <span data-ttu-id="e1db1-203">Por padrão, esses eixos serão globais em vez de locais, mas isso pode ser alterado abaixo.</span><span class="sxs-lookup"><span data-stu-id="e1db1-203">By default, these axes will be global rather than local, but this can be changed below.</span></span> <span data-ttu-id="e1db1-204">Como essa propriedade é um sinalizador, qualquer número de opções pode ser selecionado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-204">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="e1db1-205">*Eixo Y:* a rotação sobre o eixo y é restrita se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-205">*Y Axis*: Rotation about the y-axis is constrained if selected.</span></span>
- <span data-ttu-id="e1db1-206">*Eixo Z:* a rotação sobre o eixo z é restrita se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-206">*Z Axis*: Rotation about the z-axis is constrained if selected.</span></span>
- <span data-ttu-id="e1db1-207">*Eixo X:* a rotação sobre o eixo x é restrita se selecionada.</span><span class="sxs-lookup"><span data-stu-id="e1db1-207">*X Axis*: Rotation about the x-axis is constrained if selected.</span></span>

#### <a name="use-local-space-for-constraint"></a><span data-ttu-id="e1db1-208">Usar espaço local para restrição</span><span class="sxs-lookup"><span data-stu-id="e1db1-208">Use local space for constraint</span></span>

<span data-ttu-id="e1db1-209">Restringirá os eixos de transformação local do objeto manipulado se for true.</span><span class="sxs-lookup"><span data-stu-id="e1db1-209">Will constrain relative the manipulated object's local transform axes if true.</span></span> <span data-ttu-id="e1db1-210">Falso por padrão.</span><span class="sxs-lookup"><span data-stu-id="e1db1-210">False by default.</span></span>

### <a name="minmaxscaleconstraint"></a><span data-ttu-id="e1db1-211">MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="e1db1-211">MinMaxScaleConstraint</span></span>

<img src="../images/object-manipulator/MRTK_Constraint_MinMaxScale.gif" width="400" alt="Min Max Constatint">

<span data-ttu-id="e1db1-212">Essa restrição permite que os valores mínimo e máximo sejam definidos para a escala do objeto manipulado.</span><span class="sxs-lookup"><span data-stu-id="e1db1-212">This constraint allows minimum and maximum values to be set for the scale of the manipulated object.</span></span> <span data-ttu-id="e1db1-213">Isso é útil para impedir que os usuários dimensionem um objeto muito pequeno ou muito grande.</span><span class="sxs-lookup"><span data-stu-id="e1db1-213">This is useful for preventing users from scaling an object too small or too large.</span></span> <span data-ttu-id="e1db1-214">As propriedades para `MinMaxScaleConstraint` são as a seguir:</span><span class="sxs-lookup"><span data-stu-id="e1db1-214">The properties for `MinMaxScaleConstraint` are as follows:</span></span>

#### <a name="scale-minimum"></a><span data-ttu-id="e1db1-215">Dimensionar o mínimo</span><span class="sxs-lookup"><span data-stu-id="e1db1-215">Scale minimum</span></span>

<span data-ttu-id="e1db1-216">O valor de escala mínimo durante a manipulação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-216">The minimum scale value during manipulation.</span></span>

#### <a name="scale-maximum"></a><span data-ttu-id="e1db1-217">Dimensionar o máximo</span><span class="sxs-lookup"><span data-stu-id="e1db1-217">Scale maximum</span></span>

<span data-ttu-id="e1db1-218">O valor de escala máximo durante a manipulação.</span><span class="sxs-lookup"><span data-stu-id="e1db1-218">The maximum scale value during manipulation.</span></span>

#### <a name="relative-to-initial-state"></a><span data-ttu-id="e1db1-219">Relativo ao estado inicial</span><span class="sxs-lookup"><span data-stu-id="e1db1-219">Relative to initial state</span></span>

<span data-ttu-id="e1db1-220">Se true, os valores acima serão interpretados como relativos à escala inicial dos objetos.</span><span class="sxs-lookup"><span data-stu-id="e1db1-220">If true, the values above will be interpreted as relative to the objects initial scale.</span></span> <span data-ttu-id="e1db1-221">Caso contrário, eles serão interpretados como valores de escala absolutos.</span><span class="sxs-lookup"><span data-stu-id="e1db1-221">Otherwise they will be interpreted as absolute scale values.</span></span>
