---
title: BoundsControl
description: Visão geral sobre o controle de limites no MRTK
author: thalbern
ms.author: bethalha
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, controle de limites,
ms.openlocfilehash: 65558861955f782cf9d81a8bb4ec3a31dee03fde
ms.sourcegitcommit: 95ea5f3cf873acc93c4614fbccaa093e0f5186f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2021
ms.locfileid: "110487723"
---
# <a name="bounds-control"></a><span data-ttu-id="8a783-104">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="8a783-104">Bounds control</span></span>

![Controle de limites](../images/bounds-control/MRTK_BoundsControl_Main.png)

<span data-ttu-id="8a783-106">*BoundsControl* é o novo componente para o comportamento de manipulação, encontrado anteriormente em *BoundingBox*.</span><span class="sxs-lookup"><span data-stu-id="8a783-106">*BoundsControl* is the new component for manipulation behaviour, previously found in *BoundingBox*.</span></span> <span data-ttu-id="8a783-107">O controle de limites faz uma série de aprimoramentos e simplificações na instalação e adiciona novos recursos.</span><span class="sxs-lookup"><span data-stu-id="8a783-107">Bounds control makes a number of improvements and simplifications in setup and adds new features.</span></span> <span data-ttu-id="8a783-108">Esse componente é uma substituição para a caixa delimitadora, que será preterida.</span><span class="sxs-lookup"><span data-stu-id="8a783-108">This component is a replacement for the bounding box, which will be deprecated.</span></span>

<span data-ttu-id="8a783-109">O [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script fornece a funcionalidade básica para transformar objetos em realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="8a783-109">The [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script provides basic functionality for transforming objects in mixed reality.</span></span> <span data-ttu-id="8a783-110">Um controle de limites mostrará uma caixa ao contrário do holograma para indicar que ele pode ser interagindo.</span><span class="sxs-lookup"><span data-stu-id="8a783-110">A bounds control will show a box around the hologram to indicate that it can be interacted with.</span></span> <span data-ttu-id="8a783-111">As alças nos cantos e nas bordas da caixa permitem dimensionar, girar ou traduzir o objeto.</span><span class="sxs-lookup"><span data-stu-id="8a783-111">Handles on the corners and edges of the box allow scaling, rotating or translating the object.</span></span> <span data-ttu-id="8a783-112">O controle de limites também reage à entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="8a783-112">The bounds control also reacts to user input.</span></span> <span data-ttu-id="8a783-113">No HoloLens 2, por exemplo, o controle de limites responde à proximidade do dedo, fornecendo comentários visuais para ajudar a perceber a distância do objeto.</span><span class="sxs-lookup"><span data-stu-id="8a783-113">On HoloLens 2, for example, the bounds control responds to finger proximity, providing visual feedback to help perceive the distance from the object.</span></span> <span data-ttu-id="8a783-114">Todas as interações e visuais podem ser facilmente personalizados.</span><span class="sxs-lookup"><span data-stu-id="8a783-114">All interactions and visuals can be easily customized.</span></span>

## <a name="example-scene"></a><span data-ttu-id="8a783-115">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="8a783-115">Example scene</span></span>

<span data-ttu-id="8a783-116">Você pode encontrar exemplos de configurações de controle de limites na `BoundsControlExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="8a783-116">You can find examples of bounds control configurations in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Examples.png" alt="Bounds control Example">

## <a name="inspector-properties"></a><span data-ttu-id="8a783-117">Propriedades do Inspetor</span><span class="sxs-lookup"><span data-stu-id="8a783-117">Inspector properties</span></span>

### <a name="target-object"></a><span data-ttu-id="8a783-118">Objeto de destino</span><span class="sxs-lookup"><span data-stu-id="8a783-118">Target object</span></span>

<span data-ttu-id="8a783-119">Esta propriedade especifica qual objeto será transformado pela manipulação de controle de limites.</span><span class="sxs-lookup"><span data-stu-id="8a783-119">This property specifies which object will get transformed by the bounds control manipulation.</span></span> <span data-ttu-id="8a783-120">Se nenhum objeto for definido, o padrão será o objeto do proprietário.</span><span class="sxs-lookup"><span data-stu-id="8a783-120">If no object is set, it defaults to the owner object.</span></span>

### <a name="activation-behavior"></a><span data-ttu-id="8a783-121">Comportamento de ativação</span><span class="sxs-lookup"><span data-stu-id="8a783-121">Activation behavior</span></span>

<span data-ttu-id="8a783-122">Há várias opções para ativar a interface de controle de limites.</span><span class="sxs-lookup"><span data-stu-id="8a783-122">There are several options to activate the bounds control interface.</span></span>

* <span data-ttu-id="8a783-123">*Ativar ao iniciar*: o controle de limites se torna visível depois que a cena é iniciada.</span><span class="sxs-lookup"><span data-stu-id="8a783-123">*Activate On Start*: Bounds control becomes visible once the scene is started.</span></span>
* <span data-ttu-id="8a783-124">*Ativar por proximidade*: o controle de limites se torna visível quando uma mão articulada está perto do objeto.</span><span class="sxs-lookup"><span data-stu-id="8a783-124">*Activate By Proximity*: Bounds control becomes visible when an articulated hand is close to the object.</span></span>
* <span data-ttu-id="8a783-125">*Ativar por ponteiro*: o controle de limites se torna visível quando é direcionado por um ponteiro de raio à mão.</span><span class="sxs-lookup"><span data-stu-id="8a783-125">*Activate By Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer.</span></span>
* <span data-ttu-id="8a783-126">*Ativar por proximidade e ponteiro*: o controle de limites se torna visível quando é direcionado por um ponteiro de raio à mão ou uma mão articulada é próxima ao objeto.</span><span class="sxs-lookup"><span data-stu-id="8a783-126">*Activate By Proximity and Pointer*: Bounds control becomes visible when it is targeted by a hand-ray pointer or an articulated hand is close to the object.</span></span>
* <span data-ttu-id="8a783-127">*Ativar manualmente*: o controle de limites não se torna visível automaticamente.</span><span class="sxs-lookup"><span data-stu-id="8a783-127">*Activate Manually*: Bounds control does not become visible automatically.</span></span> <span data-ttu-id="8a783-128">Você pode ativá-lo manualmente por meio de um script acessando a propriedade boundsControl. Active.</span><span class="sxs-lookup"><span data-stu-id="8a783-128">You can manually activate it through a script by accessing the boundsControl.Active property.</span></span>

### <a name="bounds-override"></a><span data-ttu-id="8a783-129">Substituição de limites</span><span class="sxs-lookup"><span data-stu-id="8a783-129">Bounds override</span></span>

<span data-ttu-id="8a783-130">Define um colisor de caixa do objeto para computação de limites.</span><span class="sxs-lookup"><span data-stu-id="8a783-130">Sets a box collider from the object for bounds computation.</span></span>

### <a name="box-padding"></a><span data-ttu-id="8a783-131">Preenchimento de caixa</span><span class="sxs-lookup"><span data-stu-id="8a783-131">Box padding</span></span>

<span data-ttu-id="8a783-132">Adiciona um preenchimento aos limites do colisor usados para calcular as extensões do controle.</span><span class="sxs-lookup"><span data-stu-id="8a783-132">Adds a padding to the collider bounds used to calculate the extents of the control.</span></span> <span data-ttu-id="8a783-133">Isso influenciará não apenas a interação, mas também afetará os visuais.</span><span class="sxs-lookup"><span data-stu-id="8a783-133">This will influence not only interaction but also impact the visuals.</span></span>

### <a name="flatten-axis"></a><span data-ttu-id="8a783-134">Nivelar eixo</span><span class="sxs-lookup"><span data-stu-id="8a783-134">Flatten axis</span></span>

<span data-ttu-id="8a783-135">Indica se o controle é achatado em um dos eixos, tornando-o bidimensional e desautorizando a manipulação ao longo desse eixo.</span><span class="sxs-lookup"><span data-stu-id="8a783-135">Indicates whether the control is flattened in one of the axes, making it 2 dimensional and disallowing manipulation along that axis.</span></span> <span data-ttu-id="8a783-136">Esse recurso pode ser usado para objetos finos como slates.</span><span class="sxs-lookup"><span data-stu-id="8a783-136">This feature can be used for thin objects like slates.</span></span>
<span data-ttu-id="8a783-137">Se o eixo achatado estiver definido como *automático achatado* , o script selecionará automaticamente o eixo com a menor extensão que o eixo achatado.</span><span class="sxs-lookup"><span data-stu-id="8a783-137">If flatten axis is set to *Flatten Auto* the script will automatically pick the axis with the smallest extent as flatten axis.</span></span>

### <a name="smoothing"></a><span data-ttu-id="8a783-138">Suavização</span><span class="sxs-lookup"><span data-stu-id="8a783-138">Smoothing</span></span>

<span data-ttu-id="8a783-139">A seção suavização permite configurar o comportamento de suavização para dimensionar e girar o controle.</span><span class="sxs-lookup"><span data-stu-id="8a783-139">The smoothing section allows to configure smoothing behavior for scale and rotate of the control.</span></span>

### <a name="visuals"></a><span data-ttu-id="8a783-140">Visuais</span><span class="sxs-lookup"><span data-stu-id="8a783-140">Visuals</span></span>

<span data-ttu-id="8a783-141">A aparência do controle de limites pode ser configurada modificando uma das configurações visuais correspondentes.</span><span class="sxs-lookup"><span data-stu-id="8a783-141">The appearance of bounds control can be configured by modifying one of the corresponding visuals configurations.</span></span>
<span data-ttu-id="8a783-142">As configurações visuais são objetos vinculados ou embutidos em script e são descritos mais detalhadamente na [seção objeto de configuração](#configuration-objects).</span><span class="sxs-lookup"><span data-stu-id="8a783-142">Visual configurations are either linked or inlined scriptable objects and are described in more detail in the [configuration object section](#configuration-objects).</span></span>

## <a name="configuration-objects"></a><span data-ttu-id="8a783-143">Objetos de configuração</span><span class="sxs-lookup"><span data-stu-id="8a783-143">Configuration Objects</span></span>

<span data-ttu-id="8a783-144">O controle vem com um conjunto de objetos de configuração que podem ser armazenados como objetos programáveis e compartilhados entre diferentes instâncias ou pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="8a783-144">The control comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="8a783-145">As configurações podem ser compartilhadas e vinculadas como arquivos de ativo programáveis por script ou ativos de script aninhados individuais dentro do pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="8a783-145">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="8a783-146">Configurações adicionais também podem ser definidas diretamente na instância sem vínculo com um ativo com script aninhado ou externo.</span><span class="sxs-lookup"><span data-stu-id="8a783-146">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="8a783-147">O Inspetor de controle de limites indicará se uma configuração é compartilhada ou embutida como parte da instância atual, mostrando uma mensagem no Inspetor de propriedades.</span><span class="sxs-lookup"><span data-stu-id="8a783-147">The bounds control inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="8a783-148">Além disso, as instâncias compartilhadas não serão editáveis diretamente na própria janela de propriedades de controle de limites, mas o ativo ao qual está vinculando precisará ser diretamente modificado para evitar alterações acidentais em configurações compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="8a783-148">In addition shared instances won't be editable directly in the bounds control property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="8a783-149">Atualmente, o controle de limites oferece opções de objetos de configuração para os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="8a783-149">Currently bounds control offers configuration objects options for the following features:</span></span>

* <span data-ttu-id="8a783-150">Alças</span><span class="sxs-lookup"><span data-stu-id="8a783-150">Handles</span></span>
  * [<span data-ttu-id="8a783-151">Alças de escala</span><span class="sxs-lookup"><span data-stu-id="8a783-151">Scale handles</span></span>](#scale-handles-configuration)
  * [<span data-ttu-id="8a783-152">Alças de rotação</span><span class="sxs-lookup"><span data-stu-id="8a783-152">Rotation handles</span></span>](#rotation-handles-configuration)
  * [<span data-ttu-id="8a783-153">Identificadores de tradução</span><span class="sxs-lookup"><span data-stu-id="8a783-153">Translation handles</span></span>](#translation-handles-configuration)
* [<span data-ttu-id="8a783-154">Links/wireframe</span><span class="sxs-lookup"><span data-stu-id="8a783-154">Links / Wireframe</span></span>](#links-configuration-wireframe)
* [<span data-ttu-id="8a783-155">Exibição da caixa</span><span class="sxs-lookup"><span data-stu-id="8a783-155">Box display</span></span>](#box-configuration)
* [<span data-ttu-id="8a783-156">Efeito de proximidade</span><span class="sxs-lookup"><span data-stu-id="8a783-156">Proximity effect</span></span>](#proximity-effect-configuration)

### <a name="box-configuration"></a><span data-ttu-id="8a783-157">Configuração de caixa</span><span class="sxs-lookup"><span data-stu-id="8a783-157">Box configuration</span></span>

<span data-ttu-id="8a783-158">A configuração Box é responsável por renderizar uma caixa sólida com limites definidos por meio do tamanho do colisor e do preenchimento da caixa.</span><span class="sxs-lookup"><span data-stu-id="8a783-158">The box configuration is responsible for rendering a solid box with bounds defined via collider size and box padding.</span></span> <span data-ttu-id="8a783-159">As propriedades a seguir podem ser configuradas:</span><span class="sxs-lookup"><span data-stu-id="8a783-159">The following properties can be set up:</span></span>

* <span data-ttu-id="8a783-160">**Material da caixa**: define o material aplicado à caixa renderizada quando nenhuma interação ocorre.</span><span class="sxs-lookup"><span data-stu-id="8a783-160">**Box material**: defines the material applied to the rendered box when no interaction takes place.</span></span> <span data-ttu-id="8a783-161">Uma caixa só será renderizada se esse material estiver definido.</span><span class="sxs-lookup"><span data-stu-id="8a783-161">A box will only be rendered if this material is set.</span></span>
* <span data-ttu-id="8a783-162">**Material capturado de caixa**: material para a caixa quando o usuário interage com o controle, pegando por meio de interação próxima ou extrema.</span><span class="sxs-lookup"><span data-stu-id="8a783-162">**Box grabbed material**: material for the box when the user interacts with the control by grabbing via near or far interaction.</span></span>
* <span data-ttu-id="8a783-163">**Escala de exibição do eixo achatado**: uma escala aplicada à caixa é exibida se um dos eixos é [achatado](#flatten-axis).</span><span class="sxs-lookup"><span data-stu-id="8a783-163">**Flatten axis display scale**: a scale that is applied to the box display if one of the axes is [flattened](#flatten-axis).</span></span>

### <a name="scale-handles-configuration"></a><span data-ttu-id="8a783-164">Configuração de alças de escala</span><span class="sxs-lookup"><span data-stu-id="8a783-164">Scale handles configuration</span></span>

<span data-ttu-id="8a783-165">Essa gaveta de propriedade permite modificar o comportamento e a visualização de alças de escala do controle de limites.</span><span class="sxs-lookup"><span data-stu-id="8a783-165">This property drawer allows to modify behavior and visualization of scale handles of bounds control.</span></span>

* <span data-ttu-id="8a783-166">**Material de manuseio**: material aplicado às alças.</span><span class="sxs-lookup"><span data-stu-id="8a783-166">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="8a783-167">**Tratar material capturado**: material aplicado ao identificador capturado.</span><span class="sxs-lookup"><span data-stu-id="8a783-167">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="8a783-168">**Tratar pré-fabricado**: pré-fabricado opcional para a alça de dimensionamento.</span><span class="sxs-lookup"><span data-stu-id="8a783-168">**Handle prefab**: optional prefab for the scale handle.</span></span> <span data-ttu-id="8a783-169">Se não for definido, MRTK usará um cubo como padrão.</span><span class="sxs-lookup"><span data-stu-id="8a783-169">If non is set MRTK will use a cube as default.</span></span>
* <span data-ttu-id="8a783-170">**Tamanho do identificador**: tamanho da alça de escala.</span><span class="sxs-lookup"><span data-stu-id="8a783-170">**Handle size**: size of the scale handle.</span></span>
* <span data-ttu-id="8a783-171">**Preenchimento do colisor**: preenchimento a ser adicionado ao colisor do identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-171">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="8a783-172">**Desenhar o compartilhamento de Internet ao manipular**: quando ativo, você desenhará uma linha de compartilhamento de Internet a partir do ponto de início da interação com a posição atual ou do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8a783-172">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="8a783-173">Os **identificadores ignoram o colisor**: se um colisor estiver vinculado aqui, os identificadores ignorarão qualquer colisão com esse colisor.</span><span class="sxs-lookup"><span data-stu-id="8a783-173">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="8a783-174">**Tratar pré-fabricado Slate**: pré-fabricado a ser usado para o identificador quando o controle for nivelado.</span><span class="sxs-lookup"><span data-stu-id="8a783-174">**Handle slate prefab**: prefab to use for the handle when the control is flattened.</span></span>
* <span data-ttu-id="8a783-175">**Mostrar alças de escala**: controla a visibilidade do identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-175">**Show scale handles**: controls visibility of the handle.</span></span>
* <span data-ttu-id="8a783-176">**Comportamento de escala**: pode ser definido como dimensionamento uniforme ou não uniforme.</span><span class="sxs-lookup"><span data-stu-id="8a783-176">**Scale behavior**: can be set to uniform or non-uniform scaling.</span></span>

### <a name="rotation-handles-configuration"></a><span data-ttu-id="8a783-177">Configuração de identificadores de rotação</span><span class="sxs-lookup"><span data-stu-id="8a783-177">Rotation handles configuration</span></span>

<span data-ttu-id="8a783-178">Essa configuração define o comportamento do identificador de rotação.</span><span class="sxs-lookup"><span data-stu-id="8a783-178">This configuration defines the rotation handle behavior.</span></span>

* <span data-ttu-id="8a783-179">**Material de manuseio**: material aplicado às alças.</span><span class="sxs-lookup"><span data-stu-id="8a783-179">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="8a783-180">**Tratar material capturado**: material aplicado ao identificador capturado.</span><span class="sxs-lookup"><span data-stu-id="8a783-180">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="8a783-181">**Tratar pré-fabricado**: pré-fabricado opcional para o identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-181">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="8a783-182">Se não for definido, MRTK usará uma esfera como padrão.</span><span class="sxs-lookup"><span data-stu-id="8a783-182">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="8a783-183">**Tamanho do identificador**: tamanho do identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-183">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="8a783-184">**Preenchimento do colisor**: preenchimento a ser adicionado ao colisor do identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-184">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="8a783-185">**Desenhar o compartilhamento de Internet ao manipular**: quando ativo, você desenhará uma linha de compartilhamento de Internet a partir do ponto de início da interação com a posição atual ou do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8a783-185">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="8a783-186">Os **identificadores ignoram o colisor**: se um colisor estiver vinculado aqui, os identificadores ignorarão qualquer colisão com esse colisor.</span><span class="sxs-lookup"><span data-stu-id="8a783-186">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="8a783-187">**Manipular tipo de colisor pré-fabricado**: tipo de colisor a ser usado com o identificador criado.</span><span class="sxs-lookup"><span data-stu-id="8a783-187">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="8a783-188">**Mostrar identificador de x**: controla a visibilidade do identificador para o eixo x.</span><span class="sxs-lookup"><span data-stu-id="8a783-188">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="8a783-189">**Mostrar identificador para y**: controla a visibilidade do identificador para o eixo y.</span><span class="sxs-lookup"><span data-stu-id="8a783-189">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="8a783-190">**Mostrar identificador para Z**: controla a visibilidade do identificador para o eixo Z.</span><span class="sxs-lookup"><span data-stu-id="8a783-190">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="translation-handles-configuration"></a><span data-ttu-id="8a783-191">Configuração de identificadores de tradução</span><span class="sxs-lookup"><span data-stu-id="8a783-191">Translation handles configuration</span></span>

<span data-ttu-id="8a783-192">Permite habilitar e configurar identificadores de tradução para controle de limites.</span><span class="sxs-lookup"><span data-stu-id="8a783-192">Allows enabling and configuring translation handles for bounds control.</span></span> <span data-ttu-id="8a783-193">Observe que os identificadores de tradução são desabilitados por padrão.</span><span class="sxs-lookup"><span data-stu-id="8a783-193">Note that translation handles are disabled per default.</span></span>

* <span data-ttu-id="8a783-194">**Material de manuseio**: material aplicado às alças.</span><span class="sxs-lookup"><span data-stu-id="8a783-194">**Handle material**: material applied to the handles.</span></span>
* <span data-ttu-id="8a783-195">**Tratar material capturado**: material aplicado ao identificador capturado.</span><span class="sxs-lookup"><span data-stu-id="8a783-195">**Handle grabbed material**: material applied to the grabbed handle.</span></span>
* <span data-ttu-id="8a783-196">**Tratar pré-fabricado**: pré-fabricado opcional para o identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-196">**Handle prefab**: optional prefab for the handle.</span></span> <span data-ttu-id="8a783-197">Se não for definido, MRTK usará uma esfera como padrão.</span><span class="sxs-lookup"><span data-stu-id="8a783-197">If non is set MRTK will use a sphere as default.</span></span>
* <span data-ttu-id="8a783-198">**Tamanho do identificador**: tamanho do identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-198">**Handle size**: size of the handle.</span></span>
* <span data-ttu-id="8a783-199">**Preenchimento do colisor**: preenchimento a ser adicionado ao colisor do identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-199">**Collider padding**: padding to add to the handle collider.</span></span>
* <span data-ttu-id="8a783-200">**Desenhar o compartilhamento de Internet ao manipular**: quando ativo, você desenhará uma linha de compartilhamento de Internet a partir do ponto de início da interação com a posição atual ou do ponteiro.</span><span class="sxs-lookup"><span data-stu-id="8a783-200">**Draw tether when manipulating**: when active will draw a tether line from point of start of interaction to current hand or pointer position.</span></span>
* <span data-ttu-id="8a783-201">**Alças ignoram colisor:** se um colisor for vinculado aqui, os alças ignorarão qualquer colisão com esse colisor.</span><span class="sxs-lookup"><span data-stu-id="8a783-201">**Handles ignore collider**: if a collider gets linked here, handles will ignore any collision with this collider.</span></span>
* <span data-ttu-id="8a783-202">**Manipular o tipo de colisor de pré-fab**: tipo de colisor a ser usado com o identificador criado.</span><span class="sxs-lookup"><span data-stu-id="8a783-202">**Handle prefab collider type**: collider type to be used with the created handle.</span></span>
* <span data-ttu-id="8a783-203">**Mostrar o handle para X:** controla a visibilidade do alça para o eixo X.</span><span class="sxs-lookup"><span data-stu-id="8a783-203">**Show handle for X**: controls visibility of the handle for X axis.</span></span>
* <span data-ttu-id="8a783-204">**Mostrar o handle para Y:** controla a visibilidade do alça para o eixo Y.</span><span class="sxs-lookup"><span data-stu-id="8a783-204">**Show handle for Y**: controls visibility of the handle for Y axis.</span></span>
* <span data-ttu-id="8a783-205">**Mostrar o handle para Z:** controla a visibilidade do alça para o eixo Z.</span><span class="sxs-lookup"><span data-stu-id="8a783-205">**Show handle for Z**: controls visibility of the handle for Z axis.</span></span>

### <a name="links-configuration-wireframe"></a><span data-ttu-id="8a783-206">Configuração de links (wireframe)</span><span class="sxs-lookup"><span data-stu-id="8a783-206">Links configuration (wireframe)</span></span>

<span data-ttu-id="8a783-207">A configuração de links habilita o recurso wireframe do controle de limites.</span><span class="sxs-lookup"><span data-stu-id="8a783-207">The links configuration enables the wireframe feature of bounds control.</span></span> <span data-ttu-id="8a783-208">As propriedades a seguir podem ser configuradas:</span><span class="sxs-lookup"><span data-stu-id="8a783-208">The following properties can be configured:</span></span>

* <span data-ttu-id="8a783-209">**Material de wireframe:** o material aplicado à malha wireframe.</span><span class="sxs-lookup"><span data-stu-id="8a783-209">**Wireframe material**: the material applied to the wireframe mesh.</span></span>
* <span data-ttu-id="8a783-210">**Raio de borda do wireframe:** a espessura do wireframe.</span><span class="sxs-lookup"><span data-stu-id="8a783-210">**Wireframe edge radius**: the thickness of the wireframe.</span></span>
* <span data-ttu-id="8a783-211">**Forma de wireframe:** a forma do wireframe pode ser cúbica ou cilíndrica.</span><span class="sxs-lookup"><span data-stu-id="8a783-211">**Wireframe shape**: shape of the wireframe can by either cubic or cylindrical.</span></span>
* <span data-ttu-id="8a783-212">**Mostrar wireframe:** controla a visibilidade do wireframe.</span><span class="sxs-lookup"><span data-stu-id="8a783-212">**Show wireframe**: controls visibility of the wireframe.</span></span>

### <a name="proximity-effect-configuration"></a><span data-ttu-id="8a783-213">Configuração do efeito de proximidade</span><span class="sxs-lookup"><span data-stu-id="8a783-213">Proximity effect configuration</span></span>

<span data-ttu-id="8a783-214">Mostrar e ocultar os alças com animação com base na distância até as mãos.</span><span class="sxs-lookup"><span data-stu-id="8a783-214">Show and hide the handles with animation based on the distance to the hands.</span></span> <span data-ttu-id="8a783-215">Ele tem animação de dimensionamento em duas etapas.</span><span class="sxs-lookup"><span data-stu-id="8a783-215">It has two-step scaling animation.</span></span> <span data-ttu-id="8a783-216">Os padrões são definidos como comportamento de estilo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8a783-216">Defaults are set to HoloLens 2 style behavior.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Proximity.png" alt="Bounds control Proximity">

* <span data-ttu-id="8a783-217">**Efeito de proximidade ativo:** habilitar a ativação de alça baseada em proximidade</span><span class="sxs-lookup"><span data-stu-id="8a783-217">**Proximity Effect Active**: Enable proximity-based handle activation</span></span>
* <span data-ttu-id="8a783-218">**Proximidade média do objeto:** distância para o dimensionamento da primeira etapa</span><span class="sxs-lookup"><span data-stu-id="8a783-218">**Object Medium Proximity**: Distance for the 1st step scaling</span></span>
* <span data-ttu-id="8a783-219">**Proximidade de fechamento do objeto:** distância para o dimensionamento da segunda etapa</span><span class="sxs-lookup"><span data-stu-id="8a783-219">**Object Close Proximity**: Distance for the 2nd step scaling</span></span>
* <span data-ttu-id="8a783-220">**Escala distante:** valor de escala padrão do ativo de alça quando as mãos estão fora do intervalo da interação de controle de limites (distância definida acima por "Tratar proximidade média".</span><span class="sxs-lookup"><span data-stu-id="8a783-220">**Far Scale**: Default scale value of the handle asset when the hands are out of range of the bounds control interaction (distance defined above by 'Handle Medium Proximity'.</span></span> <span data-ttu-id="8a783-221">Usar 0 para ocultar o handle por padrão)</span><span class="sxs-lookup"><span data-stu-id="8a783-221">Use 0 to hide handle by default)</span></span>
* <span data-ttu-id="8a783-222">**Escala média:** valor de escala do ativo de alça quando as mãos estão dentro do intervalo da interação de controle de limites (distância definida acima por "Lidar com proximidade próxima".</span><span class="sxs-lookup"><span data-stu-id="8a783-222">**Medium Scale**: Scale value of the handle asset when the hands are within range of the bounds control interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="8a783-223">Use 1 para mostrar o tamanho normal)</span><span class="sxs-lookup"><span data-stu-id="8a783-223">Use 1 to show normal size)</span></span>
* <span data-ttu-id="8a783-224">**Escala de Fechamento:** valor de escala do ativo de alça quando as mãos estão dentro do intervalo da interação de captura (distância definida acima por "Lidar com proximidade próxima".</span><span class="sxs-lookup"><span data-stu-id="8a783-224">**Close Scale**: Scale value of the handle asset when the hands are within range of the grab interaction (distance defined above by 'Handle Close Proximity'.</span></span> <span data-ttu-id="8a783-225">Usar 1.x para mostrar um tamanho maior)</span><span class="sxs-lookup"><span data-stu-id="8a783-225">Use 1.x to show bigger size)</span></span>
* <span data-ttu-id="8a783-226">**Taxa de crescimento distante:** a taxa de um objeto dimensionado por proximidade é dimensionada quando a mão se move de proximidade média para distante.</span><span class="sxs-lookup"><span data-stu-id="8a783-226">**Far Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to far proximity.</span></span>
* <span data-ttu-id="8a783-227">**Taxa média de crescimento:** a taxa de um objeto dimensionado por proximidade é dimensionada quando a mão se move da média para a proximidade próxima.</span><span class="sxs-lookup"><span data-stu-id="8a783-227">**Medium Grow Rate**: Rate a proximity scaled object scales when the hand moves from medium to close proximity.</span></span>
* <span data-ttu-id="8a783-228">**Fechar Taxa de Crescimento:** a taxa de um objeto dimensionado por proximidade é dimensionada quando a mão se move da proximidade ao centro do objeto.</span><span class="sxs-lookup"><span data-stu-id="8a783-228">**Close Grow Rate**: Rate a proximity scaled object scales when the hand moves from close proximity to object center.</span></span>

## <a name="constraint-system"></a><span data-ttu-id="8a783-229">Sistema de restrição</span><span class="sxs-lookup"><span data-stu-id="8a783-229">Constraint System</span></span>

<span data-ttu-id="8a783-230">O controle bounds dá suporte ao [uso](constraint-manager.md) do gerenciador de restrições para limitar ou modificar o comportamento de conversão, rotação ou dimensionamento ao usar alças de controle de limites.</span><span class="sxs-lookup"><span data-stu-id="8a783-230">Bounds control supports using the [constraint manager](constraint-manager.md) to limit or modify translation, rotation or scaling behavior while using bounds control handles.</span></span>

<span data-ttu-id="8a783-231">O inspetor de propriedade mostrará todos os gerenciadores de restrição disponíveis anexados ao mesmo objeto de jogo em uma lista suspenso com a opção de rolar e realçar o gerenciador de restrições selecionado.</span><span class="sxs-lookup"><span data-stu-id="8a783-231">The property inspector will show all available constraint managers attached to the same game object in a dropdown with an option to scroll and highlight the selected constraint manager.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Constraints.png" width="450" alt="Bounds control Constraints">

## <a name="events"></a><span data-ttu-id="8a783-232">Eventos</span><span class="sxs-lookup"><span data-stu-id="8a783-232">Events</span></span>

<span data-ttu-id="8a783-233">O controle bounds fornece os seguintes eventos.</span><span class="sxs-lookup"><span data-stu-id="8a783-233">Bounds control provides the following events.</span></span> <span data-ttu-id="8a783-234">Este exemplo usa esses eventos para reproduzir comentários de áudio.</span><span class="sxs-lookup"><span data-stu-id="8a783-234">This example uses these events to play audio feedback.</span></span>

* <span data-ttu-id="8a783-235">**Rotação Iniciada:** acionado quando a rotação é iniciada.</span><span class="sxs-lookup"><span data-stu-id="8a783-235">**Rotate Started**: Fired when rotation starts.</span></span>
* <span data-ttu-id="8a783-236">**Girar Parado:** acionado quando a rotação é interrompida.</span><span class="sxs-lookup"><span data-stu-id="8a783-236">**Rotate Stopped**: Fired when rotation stops.</span></span>
* <span data-ttu-id="8a783-237">**Escala iniciada:** é a incêndio quando o dimensionamento é iniciado.</span><span class="sxs-lookup"><span data-stu-id="8a783-237">**Scale Started**: Fires when scaling starts.</span></span>
* <span data-ttu-id="8a783-238">**Escala interrompida:** é a incêndio quando o dimensionamento é interrompido.</span><span class="sxs-lookup"><span data-stu-id="8a783-238">**Scale Stopped**: Fires when scaling stops.</span></span>
* <span data-ttu-id="8a783-239">**Translate Started:** acionará quando a conversão for iniciada.</span><span class="sxs-lookup"><span data-stu-id="8a783-239">**Translate Started**: Fires when translation starts.</span></span>
* <span data-ttu-id="8a783-240">**Translate Stopped:** acionará quando a conversão for interrompida.</span><span class="sxs-lookup"><span data-stu-id="8a783-240">**Translate Stopped**: Fires when translation stops.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Events.png" width="450" alt="Bounds control Events">

## <a name="elastics-experimental"></a><span data-ttu-id="8a783-241">Elástico (experimental)</span><span class="sxs-lookup"><span data-stu-id="8a783-241">Elastics (Experimental)</span></span>

<span data-ttu-id="8a783-242">Os elásticos podem ser usados ao manipular objetos por meio do controle de limites.</span><span class="sxs-lookup"><span data-stu-id="8a783-242">Elastics can be used when manipulating objects via bounds control.</span></span> <span data-ttu-id="8a783-243">Observe que o [sistema elástico ainda](../elastics/elastic-system.md) está em estado experimental.</span><span class="sxs-lookup"><span data-stu-id="8a783-243">Note that the [elastics system](../elastics/elastic-system.md) is still in experimental state.</span></span> <span data-ttu-id="8a783-244">Para habilitar o elástico, vincule um componente existente do Elastics Manager ou crie e vincule um novo gerenciador de elásticos por meio do `Add Elastics Manager` botão.</span><span class="sxs-lookup"><span data-stu-id="8a783-244">To enable elastics either link an existing elastics manager component or create and link a new elastics manager via the `Add Elastics Manager` button.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Elastics.png" width="450" alt="Bounds control Elastics">

## <a name="handle-styles"></a><span data-ttu-id="8a783-245">Manipular estilos</span><span class="sxs-lookup"><span data-stu-id="8a783-245">Handle styles</span></span>

<span data-ttu-id="8a783-246">Por padrão, quando você apenas atribuir o script, ele mostrará o handle do estilo de [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) 1ª geração do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="8a783-246">By default, when you just assign the [`BoundsControl.cs`](xref:Microsoft.MixedReality.Toolkit.UI.BoundsControl) script, it will show the handle of the HoloLens 1st gen style.</span></span> <span data-ttu-id="8a783-247">Para usar os alças de estilo do HoloLens 2, você precisa atribuir materiais e pré-requisitos de alça adequados.</span><span class="sxs-lookup"><span data-stu-id="8a783-247">To use HoloLens 2 style handles, you need to assign proper handle prefabs and materials.</span></span>

![Estilos de alça de controle de limites 2](../images/bounds-control/MRTK_BoundsControl_HandleStyles1.png)

<span data-ttu-id="8a783-249">Abaixo estão os pré-requisitos, os materiais e os valores de dimensionamento para os alças de controle de limites de estilo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8a783-249">Below are the prefabs, materials, and the scaling values for the HoloLens 2 style bounds control handles.</span></span> <span data-ttu-id="8a783-250">Você pode encontrar este exemplo na `BoundsControlExamples` cena.</span><span class="sxs-lookup"><span data-stu-id="8a783-250">You can find this example in the `BoundsControlExamples` scene.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_HandleStyles2.png" width="450" alt="Bounds control HandleStyles">

### <a name="handles-setup-for-hololens-2-style"></a><span data-ttu-id="8a783-251">Alças (configuração para o estilo do HoloLens 2)</span><span class="sxs-lookup"><span data-stu-id="8a783-251">Handles (Setup for HoloLens 2 style)</span></span>

* <span data-ttu-id="8a783-252">**Material do handle:** BoundingBoxHandleWhite.mat</span><span class="sxs-lookup"><span data-stu-id="8a783-252">**Handle Material**: BoundingBoxHandleWhite.mat</span></span>
* <span data-ttu-id="8a783-253">**Material de alça ressalvado:** BoundingBoxHandleBlueGrabbed.mat</span><span class="sxs-lookup"><span data-stu-id="8a783-253">**Handle Grabbed Material**: BoundingBoxHandleBlueGrabbed.mat</span></span>
* <span data-ttu-id="8a783-254">**Pré-fab de alça de escala:** MRTK_BoundingBox_ScaleHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="8a783-254">**Scale Handle Prefab**: MRTK_BoundingBox_ScaleHandle.prefab</span></span>
* <span data-ttu-id="8a783-255">**Pré-fab de Slate do Alça de** Escala: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span><span class="sxs-lookup"><span data-stu-id="8a783-255">**Scale Handle Slate Prefab**: MRTK_BoundingBox_ScaleHandle_Slate.prefab</span></span>
* <span data-ttu-id="8a783-256">**Tamanho do alça de** escala: 0,016 (1,6 cm)</span><span class="sxs-lookup"><span data-stu-id="8a783-256">**Scale Handle Size**: 0.016 (1.6cm)</span></span>
* <span data-ttu-id="8a783-257">**Preenchimento do Colisor de Alça** de Escala: 0,016 (torna o colisor acessível um pouco maior do que o visual de alça)</span><span class="sxs-lookup"><span data-stu-id="8a783-257">**Scale Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>
* <span data-ttu-id="8a783-258">**Pré-fab de alça de** rotação: MRTK_BoundingBox_RotateHandle.prefab</span><span class="sxs-lookup"><span data-stu-id="8a783-258">**Rotation Handle Prefab**: MRTK_BoundingBox_RotateHandle.prefab</span></span>
* <span data-ttu-id="8a783-259">**Tamanho do alça de** rotação: 0,016</span><span class="sxs-lookup"><span data-stu-id="8a783-259">**Rotation Handle Size**: 0.016</span></span>
* <span data-ttu-id="8a783-260">**Preenchimento do Colisor de** Alça de Rotação : 0,016 (torna o colisor acessível um pouco maior do que o visual de alça)</span><span class="sxs-lookup"><span data-stu-id="8a783-260">**Rotation Handle Collider Padding**: 0.016 (makes the grabbable collider slightly bigger than handle visual)</span></span>

## <a name="transformation-changes-with-object-manipulator"></a><span data-ttu-id="8a783-261">Alterações de transformação com o manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="8a783-261">Transformation changes with object manipulator</span></span>

<span data-ttu-id="8a783-262">Um controle de limites pode ser usado em combinação com [`ObjectManipulator.cs`](object-manipulator.md) para permitir determinados tipos de manipulação (por exemplo,</span><span class="sxs-lookup"><span data-stu-id="8a783-262">A bounds control can be used in combination with [`ObjectManipulator.cs`](object-manipulator.md) to allow for certain types of manipulation (eg.</span></span> <span data-ttu-id="8a783-263">movendo o objeto ) sem usar identificador.</span><span class="sxs-lookup"><span data-stu-id="8a783-263">moving the object) without using handles.</span></span> <span data-ttu-id="8a783-264">O manipulador de manipulação dá suporte a interações de uma e duas mãos.</span><span class="sxs-lookup"><span data-stu-id="8a783-264">The manipulation handler supports both one and two-handed interactions.</span></span> <span data-ttu-id="8a783-265">[O acompanhamento](../input/hand-tracking.md) de mão pode ser usado para interagir com um objeto de perto.</span><span class="sxs-lookup"><span data-stu-id="8a783-265">[Hand tracking](../input/hand-tracking.md) can be used to interact with an object up close.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_ObjectManipulator.png" width="450" alt="Bounds control Object Manipulator">

<span data-ttu-id="8a783-266">Para que as bordas de controle de limites se comportem da mesma maneira ao movimentação usando a interação distante de , é aconselhável conectar seus eventos para On Manipulation Started On Manipulation Ended to respectivamente, conforme mostrado na captura de tela [`ObjectManipulator`](object-manipulator.md)   /   `BoundsControl.HighlightWires`  /  `BoundsControl.UnhighlightWires` acima.</span><span class="sxs-lookup"><span data-stu-id="8a783-266">In order for the bounds control edges to behave the same way when moving it using [`ObjectManipulator`](object-manipulator.md)'s far interaction, it is advised to connect its events for *On Manipulation Started* / *On Manipulation Ended* to `BoundsControl.HighlightWires` / `BoundsControl.UnhighlightWires` respectively, as shown in the screenshot above.</span></span>

## <a name="how-to-add-and-configure-a-bounds-control-using-unity-inspector"></a><span data-ttu-id="8a783-267">Como adicionar e configurar um controle de limites usando o Inspetor do Unity</span><span class="sxs-lookup"><span data-stu-id="8a783-267">How to add and configure a bounds control using Unity Inspector</span></span>

1. <span data-ttu-id="8a783-268">Adicionar Colisor de Caixa a um objeto</span><span class="sxs-lookup"><span data-stu-id="8a783-268">Add Box Collider to an object</span></span>
2. <span data-ttu-id="8a783-269">Atribuir `BoundsControl` script a um objeto</span><span class="sxs-lookup"><span data-stu-id="8a783-269">Assign `BoundsControl` script to an object</span></span>
3. <span data-ttu-id="8a783-270">Configurar opções, como métodos de 'Ativação' (consulte [a seção Propriedades do](#inspector-properties) inspetor abaixo)</span><span class="sxs-lookup"><span data-stu-id="8a783-270">Configure options, such as 'Activation' methods (see [Inspector properties](#inspector-properties) section below)</span></span>
4. <span data-ttu-id="8a783-271">(Opcional) Atribuir pré-requisitos e materiais para um controle de limites de estilo do HoloLens 2 (consulte a [seção Manipular estilos](#handle-styles) abaixo)</span><span class="sxs-lookup"><span data-stu-id="8a783-271">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control (see [Handle styles](#handle-styles) section below)</span></span>

> [!NOTE]
> <span data-ttu-id="8a783-272">Use *o campo Objeto de* Destino e Substituição de Limites no inspetor para atribuir um objeto e *colisor* específicos no objeto com vários componentes filho.</span><span class="sxs-lookup"><span data-stu-id="8a783-272">Use *Target Object* and *Bounds Override* field in the inspector to assign specific object and collider in the object with multiple child components.</span></span>

![Controle de limites](../images/bounds-control/MRTK_BoundsControl_Assign.png)

## <a name="how-to-add-and-configure-a-bounds-control-in-the-code"></a><span data-ttu-id="8a783-274">Como adicionar e configurar um controle de limites no código</span><span class="sxs-lookup"><span data-stu-id="8a783-274">How to add and configure a bounds control in the code</span></span>

1. <span data-ttu-id="8a783-275">Insinuar gameObject de cubo</span><span class="sxs-lookup"><span data-stu-id="8a783-275">Instantiate cube GameObject</span></span>

    ```c#
    GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
    ```

1. <span data-ttu-id="8a783-276">Atribuir `BoundsControl` script a um objeto com colisor usando AddComponent<>()</span><span class="sxs-lookup"><span data-stu-id="8a783-276">Assign `BoundsControl` script to an object with collider, using AddComponent<>()</span></span>

    ```c#
    private BoundsControl boundsControl;
    boundsControl = cube.AddComponent<BoundsControl>();
    ```

1. <span data-ttu-id="8a783-277">Configure opções diretamente no controle ou por meio de uma das configurações de script (consulte a seção [Propriedades e](#inspector-properties) [configurações](#configuration-objects) do inspetor abaixo)</span><span class="sxs-lookup"><span data-stu-id="8a783-277">Configure options either directly on the control or via one of the scriptable configurations (see [Inspector properties](#inspector-properties) and [Configurations](#configuration-objects) section below)</span></span>

    ```c#
    // Change activation method
    boundsControl.BoundsControlActivation = BoundsControlActivationType.ActivateByProximityAndPointer;
    // Make the scale handles large
    boundsControl.ScaleHandlesConfig.HandleSize = 0.1f;
    // Hide rotation handles for x axis
    boundsControl.RotationHandlesConfig.ShowRotationHandleForX = false;
    ```

1. <span data-ttu-id="8a783-278">(Opcional) Atribua pré-requisitos e materiais para um controle de limites de estilo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8a783-278">(Optional) Assign prefabs and materials for a HoloLens 2 style bounds control.</span></span> <span data-ttu-id="8a783-279">Isso ainda requer atribuições por meio do inspetor, pois os materiais e os pré-requisitos devem ser carregados dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="8a783-279">This still requires assignments through the inspector since the materials and prefabs should be dynamically loaded.</span></span>

> [!NOTE]
> <span data-ttu-id="8a783-280">Não é recomendável usar a pasta 'Recursos' do Unity ou o [Sombreador.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) para carregar dinamicamente sombreadores, pois as permutações do sombreador podem estar ausentes em runtime.</span><span class="sxs-lookup"><span data-stu-id="8a783-280">Using Unity's 'Resources' folder or [Shader.Find]( https://docs.unity3d.com/ScriptReference/Shader.Find.html) for dynamically loading shaders is not recommended since shader permutations may be missing at runtime.</span></span>

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

### <a name="example-set-minimum-maximum-bounds-control-scale-using-minmaxscaleconstraint"></a><span data-ttu-id="8a783-281">Exemplo: definir a escala de controle de limites mínimo e máximo usando MinMaxScaleConstraint</span><span class="sxs-lookup"><span data-stu-id="8a783-281">Example: Set minimum, maximum bounds control scale using MinMaxScaleConstraint</span></span>

<span data-ttu-id="8a783-282">Para definir a escala mínima e máxima, anexe um [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) ao seu controle.</span><span class="sxs-lookup"><span data-stu-id="8a783-282">To set the minimum and maximum scale, attach a [`MinMaxScaleConstraint`](xref:Microsoft.MixedReality.Toolkit.UI.MinMaxScaleConstraint) to your control.</span></span> <span data-ttu-id="8a783-283">À medida que o controle de limites anexar e ativar automaticamente o gerenciador de restrições, MinMaxScaleConstraint será aplicado automaticamente às alterações de transformação depois que ele for anexado e configurado.</span><span class="sxs-lookup"><span data-stu-id="8a783-283">As bounds control automatically attaches and activates constraint manager the MinMaxScaleConstraint will be automatically applied to the transformation changes once it's attached and configured.</span></span>

<span data-ttu-id="8a783-284">Você também pode usar MinMaxScaleConstraint para definir a escala mínima e máxima para [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator) .</span><span class="sxs-lookup"><span data-stu-id="8a783-284">You can also use MinMaxScaleConstraint to set minimum and maximum scale for [`ObjectManipulator`](xref:Microsoft.MixedReality.Toolkit.UI.ObjectManipulator).</span></span>

```c#
GameObject cube = GameObject.CreatePrimitive(PrimitiveType.Cube);
bcontrol = cube.AddComponent<BoundsControl>();
// Important: BoundsControl creates a constraint manager on start if one does not exist.
// There's no need to manually attach a constraint manager.
MinMaxScaleConstraint scaleConstraint = bcontrol.gameObject.AddComponent<MinMaxScaleConstraint>();
scaleConstraint.ScaleMinimum = 1f;
scaleConstraint.ScaleMaximum = 2f;
```

## <a name="example-add-bounds-control-around-a-game-object"></a><span data-ttu-id="8a783-285">Exemplo: Adicionar controle de limites em torno de um objeto de jogo</span><span class="sxs-lookup"><span data-stu-id="8a783-285">Example: Add bounds control around a game object</span></span>

<span data-ttu-id="8a783-286">Para adicionar um controle de limites em torno de um objeto, basta adicionar um `BoundsControl` componente a ele:</span><span class="sxs-lookup"><span data-stu-id="8a783-286">To add a bounds control around an object, simply add a `BoundsControl` component to it:</span></span>

```c#
private void PutABoundsControlAroundIt(GameObject target)
{
   target.AddComponent<BoundsControl>();
}
```

## <a name="migrating-from-bounding-box"></a><span data-ttu-id="8a783-287">Migrando da caixa delimitada</span><span class="sxs-lookup"><span data-stu-id="8a783-287">Migrating from Bounding Box</span></span>

<span data-ttu-id="8a783-288">Os pré-requisitos e [](bounding-box.md) instâncias existentes que usam a caixa delimitatória podem ser atualizados para o novo controle de limites por meio da janela de migração, que faz parte do pacote de ferramentas do MRTK. [](../tools/migration-window.md)</span><span class="sxs-lookup"><span data-stu-id="8a783-288">Existing prefabs and instances using [bounding box](bounding-box.md) can be upgraded to the new bounds control via the [migration window](../tools/migration-window.md) which is part of the MRTK tools package.</span></span>

<span data-ttu-id="8a783-289">Para atualizar instâncias individuais da caixa delimitador, também há uma opção de migração dentro do inspetor de propriedade do componente.</span><span class="sxs-lookup"><span data-stu-id="8a783-289">For upgrading individual instances of bounding box there's also an a migration option inside the property inspector of the component.</span></span>

<img src="../images/bounds-control/MRTK_BoundsControl_Migrate.png" width="450" alt="Bounds control Migrate">

## <a name="see-also"></a><span data-ttu-id="8a783-290">Confira também</span><span class="sxs-lookup"><span data-stu-id="8a783-290">See also</span></span>

* [<span data-ttu-id="8a783-291">Manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="8a783-291">Object manipulator</span></span>](object-manipulator.md)
* [<span data-ttu-id="8a783-292">Gerenciador de restrições</span><span class="sxs-lookup"><span data-stu-id="8a783-292">Constraint manager</span></span>](constraint-manager.md)
* [<span data-ttu-id="8a783-293">Janela de migração</span><span class="sxs-lookup"><span data-stu-id="8a783-293">Migration window</span></span>](../tools/migration-window.md)
* [<span data-ttu-id="8a783-294">Sistema elástico (Experimental)</span><span class="sxs-lookup"><span data-stu-id="8a783-294">Elastics system (Experimental)</span></span>](../elastics/elastic-system.md)
