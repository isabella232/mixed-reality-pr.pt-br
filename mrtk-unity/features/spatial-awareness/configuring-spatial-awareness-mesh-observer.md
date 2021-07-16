---
title: Configurando os observadores de malha para o dispositivo
description: Como configurar o observador de malha espacial pronta no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: aba49e88d4fc555a88fe42e4b09858f1d2453ddc
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114281931"
---
# <a name="configuring-mesh-observers-for-device"></a><span data-ttu-id="6e1bf-104">Configurando os observadores de malha para o dispositivo</span><span class="sxs-lookup"><span data-stu-id="6e1bf-104">Configuring mesh observers for device</span></span>

<span data-ttu-id="6e1bf-105">este guia explicará como configurar o observador de malha espacial pronta no MRTK, que dá suporte à plataforma de Windows Mixed Reality (ou seja,</span><span class="sxs-lookup"><span data-stu-id="6e1bf-105">This guide will walk through configuring the out-of-box Spatial Mesh Observer in MRTK which supports the Windows Mixed Reality platform (i.e</span></span> <span data-ttu-id="6e1bf-106">HoloLens).</span><span class="sxs-lookup"><span data-stu-id="6e1bf-106">HoloLens).</span></span> <span data-ttu-id="6e1bf-107">a implementação padrão fornecida pela realidade misturada Toolkit é a classe [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) .</span><span class="sxs-lookup"><span data-stu-id="6e1bf-107">The default implementation provided by the Mixed Reality Toolkit is the [WindowsMixedRealitySpatialMeshObserver](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.SpatialAwareness.WindowsMixedRealitySpatialMeshObserver) class.</span></span> <span data-ttu-id="6e1bf-108">Muitas das propriedades neste artigo se aplicam a outras [implementações personalizadas do observador](create-data-provider.md).</span><span class="sxs-lookup"><span data-stu-id="6e1bf-108">Many of the properties in this article though apply for other [custom Observer implementations](create-data-provider.md).</span></span>

## <a name="profile-settings"></a><span data-ttu-id="6e1bf-109">Configurações de perfil</span><span class="sxs-lookup"><span data-stu-id="6e1bf-109">Profile settings</span></span>

<span data-ttu-id="6e1bf-110">Os dois itens a seguir devem ser definidos primeiro ao configurar um perfil de observador de malha espacial para o [sistema de conscientização espacial](spatial-awareness-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="6e1bf-110">The following two items must be defined first when configuring a Spatial Mesh Observer profile for the [Spatial Awareness system](spatial-awareness-getting-started.md).</span></span>

1. <span data-ttu-id="6e1bf-111">A implementação do tipo de observador concreto</span><span class="sxs-lookup"><span data-stu-id="6e1bf-111">The concrete observer type implementation</span></span>
1. <span data-ttu-id="6e1bf-112">lista de plataforma (s) com suporte para executar este observador</span><span class="sxs-lookup"><span data-stu-id="6e1bf-112">list of supported platform(s) to run this observer</span></span>

> [!NOTE]
> <span data-ttu-id="6e1bf-113">Todos os observadores devem estender a interface [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) .</span><span class="sxs-lookup"><span data-stu-id="6e1bf-113">All observers must extend the [IMixedRealitySpatialAwarenessObserver](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver) interface.</span></span>

![observador de malha geral Configurações tipos de plataforma](../images/spatial-awareness/SpatialAwarenessMeshObserverProfile_TypesPlatforms.png)

### <a name="general-settings"></a><span data-ttu-id="6e1bf-115">Configurações gerais</span><span class="sxs-lookup"><span data-stu-id="6e1bf-115">General settings</span></span>

![observador de malha geral Configurações configurações de Genral](../images/spatial-awareness/MeshObserverGeneralSettings.png)

<span data-ttu-id="6e1bf-117">**Comportamento de inicialização**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-117">**Startup Behavior**</span></span>

<span data-ttu-id="6e1bf-118">O comportamento de inicialização especifica se o observador começará a ser executado quando a primeira instância for criada.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-118">The startup behavior specifies whether the observer will begin running when first instantiated.</span></span> <span data-ttu-id="6e1bf-119">As duas opções são:</span><span class="sxs-lookup"><span data-stu-id="6e1bf-119">The two options are:</span></span>

* <span data-ttu-id="6e1bf-120">*Início automático* -o valor padrão no qual o observador iniciará a operação após a inicialização</span><span class="sxs-lookup"><span data-stu-id="6e1bf-120">*Auto Start* - The default value whereby the observer will begin operation after initialization</span></span>
* <span data-ttu-id="6e1bf-121">*Início manual* -o observador aguardará para ser direcionado para o início</span><span class="sxs-lookup"><span data-stu-id="6e1bf-121">*Manual Start* - The Observer will wait to be directed to start</span></span>

<span data-ttu-id="6e1bf-122">Se estiver usando o *início manual, será* necessário [retomá-los e suspendê-los em tempo de execução por meio de código](usage-guide.md#starting-and-stopping-mesh-observation).</span><span class="sxs-lookup"><span data-stu-id="6e1bf-122">If using *Manual Start*, one must [resume and suspend them at runtime via code](usage-guide.md#starting-and-stopping-mesh-observation).</span></span>

<span data-ttu-id="6e1bf-123">**Intervalo de atualização**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-123">**Update Interval**</span></span>

<span data-ttu-id="6e1bf-124">O tempo, em segundos, entre as solicitações para a plataforma para atualizar dados de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-124">The time, in seconds, between requests to the platform to update spatial mesh data.</span></span> <span data-ttu-id="6e1bf-125">Os valores típicos se enquadram no intervalo de 0,1 a 5,0 segundos.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-125">Typical values fall in the range of 0.1 and 5.0 seconds.</span></span>

<span data-ttu-id="6e1bf-126">**É observador estacionário**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-126">**Is Stationary Observer**</span></span>

<span data-ttu-id="6e1bf-127">Indica se o observador deve ou não ser estacionário ou movido e atualizado com o usuário.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-127">Indicates whether or not the observer is to remain stationary or to move and update with the user.</span></span> <span data-ttu-id="6e1bf-128">Se for true, a *forma de observador* com volume definido por *extensões de observação* permanecerá na origem na inicialização.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-128">If true, the *Observer Shape* with volume defined by *Observation Extents* will remain at the origin on startup.</span></span> <span data-ttu-id="6e1bf-129">Se for false, o espaço do observador seguirá o cabeçalho do usuário como a origem da forma.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-129">If false, the Observer space will follow the user's head as the shape's origin.</span></span>

<span data-ttu-id="6e1bf-130">Não haverá dados de malha calculados para qualquer área física fora do espaço do observador, conforme definido por essas propriedades: *é observador estacionário*, \* forma do observador \* \* e *extensões de observação*.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-130">There will be no mesh data calculated for any physical area outside of the Observer space as defined by these properties: *Is Stationary Observer*, \*Observer Shape\*\*, and *Observation Extents*.</span></span>

<span data-ttu-id="6e1bf-131">**Forma do observador**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-131">**Observer Shape**</span></span>

<span data-ttu-id="6e1bf-132">A forma do observador define o tipo de volume que o observador de malha usará ao observar as malhas.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-132">The observer shape defines the type of volume that the mesh observer will use when observing meshes.</span></span> <span data-ttu-id="6e1bf-133">As opções com suporte são:</span><span class="sxs-lookup"><span data-stu-id="6e1bf-133">The supported options are:</span></span>

* <span data-ttu-id="6e1bf-134">*Cubo alinhado ao eixo* – forma retangular que permanece alinhada com os eixos do sistema mundial de coordenadas, conforme determinado na inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-134">*Axis Aligned Cube* - Rectangular shape that stays aligned with the axes of the world coordinate system, as determined at application startup.</span></span>
* <span data-ttu-id="6e1bf-135">*Cubo alinhado ao usuário* – forma retangular que gira para alinhar com o sistema de coordenadas local dos usuários.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-135">*User Aligned Cube* - Rectangular shape that rotates to align with the users local coordinate system.</span></span>
* <span data-ttu-id="6e1bf-136">*Esfera* -um volume esférico com um centro na origem do espaço mundial.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-136">*Sphere* - A spherical volume with a center at the world space origin.</span></span> <span data-ttu-id="6e1bf-137">O valor X da propriedade de *extensões de observação* será usado como o raio da esfera.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-137">The X value of the *Observation Extents* property will be used as the radius of the sphere.</span></span>

<span data-ttu-id="6e1bf-138">**Extensões de observação**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-138">**Observation Extents**</span></span>

<span data-ttu-id="6e1bf-139">As extensões de observação definem a distância do ponto de observação que as malhas serão observadas.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-139">The observation extents define the distance from the observation point that meshes will be observed.</span></span>

### <a name="physics-settings"></a><span data-ttu-id="6e1bf-140">Configurações de física</span><span class="sxs-lookup"><span data-stu-id="6e1bf-140">Physics settings</span></span>

![Configurações física do observador de malha](../images/spatial-awareness/MeshObserverPhysicsSettings.png)

<span data-ttu-id="6e1bf-142">**Camada física**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-142">**Physics Layer**</span></span>

<span data-ttu-id="6e1bf-143">A camada física na qual os objetos de malha espacial serão colocados para interagir com os sistemas física e RayCast do Unity.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-143">The physics layer on which spatial mesh objects will be placed in order to interact with the Unity Physics and RayCast systems.</span></span>

> [!NOTE]
> <span data-ttu-id="6e1bf-144">a realidade misturada Toolkit reserva a *camada 31* por padrão para uso por observadores de conscientização espacial.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-144">The Mixed Reality Toolkit reserves *layer 31* by default for use by Spatial Awareness observers.</span></span>

<span data-ttu-id="6e1bf-145">**Recalcular Normals**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-145">**Recalculate Normals**</span></span>

<span data-ttu-id="6e1bf-146">Especifica se o observador de malha recalculará os Normals da malha após a observação.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-146">Specifies whether or not the mesh observer will recalculate the normals of the mesh following observation.</span></span> <span data-ttu-id="6e1bf-147">Essa configuração está disponível para garantir que os aplicativos recebam malhas que contêm dados normais válidos em plataformas que não as retornam com malhas.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-147">This setting is available to ensure applications receive meshes that contain valid normals data on platforms that do not return them with meshes.</span></span>

### <a name="level-of-detail-settings"></a><span data-ttu-id="6e1bf-148">Nível de configurações de detalhes</span><span class="sxs-lookup"><span data-stu-id="6e1bf-148">Level of detail settings</span></span>

![nível de detalhe do observador de malha Configurações](../images/spatial-awareness/MeshObserverLevelOfDetailSettings.png)

<span data-ttu-id="6e1bf-150">**Nível de detalhe**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-150">**Level of Detail**</span></span>

<span data-ttu-id="6e1bf-151">Especifica o nível de detalhe (LOD) dos dados de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-151">Specifies the level of detail (LOD) of the spatial mesh data.</span></span> <span data-ttu-id="6e1bf-152">Os valores definidos no momento são grande, bem e personalizados.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-152">Currently defined values are Coarse, Fine and Custom.</span></span>

* <span data-ttu-id="6e1bf-153">Em *grande* lugar, um impacto menor no desempenho do aplicativo e é uma excelente opção para a localização de navegação/plano.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-153">*Coarse* - Places a smaller impact on application performance and is an excellent choice for navigation/plane finding.</span></span>

* <span data-ttu-id="6e1bf-154">A configuração com balanceamento *médio* geralmente é útil para experiências que verificam continuamente o ambiente em busca de recursos grandes, andares e paredes, bem como detalhes de oclusão.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-154">*Medium* - Balanced setting often useful for experiences that continually scan the environment for both large features, floors and walls, as well as occlusion details.</span></span>

* <span data-ttu-id="6e1bf-155">*Normalmente,* isso é exatamente um impacto maior no desempenho do aplicativo e é uma ótima opção para as malhas de oclusão.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-155">*Fine* - Generally exacts a higher impact on application performance and is a great option for occlusion meshes.</span></span>

* <span data-ttu-id="6e1bf-156">*Personalizado* – exige que o aplicativo especifique a propriedade de *medidor de triângulos/cúbico* e permite que os aplicativos ajustem a precisão versus o impacto no desempenho do observador de malha espacial.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-156">*Custom* - Requires the application to specify the *Triangles / Cubic Meter* property and allows applications to tune the accuracy vs. performance impact of the spatial mesh observer.</span></span>

> [!NOTE]
> <span data-ttu-id="6e1bf-157">Não há garantia de que todos os valores de *medidor de triângulos/cúbicos* sejam respeitados por todas as plataformas.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-157">It is not guaranteed that all *Triangles/Cubic Meter* values are honored by all platforms.</span></span> <span data-ttu-id="6e1bf-158">A experimentação e a criação de perfil são altamente recomendadas ao usar um LOD personalizado.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-158">Experimentation and profiling is highly recommended when using a custom LOD.</span></span>

<span data-ttu-id="6e1bf-159">**Triângulos por medidor cúbico**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-159">**Triangles per Cubic Meter**</span></span>

<span data-ttu-id="6e1bf-160">Válido ao usar a configuração *personalizada* para o **nível de propriedade de detalhe** e especifica a densidade de triângulo para a malha espacial.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-160">Valid when using the *Custom* setting for the **Level of Detail** property and specifies the triangle density for the spatial mesh.</span></span>

### <a name="display-settings"></a><span data-ttu-id="6e1bf-161">Configurações de vídeo</span><span class="sxs-lookup"><span data-stu-id="6e1bf-161">Display settings</span></span>

![Configurações de exibição de observador de malha](../images/spatial-awareness/MeshObserverDisplaySettings.png)

<span data-ttu-id="6e1bf-163">**Opção de exibição**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-163">**Display Option**</span></span>

<span data-ttu-id="6e1bf-164">Especifica como as malhas espaciais devem ser exibidas pelo observador.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-164">Specifies how spatial meshes are to be displayed by the observer.</span></span> <span data-ttu-id="6e1bf-165">Os valores com suporte são:</span><span class="sxs-lookup"><span data-stu-id="6e1bf-165">Supported values are:</span></span>

* <span data-ttu-id="6e1bf-166">*Nenhum* -o observador não renderizará a malha</span><span class="sxs-lookup"><span data-stu-id="6e1bf-166">*None* - Observer will not render the mesh</span></span>
* <span data-ttu-id="6e1bf-167">*Visível* -os dados de malha ficarão visíveis usando o *material visível*</span><span class="sxs-lookup"><span data-stu-id="6e1bf-167">*Visible* - Mesh data will be visible using the *Visible Material*</span></span>
* <span data-ttu-id="6e1bf-168">*Oclusão* -os dados de malha serão occlude itens em cena usando o *material de oclusão*</span><span class="sxs-lookup"><span data-stu-id="6e1bf-168">*Occlusion* - Mesh data will be occlude items in scene using the *Occlusion Material*</span></span>

![Selecione a implementação do sistema de conscientização espacial](../images/spatial-awareness/MRTK_SpatialAwareness_DisplayOptions.jpg)

<span data-ttu-id="6e1bf-170">Os observadores espaciais podem ser [retomados/suspensos em tempo de execução por meio de código.](usage-guide.md#starting-and-stopping-mesh-observation)</span><span class="sxs-lookup"><span data-stu-id="6e1bf-170">Spatial Observers can be [resumed/suspended at runtime via code.](usage-guide.md#starting-and-stopping-mesh-observation)</span></span>

> [!WARNING]
> <span data-ttu-id="6e1bf-171">A configuração da *opção de exibição* para *nenhum* **não interrompe a** execução do observador.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-171">Setting *Display Option* to *None* does **NOT** stop the observer from running.</span></span> <span data-ttu-id="6e1bf-172">Se você quiser interromper todos os observadores, os aplicativos precisarão suspender todos os observadores por meio de [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span><span class="sxs-lookup"><span data-stu-id="6e1bf-172">If you wish to stop all observers, applications will need to suspend all observers via [`CoreServices.SpatialAwareness.SuspendObservers()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessSystem.SuspendObservers)</span></span>

<span data-ttu-id="6e1bf-173">**Material visível**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-173">**Visible Material**</span></span>

<span data-ttu-id="6e1bf-174">Indica o material a ser usado ao visualizar a malha espacial.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-174">Indicates the material to be used when visualizing the spatial mesh.</span></span>

<span data-ttu-id="6e1bf-175">**Material de oclusão**</span><span class="sxs-lookup"><span data-stu-id="6e1bf-175">**Occlusion Material**</span></span>

<span data-ttu-id="6e1bf-176">Indica o material a ser usado para fazer com que a malha espacial occlude hologramas.</span><span class="sxs-lookup"><span data-stu-id="6e1bf-176">Indicates the material to be used to cause the spatial mesh to occlude holograms.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e1bf-177">Confira também</span><span class="sxs-lookup"><span data-stu-id="6e1bf-177">See also</span></span>

* [<span data-ttu-id="6e1bf-178">Sistema de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="6e1bf-178">Spatial Awareness System</span></span>](spatial-awareness-getting-started.md)
* [<span data-ttu-id="6e1bf-179">Configurando o sistema de reconhecimento espacial por meio de código</span><span class="sxs-lookup"><span data-stu-id="6e1bf-179">Configuring Spatial Awareness system via Code</span></span>](usage-guide.md)
* [<span data-ttu-id="6e1bf-180">Documentação da API do IMixedRealitySpatialAwarenessObserver</span><span class="sxs-lookup"><span data-stu-id="6e1bf-180">IMixedRealitySpatialAwarenessObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver)
* [<span data-ttu-id="6e1bf-181">Documentação da API do IMixedRealitySpatialAwarenessMeshObserver</span><span class="sxs-lookup"><span data-stu-id="6e1bf-181">IMixedRealitySpatialAwarenessMeshObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessMeshObserver)
* [<span data-ttu-id="6e1bf-182">Documentação da API do BaseSpatialObserver</span><span class="sxs-lookup"><span data-stu-id="6e1bf-182">BaseSpatialObserver API documentation</span></span>](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.BaseSpatialObserver)
