---
title: Controle de limites
description: Visão geral sobre o controle de limites no MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Controle de Limites,
ms.openlocfilehash: f5f5e1f463f741eb23f75c9826034b8974baf947
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176466"
---
# <a name="bounds-control"></a><span data-ttu-id="63b8a-104">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="63b8a-104">Bounds control</span></span>

![Controle de limites](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="63b8a-106">*BoundsControl* é o novo componente para o comportamento de manipulação, encontrado anteriormente *em BoundingBox.*</span><span class="sxs-lookup"><span data-stu-id="63b8a-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="63b8a-107">O controle de limites faz várias melhorias e simplificações na instalação e adiciona novos recursos.</span><span class="sxs-lookup"><span data-stu-id="63b8a-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="63b8a-108">Esse componente é uma substituição para a caixa delimitada, que será preterida.</span><span class="sxs-lookup"><span data-stu-id="63b8a-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="63b8a-109">O [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fornece funcionalidade básica para transformar objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="63b8a-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="63b8a-110">Um controle de limites mostrará uma caixa ao redor do holograma para indicar que ele pode ser interagido.</span><span class="sxs-lookup"><span data-stu-id="63b8a-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="63b8a-111">As alças nos cantos e bordas da caixa permitem dimensionamento, rotação ou tradução do objeto.</span><span class="sxs-lookup"><span data-stu-id="63b8a-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="63b8a-112">O controle de limites também reage à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="63b8a-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="63b8a-113">No HoloLens 2, por exemplo, o controle de limites responde à proximidade do dedo, fornecendo comentários visuais para ajudar a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="63b8a-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="63b8a-114">Todas as interações e visuais podem ser facilmente personalizados.</span><span class="sxs-lookup"><span data-stu-id="63b8a-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="63b8a-115">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="63b8a-115">Example scene</span></span>

<span data-ttu-id="63b8a-116">Você pode encontrar exemplos de configurações de controle de limites na `BoundsControlExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="63b8a-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="63b8a-117">Propriedades do inspetor</span><span class="sxs-lookup"><span data-stu-id="63b8a-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="63b8a-118">Objeto de destino</span><span class="sxs-lookup"><span data-stu-id="63b8a-118">Target object</span></span>

<span data-ttu-id="63b8a-119">Essa propriedade especifica qual objeto será transformado pela manipulação de controle de limites.</span><span class="sxs-lookup"><span data-stu-id="63b8a-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="63b8a-120">Se nenhum objeto for definido, o padrão será o objeto proprietário.</span><span class="sxs-lookup"><span data-stu-id="63b8a-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="63b8a-121">Comportamento de ativação</span><span class="sxs-lookup"><span data-stu-id="63b8a-121">Activation behavior</span></span>

<span data-ttu-id="63b8a-122">Há várias opções para ativar a interface de controle de limites.</span><span class="sxs-lookup"><span data-stu-id="63b8a-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="63b8a-123">*Ativar Ao Iniciar:* o controle de limites fica visível depois que a cena é iniciada.</span><span class="sxs-lookup"><span data-stu-id="63b8a-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="63b8a-124">*Ativar por proximidade:* o controle de limites fica visível quando uma mão articulada está perto do objeto.</span><span class="sxs-lookup"><span data-stu-id="63b8a-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="63b8a-125">*Ativar por ponteiro:* o controle de limites fica visível quando é direcionado por um ponteiro de raio de mão.</span><span class="sxs-lookup"><span data-stu-id="63b8a-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="63b8a-126">*Ativar por proximidade e ponteiro:* o controle de limites fica visível quando é direcionado por um ponteiro de raio de mão ou uma mão articulada está perto do objeto.</span><span class="sxs-lookup"><span data-stu-id="63b8a-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="63b8a-127">*Ativar Manualmente:* o controle de limites não fica visível automaticamente.</span><span class="sxs-lookup"><span data-stu-id="63b8a-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="63b8a-128">Você pode ativá-lo manualmente por meio de um script acessando a propriedade boundsControl.Active.</span><span class="sxs-lookup"><span data-stu-id="63b8a-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="63b8a-129">Substituição de limites</span><span class="sxs-lookup"><span data-stu-id="63b8a-129">Bounds override</span></span>

<span data-ttu-id="63b8a-130">Define um colisor de caixa do objeto para computação de limites.</span><span class="sxs-lookup"><span data-stu-id="63b8a-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="63b8a-131">Preenchimento de caixa</span><span class="sxs-lookup"><span data-stu-id="63b8a-131">Box padding</span></span>

<span data-ttu-id="63b8a-132">Adiciona um preenchimento aos limites do colisor usados para calcular as extensão do controle.</span><span class="sxs-lookup"><span data-stu-id="63b8a-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="63b8a-133">Isso influenciará não apenas a interação, mas também afetará os visuais.</span><span class="sxs-lookup"><span data-stu-id="63b8a-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="63b8a-134">Eixo de nivelar</span><span class="sxs-lookup"><span data-stu-id="63b8a-134">Flatten axis</span></span>

<span data-ttu-id="63b8a-135">Indica se o controle é nivelado em um dos eixos, tornando-o bidimensional e não permite a manipulação ao longo desse eixo.</span><span class="sxs-lookup"><span data-stu-id="63b8a-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="63b8a-136">Esse recurso pode ser usado para objetos finos, como slates.</span><span class="sxs-lookup"><span data-stu-id="63b8a-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="63b8a-137">Se o eixo nivelado estiver definido como *Nivelar Automaticamente,* o script escolherá automaticamente o eixo com a menor extensão como eixo nivelado.</span><span class="sxs-lookup"><span data-stu-id="63b8a-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="63b8a-138">Suavização</span><span class="sxs-lookup"><span data-stu-id="63b8a-138">Smoothing</span></span>

<span data-ttu-id="63b8a-139">A seção de suavização permite configurar o comportamento de suavização para escala e rotação do controle.</span><span class="sxs-lookup"><span data-stu-id="63b8a-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="63b8a-140">Visuais</span><span class="sxs-lookup"><span data-stu-id="63b8a-140">Visuals</span></span>

<span data-ttu-id="63b8a-141">A aparência do controle de limites pode ser configurada modificando uma das configurações de visuais correspondentes.</span><span class="sxs-lookup"><span data-stu-id="63b8a-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="63b8a-142">As configurações visuais são objetos vinculados ou inlinados que podem ser scripts e são descritas mais detalhadamente na seção [do objeto de configuração](#configuration-objects).</span><span class="sxs-lookup"><span data-stu-id="63b8a-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="63b8a-143">Objetos de configuração</span><span class="sxs-lookup"><span data-stu-id="63b8a-143">Configuration Objects</span></span>

<span data-ttu-id="63b8a-144">O controle vem com um conjunto de objetos de configuração que podem ser armazenados como objetos que podem ser scripts e compartilhados entre diferentes instâncias ou pré-fabs.</span><span class="sxs-lookup"><span data-stu-id="63b8a-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="63b8a-145">As configurações podem ser compartilhadas e vinculadas como arquivos de ativos individuais com script ou ativos aninhados que podem ser script dentro de pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="63b8a-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="63b8a-146">Outras configurações também podem ser definidas diretamente na instância sem vincular a um ativo externo ou aninhado que pode ser script.</span><span class="sxs-lookup"><span data-stu-id="63b8a-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="63b8a-147">O inspetor de controle de limites indicará se uma configuração é compartilhada ou emlinada como parte da instância atual mostrando uma mensagem no inspetor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="63b8a-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="63b8a-148">Além disso, as instâncias compartilhadas não serão editáveis diretamente na própria janela de propriedades de controle de limites, mas, em vez disso, o ativo ao que está vinculando precisa ser diretamente modfiado para evitar alterações acidentais em configurações compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="63b8a-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="63b8a-149">Atualmente, o controle de limites oferece opções de objetos de configuração para os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="63b8a-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="63b8a-150">Alças</span><span class="sxs-lookup"><span data-stu-id="63b8a-150">Handles</span></span>
  * [<span data-ttu-id="63b8a-151">Alças de escala</span><span class="sxs-lookup"><span data-stu-id="63b8a-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="63b8a-152">Alças de rotação</span><span class="sxs-lookup"><span data-stu-id="63b8a-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="63b8a-153">Alças de tradução</span><span class="sxs-lookup"><span data-stu-id="63b8a-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="63b8a-154">Links/Wireframe</span><span class="sxs-lookup"><span data-stu-id="63b8a-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="63b8a-155">Exibição de caixa</span><span class="sxs-lookup"><span data-stu-id="63b8a-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="63b8a-156">Efeito de proximidade</span><span class="sxs-lookup"><span data-stu-id="63b8a-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="63b8a-157">Configuração de caixa</span><span class="sxs-lookup"><span data-stu-id="63b8a-157">Box configuration</span></span>

<span data-ttu-id="63b8a-158">A configuração da caixa é responsável por renderizar uma caixa sólida com limites definidos por meio do tamanho do colisor e preenchimento de caixa.</span><span class="sxs-lookup"><span data-stu-id="63b8a-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="63b8a-159">As propriedades a seguir podem ser configuradas:</span><span class="sxs-lookup"><span data-stu-id="63b8a-159">The following properties can be set up:</span></span>

* <span data-ttu-id="63b8a-160">**Material da** caixa : define o material aplicado à caixa renderizada quando nenhuma interação ocorre.</span><span class="sxs-lookup"><span data-stu-id="63b8a-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="63b8a-161">Uma caixa só será renderizada se esse material estiver definido.</span><span class="sxs-lookup"><span data-stu-id="63b8a-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="63b8a-162">**Material capturado por** caixa: material para a caixa quando o usuário interage com o controle, segurando por meio de interação próxima ou distante.</span><span class="sxs-lookup"><span data-stu-id="63b8a-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="63b8a-163">**Escala de exibição do** eixo de nivelar: uma escala aplicada à caixa exibida se um dos eixos for [nivelado.](#flatten-axis)</span><span class="sxs-lookup"><span data-stu-id="63b8a-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="63b8a-164">Configuração de alças de escala</span><span class="sxs-lookup"><span data-stu-id="63b8a-164">Scale handles configuration</span></span>

<span data-ttu-id="63b8a-165">Essa gaveta de propriedades permite modificar o comportamento e a visualização de alças de escala do controle de limites.</span><span class="sxs-lookup"><span data-stu-id="63b8a-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="63b8a-166">**Material do** handle: material aplicado aos alças.</span><span class="sxs-lookup"><span data-stu-id="63b8a-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="63b8a-167">**Manipular material capturado:** material aplicado à alça de segurar.</span><span class="sxs-lookup"><span data-stu-id="63b8a-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="63b8a-168">**Tratar pré-fab**: pré-fab opcional para o alça de escala.</span><span class="sxs-lookup"><span data-stu-id="63b8a-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="63b8a-169">Se non for definido, o MRTK usará um cubo como padrão.</span><span class="sxs-lookup"><span data-stu-id="63b8a-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="63b8a-170">**Tamanho do handle:** tamanho do alça de escala.</span><span class="sxs-lookup"><span data-stu-id="63b8a-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="63b8a-171">**Preenchimento do colisor:** preenchimento para adicionar ao colisor de alça.</span><span class="sxs-lookup"><span data-stu-id="63b8a-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="63b8a-172">**Desenhar ao manipular**: quando ativo desenhará uma linha de tether do ponto de início da interação até a posição atual da mão ou do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="63b8a-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="63b8a-173">**Alças ignoram colisor:** se um colisor for vinculado aqui, os alças ignorarão qualquer colisão com esse colisor.</span><span class="sxs-lookup"><span data-stu-id="63b8a-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="63b8a-174">**Lidar com o pré-fab slate**: pré-fab a ser usado para o alça quando o controle é nivelado.</span><span class="sxs-lookup"><span data-stu-id="63b8a-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="63b8a-175">**Mostrar alças de escala:** controla a visibilidade do alça.</span><span class="sxs-lookup"><span data-stu-id="63b8a-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="63b8a-176">**Comportamento de escala:** pode ser definido como dimensionamento uniforme ou não uniforme.</span><span class="sxs-lookup"><span data-stu-id="63b8a-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="63b8a-177">Configuração de alças de rotação</span><span class="sxs-lookup"><span data-stu-id="63b8a-177">Rotation handles configuration</span></span>

<span data-ttu-id="63b8a-178">Essa configuração define o comportamento do alça de rotação.</span><span class="sxs-lookup"><span data-stu-id="63b8a-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="63b8a-179">**Material do** handle: material aplicado aos alças.</span><span class="sxs-lookup"><span data-stu-id="63b8a-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="63b8a-180">**Manipular material capturado:** material aplicado à alça de segurar.</span><span class="sxs-lookup"><span data-stu-id="63b8a-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="63b8a-181">**Tratar pré-fab**: pré-fab opcional para o alça.</span><span class="sxs-lookup"><span data-stu-id="63b8a-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="63b8a-182">Se non for definido, o MRTK usará uma esfera como padrão.</span><span class="sxs-lookup"><span data-stu-id="63b8a-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="63b8a-183">**Tamanho do handle:** tamanho do alça.</span><span class="sxs-lookup"><span data-stu-id="63b8a-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="63b8a-184">**Preenchimento do colisor:** preenchimento para adicionar ao colisor de alça.</span><span class="sxs-lookup"><span data-stu-id="63b8a-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="63b8a-185">**Desenhar ao manipular**: quando ativo desenhará uma linha de tether do ponto de início da interação até a posição atual da mão ou do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="63b8a-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="63b8a-186">**Alças ignoram colisor:** se um colisor for vinculado aqui, os alças ignorarão qualquer colisão com esse colisor.</span><span class="sxs-lookup"><span data-stu-id="63b8a-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="63b8a-187">**Manipular o tipo de colisor de pré-fab**: tipo de colisor a ser usado com o identificador criado.</span><span class="sxs-lookup"><span data-stu-id="63b8a-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="63b8a-188">**Mostrar o handle para X:** controla a visibilidade do alça para o eixo X.</span><span class="sxs-lookup"><span data-stu-id="63b8a-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="63b8a-189">**Mostrar o handle para Y:** controla a visibilidade do alça para o eixo Y.</span><span class="sxs-lookup"><span data-stu-id="63b8a-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="63b8a-190">**Mostrar o handle para Z:** controla a visibilidade do alça para o eixo Z.</span><span class="sxs-lookup"><span data-stu-id="63b8a-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="63b8a-191">Configuração de alças de tradução</span><span class="sxs-lookup"><span data-stu-id="63b8a-191">Translation handles configuration</span></span>

<span data-ttu-id="63b8a-192">Permite habilenciar e configurar os alças de tradução para o controle de limites.</span><span class="sxs-lookup"><span data-stu-id="63b8a-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="63b8a-193">Observe que os alças de tradução estão desabilitados por padrão.</span><span class="sxs-lookup"><span data-stu-id="63b8a-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="63b8a-194">**Material do** handle: material aplicado aos alças.</span><span class="sxs-lookup"><span data-stu-id="63b8a-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="63b8a-195">**Manipular material capturado:** material aplicado à alça de segurar.</span><span class="sxs-lookup"><span data-stu-id="63b8a-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="63b8a-196">**Tratar pré-fab**: pré-fab opcional para o alça.</span><span class="sxs-lookup"><span data-stu-id="63b8a-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="63b8a-197">Se non for definido, o MRTK usará uma esfera como padrão.</span><span class="sxs-lookup"><span data-stu-id="63b8a-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="63b8a-198">**Tamanho do handle:** tamanho do alça.</span><span class="sxs-lookup"><span data-stu-id="63b8a-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="63b8a-199">**Preenchimento do colisor:** preenchimento para adicionar ao colisor de alça.</span><span class="sxs-lookup"><span data-stu-id="63b8a-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="63b8a-200">**Desenhar ao manipular**: quando ativo desenhará uma linha de tether do ponto de início da interação até a posição atual da mão ou do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="63b8a-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="63b8a-201">Os **identificadores ignoram o colisor**: se um colisor estiver vinculado aqui, os identificadores ignorarão qualquer colisão com esse colisor.</span><span class="sxs-lookup"><span data-stu-id="63b8a-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="63b8a-202">**Manipular tipo de colisor pré-fabricado**: tipo de colisor a ser usado com o identificador criado.</span><span class="sxs-lookup"><span data-stu-id="63b8a-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="63b8a-203">**Mostrar identificador de x**: controla a visibilidade do identificador para o eixo x.</span><span class="sxs-lookup"><span data-stu-id="63b8a-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="63b8a-204">**Mostrar identificador para y**: controla a visibilidade do identificador para o eixo y.</span><span class="sxs-lookup"><span data-stu-id="63b8a-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="63b8a-205">**Mostrar identificador para Z**: controla a visibilidade do identificador para o eixo Z.</span><span class="sxs-lookup"><span data-stu-id="63b8a-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="63b8a-206">Configuração de links (wireframe)</span><span class="sxs-lookup"><span data-stu-id="63b8a-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="63b8a-207">A configuração de links habilita o recurso de wireframe do controle de limites.</span><span class="sxs-lookup"><span data-stu-id="63b8a-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="63b8a-208">As seguintes propriedades podem ser configuradas:</span><span class="sxs-lookup"><span data-stu-id="63b8a-208">The following properties can be configured:</span></span>

* <span data-ttu-id="63b8a-209">**Material de wireframe**: o material aplicado à malha de wireframe.</span><span class="sxs-lookup"><span data-stu-id="63b8a-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="63b8a-210">**Raio da borda do wireframe**: a espessura do wireframe.</span><span class="sxs-lookup"><span data-stu-id="63b8a-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="63b8a-211">**Forma de wireframe**: a forma do Wireframe pode ser por cúbico ou cilíndrico.</span><span class="sxs-lookup"><span data-stu-id="63b8a-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="63b8a-212">**Mostrar wireframe**: controla a visibilidade do wireframe.</span><span class="sxs-lookup"><span data-stu-id="63b8a-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="63b8a-213">Configuração de efeito de proximidade</span><span class="sxs-lookup"><span data-stu-id="63b8a-213">Proximity effect configuration</span></span>

<span data-ttu-id="63b8a-214">Mostrar e ocultar os identificadores com animação com base na distância para as mãos.</span><span class="sxs-lookup"><span data-stu-id="63b8a-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="63b8a-215">Ele tem uma animação de dimensionamento em duas etapas.</span><span class="sxs-lookup"><span data-stu-id="63b8a-215">It has two-step scaling animation.</span></span> <span data-ttu-id="63b8a-216">os padrões são definidos para o comportamento de estilo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="63b8a-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="63b8a-217">**Efeito de proximidade ativo**: habilitar a ativação de identificador baseado em proximidade</span><span class="sxs-lookup"><span data-stu-id="63b8a-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="63b8a-218">**Proximidade da mídia do objeto**: distância para o dimensionamento da 1ª etapa</span><span class="sxs-lookup"><span data-stu-id="63b8a-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="63b8a-219">**Proximidade do objeto**: distância para o dimensionamento da 2ª etapa</span><span class="sxs-lookup"><span data-stu-id="63b8a-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="63b8a-220">**Escala extrema**: o valor de escala padrão do ativo de identificador quando as mãos estão fora do intervalo da interação de controle de limites (distância definida acima por ' tratar a proximidade média '.</span><span class="sxs-lookup"><span data-stu-id="63b8a-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="63b8a-221">Use 0 para ocultar o identificador por padrão)</span><span class="sxs-lookup"><span data-stu-id="63b8a-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="63b8a-222">**Escala média**: o valor de escala do ativo de identificador quando as mãos estão dentro do intervalo da interação de controle de limites (distância definida acima por ' manipular proximidades à próxima '.</span><span class="sxs-lookup"><span data-stu-id="63b8a-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="63b8a-223">Use 1 para mostrar o tamanho normal)</span><span class="sxs-lookup"><span data-stu-id="63b8a-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="63b8a-224">**Fechar escala**: o valor de escala do ativo de identificador quando as mãos estão dentro do intervalo da interação de captura (distância definida acima por ' manipular proximidades à próxima '.</span><span class="sxs-lookup"><span data-stu-id="63b8a-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="63b8a-225">Use 1. x para mostrar um tamanho maior)</span><span class="sxs-lookup"><span data-stu-id="63b8a-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="63b8a-226">**Taxa de crescimento distante**: Classifique uma escala de objetos dimensionados de proximidade quando a mão passa de uma distância média para a extrema.</span><span class="sxs-lookup"><span data-stu-id="63b8a-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="63b8a-227">**Taxa de crescimento médio**: Classifique uma escala de objetos dimensionados de proximidade quando a mão passa de uma proximidade para a próxima.</span><span class="sxs-lookup"><span data-stu-id="63b8a-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="63b8a-228">**Fechar taxa de crescimento**: taxa um objeto escalado de proximidade é dimensionado quando a mão passa do próximo proximidade para a central de objetos.</span><span class="sxs-lookup"><span data-stu-id="63b8a-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="63b8a-229">Sistema de restrição</span><span class="sxs-lookup"><span data-stu-id="63b8a-229">Constraint System</span></span>

<span data-ttu-id="63b8a-230">O controle de limites dá suporte ao uso do [Gerenciador de restrição](constraint-manager.md) para limitar ou modificar o comportamento de conversão, rotação ou dimensionamento ao usar identificadores de controle de limites.</span><span class="sxs-lookup"><span data-stu-id="63b8a-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="63b8a-231">O Inspetor de propriedades mostrará todos os gerenciadores de restrição disponíveis anexados ao mesmo objeto de jogo em uma lista suspensa com uma opção para rolar e realçar o Gerenciador de restrição selecionado.</span><span class="sxs-lookup"><span data-stu-id="63b8a-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="63b8a-232">Eventos</span><span class="sxs-lookup"><span data-stu-id="63b8a-232">Events</span></span>

<span data-ttu-id="63b8a-233">O controle de limites fornece os seguintes eventos.</span><span class="sxs-lookup"><span data-stu-id="63b8a-233">Bounds control provides the following events.</span></span> <span data-ttu-id="63b8a-234">Este exemplo usa esses eventos para reproduzir comentários de áudio.</span><span class="sxs-lookup"><span data-stu-id="63b8a-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="63b8a-235">**Rotação iniciada**: acionada quando a rotação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="63b8a-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="63b8a-236">**Rotação interrompida**: acionada quando a rotação para.</span><span class="sxs-lookup"><span data-stu-id="63b8a-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="63b8a-237">**Escala iniciada**: acionada quando o dimensionamento é iniciado.</span><span class="sxs-lookup"><span data-stu-id="63b8a-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="63b8a-238">**Escala interrompida**: acionada quando o dimensionamento é interrompido.</span><span class="sxs-lookup"><span data-stu-id="63b8a-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="63b8a-239">**Conversão iniciada**: dispara quando a tradução é iniciada.</span><span class="sxs-lookup"><span data-stu-id="63b8a-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="63b8a-240">**Traduzir parado**: é acionado quando a tradução para.</span><span class="sxs-lookup"><span data-stu-id="63b8a-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="63b8a-241">Elásticos (experimental)</span><span class="sxs-lookup"><span data-stu-id="63b8a-241">Elastics (Experimental)</span></span>

<span data-ttu-id="63b8a-242">Os elásticos podem ser usados ao manipular objetos por meio de controle de limites.</span><span class="sxs-lookup"><span data-stu-id="63b8a-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="63b8a-243">Observe que o [sistema elásticos](../experimental/elastic-system.md) ainda está em estado experimental.</span><span class="sxs-lookup"><span data-stu-id="63b8a-243">Note that the [elastics system](../experimental/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="63b8a-244">Para habilitar os elásticos, vincule um componente do Gerenciador de elásticos existente ou crie e vincule um novo Gerenciador de elásticos por meio do `Add Elastics Manager` botão.</span><span class="sxs-lookup"><span data-stu-id="63b8a-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="63b8a-245">Estilos de identificador</span><span class="sxs-lookup"><span data-stu-id="63b8a-245">Handle styles</span></span>

<span data-ttu-id="63b8a-246">por padrão, quando você apenas atribui o [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, ele mostrará o identificador do estilo de HoloLens 1ª gen.</span><span class="sxs-lookup"><span data-stu-id="63b8a-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="63b8a-247">para usar os identificadores de estilo HoloLens 2, você precisa atribuir o identificador adequado pré-fabricados e materiais.</span><span class="sxs-lookup"><span data-stu-id="63b8a-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Estilos de alça de controle de limites 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="63b8a-249">abaixo estão os valores de pré-fabricados, materiais e dimensionamento para os identificadores de controle de limites de estilo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="63b8a-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="63b8a-250">Você pode encontrar este exemplo na `BoundsControlExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="63b8a-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="63b8a-251">identificadores (instalação para HoloLens estilo 2)</span><span class="sxs-lookup"><span data-stu-id="63b8a-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="63b8a-252">**Material de tratamento**: BoundingBoxHandleWhite. passe-partout</span><span class="sxs-lookup"><span data-stu-id="63b8a-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="63b8a-253">**Tratar material capturado**: BoundingBoxHandleBlueGrabbed. passe-partout</span><span class="sxs-lookup"><span data-stu-id="63b8a-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="63b8a-254">**Identificador de escala pré-fabricado**: MRTK_BoundingBox_ScaleHandle. pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="63b8a-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="63b8a-255">**Alça de escala Slate pré-fabricado**: MRTK_BoundingBox_ScaleHandle_Slate. pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="63b8a-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="63b8a-256">**Tamanho do identificador de escala**: 0, 16 (1.6 cm)</span><span class="sxs-lookup"><span data-stu-id="63b8a-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="63b8a-257">**Enchimento do Colisador da alça de escala**: 0, 16 (torna o colisor de captura ligeiramente maior que o Visual do manipulador)</span><span class="sxs-lookup"><span data-stu-id="63b8a-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="63b8a-258">**Identificador de rotação pré-fabricado**: MRTK_BoundingBox_RotateHandle. pré-fabricado</span><span class="sxs-lookup"><span data-stu-id="63b8a-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="63b8a-259">**Tamanho da alça de rotação**: 0, 16</span><span class="sxs-lookup"><span data-stu-id="63b8a-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="63b8a-260">**Enchimento do Colisador da alça de rotação**: 0, 16 (torna o colisor de captura ligeiramente maior que o Visual do manipulador)</span><span class="sxs-lookup"><span data-stu-id="63b8a-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="63b8a-261">Alterações de transformação com o objeto manipulador</span><span class="sxs-lookup"><span data-stu-id="63b8a-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="63b8a-262">Um controle de limites pode ser usado em combinação com [`ObjectManipulator.cs`](object-manipulator.md) para permitir certos tipos de manipulação (por exemplo,</span><span class="sxs-lookup"><span data-stu-id="63b8a-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="63b8a-263">movendo o objeto) sem usar identificadores.</span><span class="sxs-lookup"><span data-stu-id="63b8a-263">moving the object) without using handles.</span></span> <span data-ttu-id="63b8a-264">O manipulador de manipulação dá suporte a interações de uma e de duas mãos.</span><span class="sxs-lookup"><span data-stu-id="63b8a-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="63b8a-265">O [rastreamento manual](../input/hand-tracking.md) pode ser usado para interagir com um objeto de perto.</span><span class="sxs-lookup"><span data-stu-id="63b8a-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="63b8a-266">Para que as bordas de controle de limites se comportem da mesma maneira ao movê-lo usando a [`ObjectManipulator`](object-manipulator.md) interação de longe, é aconselhável conectar seus eventos para a *manipulação iniciada*  /  *na manipulação encerrada* `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` , conforme mostrado na captura de tela acima.</span><span class="sxs-lookup"><span data-stu-id="63b8a-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="63b8a-267">Como adicionar e configurar um controle de limites usando o Inspetor do Unity</span><span class="sxs-lookup"><span data-stu-id="63b8a-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="63b8a-268">Adicionar Colisor de caixa a um objeto</span><span class="sxs-lookup"><span data-stu-id="63b8a-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="63b8a-269">Atribuir `BoundsControl` script a um objeto</span><span class="sxs-lookup"><span data-stu-id="63b8a-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="63b8a-270">Configurar opções, como métodos de ' ativação ' (consulte a seção [Propriedades do Inspetor](#inspector-properties) abaixo)</span><span class="sxs-lookup"><span data-stu-id="63b8a-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="63b8a-271">Adicional atribuir pré-fabricados e materiais para um controle de limites de estilo de HoloLens 2 (consulte a seção de [estilos de identificador](#handle-styles) abaixo)</span><span class="sxs-lookup"><span data-stu-id="63b8a-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="63b8a-272">Use o *objeto de destino* e o campo de substituição de *limites* no Inspetor para atribuir um objeto específico e um colisor no objeto com vários componentes filho.</span><span class="sxs-lookup"><span data-stu-id="63b8a-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Controle de limites](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="63b8a-274">Como adicionar e configurar um controle de limites no código</span><span class="sxs-lookup"><span data-stu-id="63b8a-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="63b8a-275">Criar instância de gameobject do cubo</span><span class="sxs-lookup"><span data-stu-id="63b8a-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="63b8a-276">Atribuir `BoundsControl` script a um objeto com o colisor, usando o addComponent<> ()</span><span class="sxs-lookup"><span data-stu-id="63b8a-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="63b8a-277">Configure as opções diretamente no controle ou por meio de uma das configurações programáveis (consulte a seção Propriedades e [configurações](#configuration-objects) do [Inspetor](#inspector-properties) abaixo)</span><span class="sxs-lookup"><span data-stu-id="63b8a-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="63b8a-278">Adicional atribua pré-fabricados e materiais para um controle de limites de estilo de HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="63b8a-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="63b8a-279">Isso ainda requer atribuições por meio do Inspetor, pois os materiais e pré-fabricados devem ser carregados dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="63b8a-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="63b8a-280">O uso da pasta ' recursos ' ou do [sombreador]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) do Unity. não é recomendável localizar sombreadores dinamicamente, pois as permutações do sombreador podem estar ausentes no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="63b8a-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

```c#
BoxDisplayConfiguration boxConfiguration = boundsControl.BoxDisplayConfig;
boxConfiguration.BoxMaterial = [Assign BoundingBox.mat]
boxConfiguration.BoxGrabbedMaterial = [Assign BoundingBoxGrabbed.mat]
ScaleHandlesConfiguration scaleHandleConfiguration = boundsControl.ScaleHandlesConfig;
scaleHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
scaleHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
scaleHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_ScaleHandle.prefab]
scaleHandleConfiguration.HandleSlatePrefab = [Assign MRTK_BoundingBox_ScaleHandle_Slate.prefab]
scaleHandleConfiguration.HandleSize = 0.016f;
scaleHandleConfiguration.ColliderPadding = 0.016f;
RotationHandlesConfiguration rotationHandleConfiguration = boundsControl.RotationHandlesConfig;
rotationHandleConfiguration.HandleMaterial = [Assign BoundingBoxHandleWhite.mat]
rotationHandleConfiguration.HandleGrabbedMaterial = [Assign BoundingBoxHandleBlueGrabbed.mat]
rotationHandleConfiguration.HandlePrefab = [Assign MRTK_BoundingBox_RotateHandle.prefab]
rotationHandleConfiguration.HandleSize = 0.016f;
rotationHandleConfiguration.ColliderPadding = 0.016f;
```

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="63b8a-281">Exemplo: definir a escala de controle de limites mínimos máximos usando MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="63b8a-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="63b8a-282">Para definir a escala mínima e máxima, anexe uma [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) ao seu controle.</span><span class="sxs-lookup"><span data-stu-id="63b8a-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="63b8a-283">Como o controle limites anexa automaticamente e ativa o Gerenciador de restrição, o MinMaxScaleConstraint será aplicado automaticamente à transformação é alterada quando ela é anexada e configurada.</span><span class="sxs-lookup"><span data-stu-id="63b8a-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="63b8a-284">Você também pode usar MinMaxScaleConstraint para definir a escala mínima e máxima para [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .</span><span class="sxs-lookup"><span data-stu-id="63b8a-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="63b8a-285">Exemplo: Adicionar controle de limites em um objeto Game</span><span class="sxs-lookup"><span data-stu-id="63b8a-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="63b8a-286">Para adicionar um controle de limites em um objeto, basta adicionar um `BoundsControl` componente a ele:</span><span class="sxs-lookup"><span data-stu-id="63b8a-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="63b8a-287">Migrando da caixa delimitadora</span><span class="sxs-lookup"><span data-stu-id="63b8a-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="63b8a-288">Pré-fabricados e instâncias existentes usando a [caixa delimitadora](bounding-box.md) podem ser atualizados para o novo controle de limites por meio da [janela de migração](../tools/migration-window.md) que faz parte do pacote de ferramentas do MRTK.</span><span class="sxs-lookup"><span data-stu-id="63b8a-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="63b8a-289">Para atualizar instâncias individuais da caixa delimitadora também há uma opção de migração dentro do Inspetor de propriedades do componente.</span><span class="sxs-lookup"><span data-stu-id="63b8a-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="63b8a-290">Confira também</span><span class="sxs-lookup"><span data-stu-id="63b8a-290">See also</span></span>

* [<span data-ttu-id="63b8a-291">Manipulador de objeto</span><span class="sxs-lookup"><span data-stu-id="63b8a-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="63b8a-292">Gerenciador de restrição</span><span class="sxs-lookup"><span data-stu-id="63b8a-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="63b8a-293">Janela de migração</span><span class="sxs-lookup"><span data-stu-id="63b8a-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="63b8a-294">Sistema elásticos (experimental)</span><span class="sxs-lookup"><span data-stu-id="63b8a-294">Elastics system (Experimental)</span></span>](../experimental/elastic-system.md)
