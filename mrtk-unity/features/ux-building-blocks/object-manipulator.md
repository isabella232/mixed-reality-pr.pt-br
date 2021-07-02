---
title: Manipulador de objeto
description: Como usar o objeto manipulador no MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, manipulação de objetos,
ms.openlocfilehash: f9b644c1447d6776389e227bfe49c27f82a3cf31
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176655"
---
# <a name="object-manipulator"></a><span data-ttu-id="0bc99-104">Manipulador de objeto</span><span class="sxs-lookup"><span data-stu-id="0bc99-104">Object manipulator</span></span>

![Manipulador de objeto](../images/manipulation-handler/MRTK_Manipulation_Main.png)

<span data-ttu-id="0bc99-106">O *Objectmanipuletor* é o novo componente para o comportamento de manipulação, encontrado anteriormente em *ManipulationHandler*.</span><span class="sxs-lookup"><span data-stu-id="0bc99-106">The *ObjectManipulator* is the new component for manipulation behaviour, previously found in *ManipulationHandler*.</span></span> <span data-ttu-id="0bc99-107">O objeto manipulador faz uma série de aprimoramentos e simplificações.</span><span class="sxs-lookup"><span data-stu-id="0bc99-107">The object manipulator makes a number of improvements and simplifications.</span></span> <span data-ttu-id="0bc99-108">Esse componente é uma substituição para o manipulador de manipulação, que será preterido.</span><span class="sxs-lookup"><span data-stu-id="0bc99-108">This component is a replacement for the manipulation handler, which will be deprecated.</span></span>

<span data-ttu-id="0bc99-109">O script *Objectmanipuletor* torna um objeto móvel, escalonável e rotatable usando uma ou duas mãos.</span><span class="sxs-lookup"><span data-stu-id="0bc99-109">The *ObjectManipulator* script makes an object movable, scalable, and rotatable using one or two hands.</span></span> <span data-ttu-id="0bc99-110">O objeto manipulador pode ser configurado para controlar como o objeto responderá a várias entradas.</span><span class="sxs-lookup"><span data-stu-id="0bc99-110">The object manipulator can be configured to control how the object will respond to various inputs.</span></span> <span data-ttu-id="0bc99-111">o script deve funcionar com a maioria das formas de interação, como HoloLens duas mãos, HoloLens raios de duas mãos, HoloLens 1 olhar e gestos e entrada do controlador de movimento do headset de imersão.</span><span class="sxs-lookup"><span data-stu-id="0bc99-111">The script should work with most forms of interaction, such as HoloLens 2 articulated hand, HoloLens 2 hand rays, HoloLens 1 gaze and gestures and immersive headset motion controller input.</span></span>

> [!VIDEO https://channel9.msdn.com/Shows/Docs-Mixed-Reality/Using-Object-Manipulator-in-Mixed-Reality-Toolkit/player]

## <a name="how-to-use-the-object-manipulator"></a><span data-ttu-id="0bc99-112">Como usar o objeto manipulador</span><span class="sxs-lookup"><span data-stu-id="0bc99-112">How to use the object manipulator</span></span>

<span data-ttu-id="0bc99-113">Para usar o objeto manipulador, primeiro adicione o `ObjectManipulator` componente script a um gameobject.</span><span class="sxs-lookup"><span data-stu-id="0bc99-113">To use the object manipulator, first add the `ObjectManipulator` script component to a GameObject.</span></span> <span data-ttu-id="0bc99-114">Certifique-se também de adicionar um colisor ao objeto, correspondendo seus limites de captura.</span><span class="sxs-lookup"><span data-stu-id="0bc99-114">Make sure to also add a collider to the object, matching its grabbable bounds.</span></span>

<span data-ttu-id="0bc99-115">Para fazer com que o objeto responda à entrada de mão articulada Near, adicione o `NearInteractionGrabbable` script também.</span><span class="sxs-lookup"><span data-stu-id="0bc99-115">To make the object respond to near articulated hand input, add the `NearInteractionGrabbable` script as well.</span></span>

<span data-ttu-id="0bc99-116">O comportamento da física pode ser habilitado para o objeto manipulador adicionando um componente rigidbody ao objeto.</span><span class="sxs-lookup"><span data-stu-id="0bc99-116">Physics behaviour can be enabled for the object manipulator by adding a rigidbody component to the object.</span></span> <span data-ttu-id="0bc99-117">O comportamento de física habilitado adicionando esse componente é discutido com mais detalhes em [*física e colisões*](#physics-and-collisions).</span><span class="sxs-lookup"><span data-stu-id="0bc99-117">Physics behaviour enabled by adding this component is discussed in greater detail in [*Physics and collisions*](#physics-and-collisions).</span></span>

<span data-ttu-id="0bc99-118">Assim, a manipulação pode ser restrita com a adição de componentes de [restrição de manipulação](constraint-manager.md#transform-constraints) ao objeto.</span><span class="sxs-lookup"><span data-stu-id="0bc99-118">As well as this, manipulation can be constrained by adding [manipulation constraint components](constraint-manager.md#transform-constraints) to the object.</span></span> <span data-ttu-id="0bc99-119">Esses são componentes especiais que funcionam com a manipulação e alteram o comportamento de manipulação de alguma forma.</span><span class="sxs-lookup"><span data-stu-id="0bc99-119">These are special components that work with manipulation and change the manipulation behaviour in some way.</span></span>

![Usando o manipulador de manipulação no editor do Unity](../images/object-manipulator/MRTK_ObjectManipulator_Howto.png)

## <a name="inspector-properties-and-fields"></a><span data-ttu-id="0bc99-121">Propriedades e campos do Inspetor</span><span class="sxs-lookup"><span data-stu-id="0bc99-121">Inspector properties and fields</span></span>

<img src="../images/object-manipulator/MRTK_ObjectManipulator_Structure.png" width="450" alt="Object Manipulator Structure">

### <a name="general-properties"></a><span data-ttu-id="0bc99-122">Propriedades gerais</span><span class="sxs-lookup"><span data-stu-id="0bc99-122">General properties</span></span>

#### <a name="host-transform"></a><span data-ttu-id="0bc99-123">Transformação de host</span><span class="sxs-lookup"><span data-stu-id="0bc99-123">Host transform</span></span>

<span data-ttu-id="0bc99-124">A transformação do objeto que será manipulada.</span><span class="sxs-lookup"><span data-stu-id="0bc99-124">The object transform that will be manipulated.</span></span> <span data-ttu-id="0bc99-125">O padrão é o objeto do componente.</span><span class="sxs-lookup"><span data-stu-id="0bc99-125">Defaults to the object of the component.</span></span>

#### <a name="manipulation-type"></a><span data-ttu-id="0bc99-126">Tipo de manipulação</span><span class="sxs-lookup"><span data-stu-id="0bc99-126">Manipulation type</span></span>

<span data-ttu-id="0bc99-127">Especifica se o objeto pode ser manipulado usando uma ou duas mãos.</span><span class="sxs-lookup"><span data-stu-id="0bc99-127">Specifies whether the object can be manipulated using one hand or two hands.</span></span> <span data-ttu-id="0bc99-128">Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.</span><span class="sxs-lookup"><span data-stu-id="0bc99-128">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="0bc99-129">*Uma mão*: habilita a manipulação de uma mão, se selecionada.</span><span class="sxs-lookup"><span data-stu-id="0bc99-129">*One handed*: Enables one handed manipulation if selected.</span></span>
- <span data-ttu-id="0bc99-130">*Duas mãos*: habilita a manipulação de duas mãos, se selecionada.</span><span class="sxs-lookup"><span data-stu-id="0bc99-130">*Two handed*: Enables two handed manipulation if selected.</span></span>

#### <a name="allow-far-manipulation"></a><span data-ttu-id="0bc99-131">Permitir manipulação distante</span><span class="sxs-lookup"><span data-stu-id="0bc99-131">Allow far manipulation</span></span>

<span data-ttu-id="0bc99-132">Especifica se a manipulação pode ser feita usando a interação de longe com ponteiros.</span><span class="sxs-lookup"><span data-stu-id="0bc99-132">Specifies whether manipulation can be done using far interaction with pointers.</span></span>

### <a name="one-handed-manipulation-properties"></a><span data-ttu-id="0bc99-133">Propriedades de manipulação de uma mão</span><span class="sxs-lookup"><span data-stu-id="0bc99-133">One handed manipulation properties</span></span>

#### <a name="one-hand-rotation-mode-near"></a><span data-ttu-id="0bc99-134">Modo de rotação de um lado próximo</span><span class="sxs-lookup"><span data-stu-id="0bc99-134">One hand rotation mode near</span></span>

<span data-ttu-id="0bc99-135">Especifica como o objeto se comportará quando estiver sendo capturado com uma mão perto de.</span><span class="sxs-lookup"><span data-stu-id="0bc99-135">Specifies how the object will behave when it is being grabbed with one hand near.</span></span> <span data-ttu-id="0bc99-136">Essas opções funcionam apenas para as mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="0bc99-136">These options only work for articulated hands.</span></span>

- <span data-ttu-id="0bc99-137">*Girar sobre o centro de objetos*: o objeto gira usando a rotação da mão, mas sobre o ponto central de objetos.</span><span class="sxs-lookup"><span data-stu-id="0bc99-137">*Rotate about object center*: Object rotates using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="0bc99-138">O objeto parecerá ficar menos à medida que gira, mas pode haver uma sensação de desconexão entre a mão e o objeto.</span><span class="sxs-lookup"><span data-stu-id="0bc99-138">The object will appear to move less as it rotates, but there may be a feeling of disconnection between the hand and the object.</span></span> <span data-ttu-id="0bc99-139">Mais útil para interações distantes.</span><span class="sxs-lookup"><span data-stu-id="0bc99-139">More useful for far interaction.</span></span>
- <span data-ttu-id="0bc99-140">*Girar sobre o ponto de captura*: gire o objeto com a mão sobre o ponto de captura entre o polegar e o dedo do índice.</span><span class="sxs-lookup"><span data-stu-id="0bc99-140">*Rotate about grab point*: Rotate object with the hand about the grab point between the thumb and index finger.</span></span> <span data-ttu-id="0bc99-141">Deve parecer que o objeto está sendo mantido por mão.</span><span class="sxs-lookup"><span data-stu-id="0bc99-141">It should feel as if the object is being held by the hand.</span></span>

#### <a name="one-hand-rotation-mode-far"></a><span data-ttu-id="0bc99-142">Modo de rotação unidirecional distante</span><span class="sxs-lookup"><span data-stu-id="0bc99-142">One hand rotation mode far</span></span>

<span data-ttu-id="0bc99-143">Especifica como o objeto se comportará quando estiver sendo capturado com uma mão à distância.</span><span class="sxs-lookup"><span data-stu-id="0bc99-143">Specifies how the object will behave when it is being grabbed with one hand at distance.</span></span> <span data-ttu-id="0bc99-144">Essas opções funcionam apenas para as mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="0bc99-144">These options only work for articulated hands.</span></span>

- <span data-ttu-id="0bc99-145">*Girar sobre a central de objetos*: girar o objeto usando a rotação da mão, mas sobre o ponto central de objetos.</span><span class="sxs-lookup"><span data-stu-id="0bc99-145">*Rotate about object center*: Rotate object using rotation of the hand, but about the object center point.</span></span> <span data-ttu-id="0bc99-146">Útil para inspecionar em uma distância sem que o centro de objetos se mova enquanto o objeto gira.</span><span class="sxs-lookup"><span data-stu-id="0bc99-146">Useful for inspecting at a distance without the object center moving as the object rotates.</span></span>
- <span data-ttu-id="0bc99-147">*Girar sobre o ponto de captura*: girar o objeto usando a rotação da mão, mas sobre o ponto de acesso do ponteiro Ray.</span><span class="sxs-lookup"><span data-stu-id="0bc99-147">*Rotate about grab point*: Rotate object using rotation of the hand, but about the pointer ray hit point.</span></span> <span data-ttu-id="0bc99-148">Útil para inspeção.</span><span class="sxs-lookup"><span data-stu-id="0bc99-148">Useful for inspection.</span></span>

### <a name="two-handed-manipulation-properties"></a><span data-ttu-id="0bc99-149">Duas propriedades de manipulação de mão</span><span class="sxs-lookup"><span data-stu-id="0bc99-149">Two handed manipulation properties</span></span>

#### <a name="two-handed-manipulation-type"></a><span data-ttu-id="0bc99-150">Tipo de manipulação de duas mãos</span><span class="sxs-lookup"><span data-stu-id="0bc99-150">Two handed manipulation type</span></span>

<span data-ttu-id="0bc99-151">Especifica como a manipulação de duas mãos pode transformar um objeto.</span><span class="sxs-lookup"><span data-stu-id="0bc99-151">Specifies how two hand manipulation can transform an object.</span></span> <span data-ttu-id="0bc99-152">Como essa propriedade é um sinalizador, qualquer número de opções pode ser selecionado.</span><span class="sxs-lookup"><span data-stu-id="0bc99-152">Because this property is a flag, any number of options can be selected.</span></span>

- <span data-ttu-id="0bc99-153">*Mover*: a movimentação é permitida se selecionada.</span><span class="sxs-lookup"><span data-stu-id="0bc99-153">*Move*: Moving is allowed if selected.</span></span>
- <span data-ttu-id="0bc99-154">*Escala*: o dimensionamento é permitido se selecionado.</span><span class="sxs-lookup"><span data-stu-id="0bc99-154">*Scale*: Scaling is allowed if selected.</span></span>
- <span data-ttu-id="0bc99-155">*Girar*: a rotação é permitida se selecionada.</span><span class="sxs-lookup"><span data-stu-id="0bc99-155">*Rotate*: Rotation is allowed if selected.</span></span>

![Manipulador de manipulação](../images/manipulation-handler/MRTK_ManipulationHandler_TwoHanded.jpg)

### <a name="constraints"></a><span data-ttu-id="0bc99-157">Restrições</span><span class="sxs-lookup"><span data-stu-id="0bc99-157">Constraints</span></span>

#### <a name="enable-constraints"></a><span data-ttu-id="0bc99-158">Habilitar restrições</span><span class="sxs-lookup"><span data-stu-id="0bc99-158">Enable constraints</span></span>

<span data-ttu-id="0bc99-159">Essa configuração habilitará o [Gerenciador de restrição](constraint-manager.md)vinculado.</span><span class="sxs-lookup"><span data-stu-id="0bc99-159">This setting will enable the linked [constraint manager](constraint-manager.md).</span></span> <span data-ttu-id="0bc99-160">As alterações de transformação serão processadas por restrições registradas para o [Gerenciador de restrição](constraint-manager.md)selecionado.</span><span class="sxs-lookup"><span data-stu-id="0bc99-160">Transform changes will be processed by constraints registered to the selected [constraint manager](constraint-manager.md).</span></span>

#### <a name="constraint-manager"></a><span data-ttu-id="0bc99-161">Gerenciador de restrição</span><span class="sxs-lookup"><span data-stu-id="0bc99-161">Constraint manager</span></span>

<span data-ttu-id="0bc99-162">A lista suspensa permite selecionar qualquer um dos [gerenciadores de restrição](constraint-manager.md)anexados.</span><span class="sxs-lookup"><span data-stu-id="0bc99-162">The dropdown allows to select any of the attached [constraint managers](constraint-manager.md).</span></span> <span data-ttu-id="0bc99-163">O objeto manipulador garante que há um [Gerenciador de restrição](constraint-manager.md) anexado em todos os momentos.</span><span class="sxs-lookup"><span data-stu-id="0bc99-163">Object manipulator ensures there's a [constraint manager](constraint-manager.md) attached at all times.</span></span>
<span data-ttu-id="0bc99-164">Observe que vários componentes do mesmo tipo serão exibidos com o mesmo nome no Unity.</span><span class="sxs-lookup"><span data-stu-id="0bc99-164">Note that multiple components of the same type will show up under the same name in unity.</span></span> <span data-ttu-id="0bc99-165">Para facilitar a distinção entre vários gerenciadores de restrição no mesmo objeto, as opções disponíveis mostrarão uma dica na configuração do Gerenciador de restrição selecionado (seleção de restrição manual ou automática).</span><span class="sxs-lookup"><span data-stu-id="0bc99-165">To make it easier to distinguish between multiple constraint managers on the same object, the available options will show a hint on the configuration of the selected constraint manager (manual or auto constraint selection).</span></span>

#### <a name="go-to-component"></a><span data-ttu-id="0bc99-166">Ir para o componente</span><span class="sxs-lookup"><span data-stu-id="0bc99-166">Go to component</span></span>

<span data-ttu-id="0bc99-167">A seleção do Gerenciador de restrição vem com um botão *ir para componente* .</span><span class="sxs-lookup"><span data-stu-id="0bc99-167">The constraint manager selection comes with a *Go to component* button.</span></span> <span data-ttu-id="0bc99-168">Esse botão fará com que o Inspetor role para o componente selecionado para que ele possa ser configurado.</span><span class="sxs-lookup"><span data-stu-id="0bc99-168">This button will cause the inspector to scroll to the selected component so that it can be configured.</span></span>

### <a name="physics"></a><span data-ttu-id="0bc99-169">Física</span><span class="sxs-lookup"><span data-stu-id="0bc99-169">Physics</span></span>

<span data-ttu-id="0bc99-170">Configurações nesta seção aparecerão somente quando o objeto tiver um componente RigidBody.</span><span class="sxs-lookup"><span data-stu-id="0bc99-170">Settings in this section appear only when the object has a RigidBody component.</span></span>

#### <a name="release-behavior"></a><span data-ttu-id="0bc99-171">Comportamento da versão</span><span class="sxs-lookup"><span data-stu-id="0bc99-171">Release behavior</span></span>

<span data-ttu-id="0bc99-172">Especifique quais propriedades físicas um objeto manipulado deve manter após a liberação.</span><span class="sxs-lookup"><span data-stu-id="0bc99-172">Specify which physical properties a manipulated object should keep upon release.</span></span> <span data-ttu-id="0bc99-173">Como essa propriedade é um sinalizador, ambas as opções podem ser selecionadas.</span><span class="sxs-lookup"><span data-stu-id="0bc99-173">Because this property is a flag, both options can be selected.</span></span>

- <span data-ttu-id="0bc99-174">*Manter a velocidade*: quando o objeto for liberado, se essa opção for selecionada, ela manterá sua velocidade linear.</span><span class="sxs-lookup"><span data-stu-id="0bc99-174">*Keep Velocity*: When the object is released, if this option is selected it will keep its linear velocity.</span></span>
- <span data-ttu-id="0bc99-175">*manter Angular velocidade*: quando o objeto for liberado, se essa opção for selecionada, ela manterá sua velocidade Angular.</span><span class="sxs-lookup"><span data-stu-id="0bc99-175">*Keep Angular Velocity*: When the object is released, if this option is selected it will keep its angular velocity.</span></span>

#### <a name="use-forces-for-near-manipulation"></a><span data-ttu-id="0bc99-176">Usar forças para manipulação próxima</span><span class="sxs-lookup"><span data-stu-id="0bc99-176">Use forces for near manipulation</span></span>

<span data-ttu-id="0bc99-177">Se as forças de física são usadas para mover o objeto ao executar quase as manipulações.</span><span class="sxs-lookup"><span data-stu-id="0bc99-177">Whether physics forces are used to move the object when performing near manipulations.</span></span> <span data-ttu-id="0bc99-178">Definir isso como *false* fará com que o objeto se sinta mais diretamente conectado à mão dos usuários.</span><span class="sxs-lookup"><span data-stu-id="0bc99-178">Setting this to *false* will make the object feel more directly connected to the users hand.</span></span> <span data-ttu-id="0bc99-179">Definir como *true* vai respeitar a massa e a inércia do objeto, mas pode parecer que o objeto está conectado por uma mola.</span><span class="sxs-lookup"><span data-stu-id="0bc99-179">Setting this to *true* will honor the mass and inertia of the object, but may feel as though the object is connected through a spring.</span></span> <span data-ttu-id="0bc99-180">O padrão é *false*.</span><span class="sxs-lookup"><span data-stu-id="0bc99-180">The default is *false*.</span></span>

### <a name="smoothing"></a><span data-ttu-id="0bc99-181">Suavização</span><span class="sxs-lookup"><span data-stu-id="0bc99-181">Smoothing</span></span>

#### <a name="smoothing-far"></a><span data-ttu-id="0bc99-182">Suavizando a distância</span><span class="sxs-lookup"><span data-stu-id="0bc99-182">Smoothing far</span></span>

<span data-ttu-id="0bc99-183">Se a suavização independente de taxa de quadros está habilitada para interações distantes.</span><span class="sxs-lookup"><span data-stu-id="0bc99-183">Whether frame-rate independent smoothing is enabled for far interactions.</span></span> <span data-ttu-id="0bc99-184">A suavização está habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="0bc99-184">Far smoothing is enabled by default.</span></span>

#### <a name="smoothing-near"></a><span data-ttu-id="0bc99-185">Suavizando ao lado</span><span class="sxs-lookup"><span data-stu-id="0bc99-185">Smoothing near</span></span>

<span data-ttu-id="0bc99-186">Se a suavização independente de taxa de quadros está habilitada para interações próximas.</span><span class="sxs-lookup"><span data-stu-id="0bc99-186">Whether frame-rate independent smoothing is enabled for near interactions.</span></span> <span data-ttu-id="0bc99-187">A suavização próxima é desabilitada por padrão porque o efeito pode ser percebido como "desconectado" da mão.</span><span class="sxs-lookup"><span data-stu-id="0bc99-187">Near smoothing is disabled by default because the effect may be perceived as being 'disconnected' from the hand.</span></span>

#### <a name="smoothing-active"></a><span data-ttu-id="0bc99-188">Suavizando ativos</span><span class="sxs-lookup"><span data-stu-id="0bc99-188">Smoothing active</span></span>

<span data-ttu-id="0bc99-189">Obsoleto e será removido em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="0bc99-189">Obsolete and will be removed in a future version.</span></span> <span data-ttu-id="0bc99-190">Os aplicativos devem usar SmoothingFar, SmoothingNear ou uma combinação dos dois.</span><span class="sxs-lookup"><span data-stu-id="0bc99-190">Applications should use SmoothingFar, SmoothingNear or a combination of the two.</span></span>

#### <a name="move-lerp-time"></a><span data-ttu-id="0bc99-191">Mover tempo Lerp</span><span class="sxs-lookup"><span data-stu-id="0bc99-191">Move lerp time</span></span>

<span data-ttu-id="0bc99-192">Quantidade de suavização a ser aplicada ao movimento.</span><span class="sxs-lookup"><span data-stu-id="0bc99-192">Amount of smoothing to apply to the movement.</span></span> <span data-ttu-id="0bc99-193">A suavização de 0 significa sem suavização.</span><span class="sxs-lookup"><span data-stu-id="0bc99-193">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="0bc99-194">Valor máximo significa nenhuma alteração no valor.</span><span class="sxs-lookup"><span data-stu-id="0bc99-194">Max value means no change to value.</span></span>

#### <a name="rotate-lerp-time"></a><span data-ttu-id="0bc99-195">Girar Lerp tempo</span><span class="sxs-lookup"><span data-stu-id="0bc99-195">Rotate lerp time</span></span>

<span data-ttu-id="0bc99-196">Quantidade de suavização a ser aplicada à rotação.</span><span class="sxs-lookup"><span data-stu-id="0bc99-196">Amount of smoothing to apply to the rotation.</span></span> <span data-ttu-id="0bc99-197">A suavização de 0 significa sem suavização.</span><span class="sxs-lookup"><span data-stu-id="0bc99-197">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="0bc99-198">Valor máximo significa nenhuma alteração no valor.</span><span class="sxs-lookup"><span data-stu-id="0bc99-198">Max value means no change to value.</span></span>

#### <a name="scale-lerp-time"></a><span data-ttu-id="0bc99-199">Tempo de Lerp de escala</span><span class="sxs-lookup"><span data-stu-id="0bc99-199">Scale lerp time</span></span>

<span data-ttu-id="0bc99-200">Quantidade de suavização a ser aplicada à escala.</span><span class="sxs-lookup"><span data-stu-id="0bc99-200">Amount of smoothing to apply to the scale.</span></span> <span data-ttu-id="0bc99-201">A suavização de 0 significa sem suavização.</span><span class="sxs-lookup"><span data-stu-id="0bc99-201">Smoothing of 0 means no smoothing.</span></span> <span data-ttu-id="0bc99-202">Valor máximo significa nenhuma alteração no valor.</span><span class="sxs-lookup"><span data-stu-id="0bc99-202">Max value means no change to value.</span></span>

### <a name="manipulation-events"></a><span data-ttu-id="0bc99-203">Eventos de manipulação</span><span class="sxs-lookup"><span data-stu-id="0bc99-203">Manipulation events</span></span>

<span data-ttu-id="0bc99-204">O manipulador de manipulação fornece os seguintes eventos:</span><span class="sxs-lookup"><span data-stu-id="0bc99-204">Manipulation handler provides the following events:</span></span>

- <span data-ttu-id="0bc99-205">*OnManipulationStarted*: acionado quando a manipulação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="0bc99-205">*OnManipulationStarted*: Fired when manipulation starts.</span></span>
- <span data-ttu-id="0bc99-206">*OnManipulationEnded*: é acionado quando a manipulação termina.</span><span class="sxs-lookup"><span data-stu-id="0bc99-206">*OnManipulationEnded*: Fires when the manipulation ends.</span></span>
- <span data-ttu-id="0bc99-207">*OnHoverStarted*: é acionado quando uma mão/controlador focaliza o manipulável, próximo ou longe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-207">*OnHoverStarted*: Fires when a hand / controller hovers the manipulatable, near or far.</span></span>
- <span data-ttu-id="0bc99-208">*OnHoverEnded*: é acionado quando uma mão/controlador não passa o mouse sobre manipulável, próximo ou longe.</span><span class="sxs-lookup"><span data-stu-id="0bc99-208">*OnHoverEnded*: Fires when a hand / controller un-hovers the manipulatable, near or far.</span></span>

<span data-ttu-id="0bc99-209">A ordem de acionamento do evento para manipulação é:</span><span class="sxs-lookup"><span data-stu-id="0bc99-209">The event fire order for manipulation is:</span></span>

<span data-ttu-id="0bc99-210">*OnHoverStarted*  ->  *OnManipulationStarted*  ->  *OnManipulationEnded*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="0bc99-210">*OnHoverStarted* -> *OnManipulationStarted* -> *OnManipulationEnded* -> *OnHoverEnded*</span></span>

<span data-ttu-id="0bc99-211">Se não houver nenhuma manipulação, você ainda receberá eventos em foco com a seguinte ordem de incêndio:</span><span class="sxs-lookup"><span data-stu-id="0bc99-211">If there is no manipulation, you will still get hover events with the following fire order:</span></span>

<span data-ttu-id="0bc99-212">*OnHoverStarted*  ->  *OnHoverEnded*</span><span class="sxs-lookup"><span data-stu-id="0bc99-212">*OnHoverStarted* -> *OnHoverEnded*</span></span>

## <a name="physics-and-collisions"></a><span data-ttu-id="0bc99-213">Física e colisões</span><span class="sxs-lookup"><span data-stu-id="0bc99-213">Physics and collisions</span></span>

<span data-ttu-id="0bc99-214">O comportamento da física pode ser habilitado adicionando um componente rigidbody ao mesmo objeto que um objeto manipulador.</span><span class="sxs-lookup"><span data-stu-id="0bc99-214">Physics behaviour can be enabled by adding a rigidbody component to the same object as an object manipulator.</span></span> <span data-ttu-id="0bc99-215">Isso não apenas permite a configuração do [comportamento de versão](#release-behavior) acima, além de habilitar colisões.</span><span class="sxs-lookup"><span data-stu-id="0bc99-215">Not only does this enable configuration of [release behaviour](#release-behavior) above, it also enables collisions.</span></span> <span data-ttu-id="0bc99-216">Sem um componente rigidbody, as colisões não se comportam corretamente durante a manipulação:</span><span class="sxs-lookup"><span data-stu-id="0bc99-216">Without a rigidbody component, collisions don't behave correctly during manipulation:</span></span>

- <span data-ttu-id="0bc99-217">As colisões entre um objeto manipulado e um colisor estático (ou seja, um objeto com um colisor, mas sem rigidbody) não funcionam, o objeto manipulado passa diretamente pelo colisor estático não afetado.</span><span class="sxs-lookup"><span data-stu-id="0bc99-217">Collisions between a manipulated object and a static collider (i.e. an object with a collider but no rigidbody) do not work, the manipulated object passes straight through the static collider unaffected.</span></span>
- <span data-ttu-id="0bc99-218">Colisões entre um objeto manipulado e um rigidbody (ou seja,</span><span class="sxs-lookup"><span data-stu-id="0bc99-218">Collisions between a manipulated object and a rigidbody (i.e</span></span> <span data-ttu-id="0bc99-219">um objeto com um colisor e um rigidbody) faz com que o rigidbody tenha uma resposta de colisão, mas a resposta é um salto e não natural.</span><span class="sxs-lookup"><span data-stu-id="0bc99-219">an object with both a collider and a rigidbody) cause the rigidbody to have a collision response, but the response is jumpy and unnatural.</span></span> <span data-ttu-id="0bc99-220">Também não há nenhuma resposta de colisão no objeto manipulado.</span><span class="sxs-lookup"><span data-stu-id="0bc99-220">There is also no collision response on the manipulated object.</span></span>

<span data-ttu-id="0bc99-221">Quando um rigidbody é adicionado, as colisões devem funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="0bc99-221">When a rigidbody is added, collisions should work correctly.</span></span>

### <a name="without-rigidbody"></a><span data-ttu-id="0bc99-222">Sem rigidbody</span><span class="sxs-lookup"><span data-stu-id="0bc99-222">Without rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_NoRigidbody.gif" width="500" alt="No Rigid Body">

### <a name="with-rigidbody"></a><span data-ttu-id="0bc99-223">Com rigidbody</span><span class="sxs-lookup"><span data-stu-id="0bc99-223">With rigidbody</span></span>

<img src="../images/object-manipulator/MRTK_PhysicsManipulation_Rigidbody.gif" width="500" alt="Rigid Body">

## <a name="elastics-experimental"></a><span data-ttu-id="0bc99-224">Elásticos (experimental)</span><span class="sxs-lookup"><span data-stu-id="0bc99-224">Elastics (Experimental)</span></span>

<span data-ttu-id="0bc99-225">Os elásticos podem ser usados ao manipular objetos por meio de manipulador de objeto.</span><span class="sxs-lookup"><span data-stu-id="0bc99-225">Elastics can be used when manipulating objects via object manipulator.</span></span> <span data-ttu-id="0bc99-226">Observe que o [sistema elásticos](../experimental/elastic-system.md) ainda está em estado experimental.</span><span class="sxs-lookup"><span data-stu-id="0bc99-226">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="0bc99-227">Para habilitar os elásticos, vincule um componente do Gerenciador de elásticos existente ou crie e vincule um novo Gerenciador de elásticos por meio do `Add Elastics Manager` botão.</span><span class="sxs-lookup"><span data-stu-id="0bc99-227">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds Control Elastics">

## <a name="see-also"></a><span data-ttu-id="0bc99-228">Confira também</span><span class="sxs-lookup"><span data-stu-id="0bc99-228">See also</span></span>

- [<span data-ttu-id="0bc99-229">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="0bc99-229">Bounds control</span></span>](bounds-control.md)
- [<span data-ttu-id="0bc99-230">Gerenciador de restrição</span><span class="sxs-lookup"><span data-stu-id="0bc99-230">Constraint manager</span></span>](constraint-manager.md)
- [<span data-ttu-id="0bc99-231">Janela de migração</span><span class="sxs-lookup"><span data-stu-id="0bc99-231">Migration window</span></span>](../tools/migration-window.md)
- [<span data-ttu-id="0bc99-232">Sistema elásticos (experimental)</span><span class="sxs-lookup"><span data-stu-id="0bc99-232">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
