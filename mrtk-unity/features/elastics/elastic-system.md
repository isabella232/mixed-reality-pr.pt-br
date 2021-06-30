---
title: Sistema elástico
description: Documentação relacionada à simulação de elástico no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, ElasticsSystem,
ms.openlocfilehash: 1f90864ee6d3b6756b863de600ade8423a44cacc
ms.sourcegitcommit: 8b4c2b1aac83bc8adf46acfd92b564f899ef7735
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/30/2021
ms.locfileid: "113121234"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="50779-104">Sistema elástico (experimental)</span><span class="sxs-lookup"><span data-stu-id="50779-104">Elastic system (experimental)</span></span>

![Sistema elástico](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="50779-106">O MRTK vem com um sistema de simulação elástica que inclui uma ampla variedade de subclasses extensíveis e flexíveis, oferecendo vinculações para o quaternão 4dimensional, o 3º volume e sistemas simples de fonte linear.</span><span class="sxs-lookup"><span data-stu-id="50779-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="50779-107">Atualmente, os seguintes componentes do MRTK que suportam [o gerenciador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) podem aproveitar a funcionalidade de elástico:</span><span class="sxs-lookup"><span data-stu-id="50779-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="50779-108">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="50779-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="50779-109">Manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="50779-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="50779-110">Gerenciador de elásticos</span><span class="sxs-lookup"><span data-stu-id="50779-110">Elastics manager</span></span>

![Sistema Elástico2](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="50779-112">Os processos do gerenciador de elásticos passados são transformadas e os alimenta no sistema elástico.</span><span class="sxs-lookup"><span data-stu-id="50779-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="50779-113">A habilitação de elásticos para componentes personalizados pode ser alcançada por duas etapas:</span><span class="sxs-lookup"><span data-stu-id="50779-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="50779-114">Chamando o método Initialize no início da manipulação, atualizando o sistema com a transformação de host atual.</span><span class="sxs-lookup"><span data-stu-id="50779-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="50779-115">Consultando ApplyHostTransform sempre que um cálculo elástico deve ser executado na transformação de destino atualizada.</span><span class="sxs-lookup"><span data-stu-id="50779-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="50779-116">Observe que os elásticos continuarão a simular depois que a manipulação terminar (por meio do loop de atualização do gerenciador elástico).</span><span class="sxs-lookup"><span data-stu-id="50779-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="50779-117">Para bloquear o comportamento, a atualização automática de elástico [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) pode ser definida como false.</span><span class="sxs-lookup"><span data-stu-id="50779-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="50779-118">Por padrão, o componente do gerenciador de elásticos, quando adicionado a um objeto de jogo, não terá elásticos habilitados para nenhum tipo de transformação.</span><span class="sxs-lookup"><span data-stu-id="50779-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="50779-119">O campo precisa ser habilitado para tipos de transformação específicos para criar a configuração e as extensão de `Manipulation types using elastic feedback` elásticos para o tipo selecionado.</span><span class="sxs-lookup"><span data-stu-id="50779-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="50779-120">Configurações do Elastics</span><span class="sxs-lookup"><span data-stu-id="50779-120">Elastics configurations</span></span>

<span data-ttu-id="50779-121">Semelhante às configurações de controle de limites, o gerenciador elástico vem com um conjunto de objetos de configuração que podem ser armazenados como objetos que podem ser scripts e [compartilhados](../ux-building-blocks/bounds-control.md#configuration-objects)entre diferentes instâncias ou pré-fabs.</span><span class="sxs-lookup"><span data-stu-id="50779-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="50779-122">As configurações podem ser compartilhadas e vinculadas como arquivos de ativos individuais com script ou ativos aninhados que podem ser script dentro de pré-requisitos.</span><span class="sxs-lookup"><span data-stu-id="50779-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="50779-123">Outras configurações também podem ser definidas diretamente na instância sem vincular a um ativo externo ou aninhado que pode ser script.</span><span class="sxs-lookup"><span data-stu-id="50779-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="50779-124">O inspetor do gerenciador de elásticos indicará se uma configuração é compartilhada ou emlinada como parte da instância atual mostrando uma mensagem no inspetor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="50779-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="50779-125">Além disso, as instâncias compartilhadas não serão editáveis diretamente na própria janela de propriedades do gerenciador de elásticos, mas, em vez disso, o ativo ao que está vinculando precisa ser diretamente modfiado para evitar alterações acidentais em configurações compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="50779-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="50779-126">O Elastics Manager oferece opções de objetos de configuração para os seguintes tipos de transformação, cada um deles representado por [um objeto de configuração elástica](#elastic-configuration-object):</span><span class="sxs-lookup"><span data-stu-id="50779-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="50779-127">Tradução elástica</span><span class="sxs-lookup"><span data-stu-id="50779-127">Translation Elastic</span></span>
- <span data-ttu-id="50779-128">Rotação elástica</span><span class="sxs-lookup"><span data-stu-id="50779-128">Rotation Elastic</span></span>
- <span data-ttu-id="50779-129">Dimensionar Elástico</span><span class="sxs-lookup"><span data-stu-id="50779-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="50779-130">Objeto de configuração elástica</span><span class="sxs-lookup"><span data-stu-id="50779-130">Elastic configuration object</span></span>

<span data-ttu-id="50779-131">Uma configuração elástica define as propriedades de um sistema diferencial de oscilador insuceso escuros.</span><span class="sxs-lookup"><span data-stu-id="50779-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="50779-132">As propriedades a seguir podem ser ajustadas, mas já vêm com um conjunto de padrões no MRTK:</span><span class="sxs-lookup"><span data-stu-id="50779-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="50779-133">**Massa:** massa do elemento de oscilador simulado.</span><span class="sxs-lookup"><span data-stu-id="50779-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="50779-134">**HandK:** constante de spring da mão.</span><span class="sxs-lookup"><span data-stu-id="50779-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="50779-135">**EndK:** constante spring end cap.</span><span class="sxs-lookup"><span data-stu-id="50779-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="50779-136">**SnapK:** constante spring do ponto de encaixe.</span><span class="sxs-lookup"><span data-stu-id="50779-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="50779-137">**Arraste**: fator de arrastar/damper, proporcional à velocidade.</span><span class="sxs-lookup"><span data-stu-id="50779-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="50779-138">Extensão elástica</span><span class="sxs-lookup"><span data-stu-id="50779-138">Elastics extents</span></span>

<span data-ttu-id="50779-139">As configurações de extensão elástica variam dependendo do tipo de manipulação.</span><span class="sxs-lookup"><span data-stu-id="50779-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="50779-140">A tradução e a escala são representadas por extensão [elástica de volume](#volume-elastic-extent) e a rotação é representada por uma [extensão elástica de quatternion](#quaternion-elastic-extent).</span><span class="sxs-lookup"><span data-stu-id="50779-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="50779-141">Extensão elástica do volume</span><span class="sxs-lookup"><span data-stu-id="50779-141">Volume elastic extent</span></span>

<span data-ttu-id="50779-142">As extensão de volume definem um espaço tridimensional no qual o oscilador harmônico sem gravidade está livre para se mover.</span><span class="sxs-lookup"><span data-stu-id="50779-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Limites de alongamento de volume elástico](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="50779-144">**StretchBounds**: representa os limites inferiores do espaço elástico.</span><span class="sxs-lookup"><span data-stu-id="50779-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="50779-145">**UseBounds:** se os limites de stretch devem ser respeitados pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="50779-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="50779-146">Se true, quando a iteração atual da posição de destino estiver fora dos limites de stretch, a força final será aplicada.</span><span class="sxs-lookup"><span data-stu-id="50779-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="50779-147">**SnapPoints:** pontos dentro do espaço ao qual o sistema será encaixado.</span><span class="sxs-lookup"><span data-stu-id="50779-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="50779-148">**RepeatSnapPoints:** repete os pontos de snap para infinito.</span><span class="sxs-lookup"><span data-stu-id="50779-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="50779-149">Os pontos de snap existentes servirão como um módulo em que os pontos de snap reais são mapeados para os múltiplos inteiros mais próximos de cada ponto de snap.</span><span class="sxs-lookup"><span data-stu-id="50779-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="50779-150">**SnapRadius:** distância na qual os pontos de snap começam a forçar a fonte.</span><span class="sxs-lookup"><span data-stu-id="50779-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Grade de Snap Grid de Volume Elástico](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="50779-152">Extensão elástica do Quatternion</span><span class="sxs-lookup"><span data-stu-id="50779-152">Quaternion elastic extent</span></span>

<span data-ttu-id="50779-153">As extensão quaternion definem um espaço de rotação quatrodimensional no qual o oscilador ínteco sem gravidade está livre para girar.</span><span class="sxs-lookup"><span data-stu-id="50779-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Exemplo de rotação elástica](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="50779-155">**SnapPoints:** ângulos de euler aos quais o sistema será encaixado.</span><span class="sxs-lookup"><span data-stu-id="50779-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="50779-156">**RepeatSnapPoints:** repete os pontos de snap.</span><span class="sxs-lookup"><span data-stu-id="50779-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="50779-157">Os pontos de snap existentes servirão como um módulo em que os pontos de snap reais são mapeados para os múltiplos inteiros mais próximos de cada ponto de snap.</span><span class="sxs-lookup"><span data-stu-id="50779-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="50779-158">**SnapRadius:** arco angular no qual os pontos de ajuste começam a forçar a fonte em graus euler.</span><span class="sxs-lookup"><span data-stu-id="50779-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="50779-159">Cena de exemplo do Elastics</span><span class="sxs-lookup"><span data-stu-id="50779-159">Elastics example scene</span></span>

<span data-ttu-id="50779-160">Você pode encontrar exemplos de configurações de elásticos na `ElasticSystemExample` cena.</span><span class="sxs-lookup"><span data-stu-id="50779-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Cena de exemplo do Elastics](../images/elastics/Elastics_Example_Scene.png)
