---
title: Sistema elástico
description: documentação relacionada à simulação de elásticos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, ElasticsSystem,
ms.openlocfilehash: 01a4c4a337593252e0955c03e883e35e1329fc45
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145182"
---
# <a name="elastic-system-experimental"></a><span data-ttu-id="6a4ef-104">Sistema elástico (experimental)</span><span class="sxs-lookup"><span data-stu-id="6a4ef-104">Elastic system (experimental)</span></span>

![Sistema elástico](../images/elastics/Elastics_Main1.gif)

<span data-ttu-id="6a4ef-106">O MRTK vem com um sistema de simulação elástica que inclui uma ampla variedade de subclasses extensível e flexíveis, oferecendo associações para molas de quaternions bidimensionais, molas de volume tridimensionais e sistemas Spring lineares simples.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-106">MRTK comes with an elastic simulation system that includes a wide variety of extensible and flexible subclasses, offering bindings for 4-dimensional quaternion springs, 3-dimensional volume springs and simple linear spring systems.</span></span>

<span data-ttu-id="6a4ef-107">Atualmente, os seguintes componentes do MRTK que dão suporte ao [Gerenciador de elásticos](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) podem aproveitar a funcionalidade de elásticos:</span><span class="sxs-lookup"><span data-stu-id="6a4ef-107">Currently the following MRTK components supporting the [elastics manager](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager) can leverage elastics functionality:</span></span>

- [<span data-ttu-id="6a4ef-108">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="6a4ef-108">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="6a4ef-109">Manipulador de objeto</span><span class="sxs-lookup"><span data-stu-id="6a4ef-109">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)

## <a name="elastics-manager"></a><span data-ttu-id="6a4ef-110">Gerenciador de elásticos</span><span class="sxs-lookup"><span data-stu-id="6a4ef-110">Elastics manager</span></span>

![System2 elástico](../images/elastics/Elastics_Main.gif)

<span data-ttu-id="6a4ef-112">Os processos do elásticos Manager passaram pelas transformações e as alimentam no sistema elástico.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-112">The elastics manager processes passed transforms and feeds them into the elastics system.</span></span>

<span data-ttu-id="6a4ef-113">A habilitação de elásticos para componentes personalizados pode ser obtida por duas etapas:</span><span class="sxs-lookup"><span data-stu-id="6a4ef-113">Enabling elastics for custom components can be achieved by two steps:</span></span>

1. <span data-ttu-id="6a4ef-114">Chamar o método Initialize no início da manipulação, atualizar o sistema com a transformação do host atual.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-114">Calling the Initialize method on manipulation start, updating the system with the current host transform.</span></span>
1. <span data-ttu-id="6a4ef-115">Consultando ApplyHostTransform sempre que um cálculo de elásticos deve ser executado na transformação de destino atualizada.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-115">Querying ApplyHostTransform whenever a elastics calculation should be performed on the updated target transform.</span></span>

<span data-ttu-id="6a4ef-116">Observe que os elásticos continuarão simulando após o término da manipulação (por meio do loop de atualização do elásticos Manager).</span><span class="sxs-lookup"><span data-stu-id="6a4ef-116">Note that elastics will continue simulating once manipulation ends (through the elastics manager update loop).</span></span> <span data-ttu-id="6a4ef-117">Para bloquear o comportamento, a atualização automática de elásticos [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) pode ser definida como false.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-117">To block the behavior, elastics auto update [EnableElasticsUpdate](xref:Microsoft.MixedReality.Toolkit.Experimental.Physics.ElasticsManager.EnableElasticsUpdate) can be set to false.</span></span>

<span data-ttu-id="6a4ef-118">Por padrão, o componente do elásticos Manager, quando adicionado a um objeto de jogo, não tem elásticos habilitados para qualquer tipo de transformações.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-118">By default, the elastics manager component, when added to a game object, won't have elastics enabled for any transforms type.</span></span>
<span data-ttu-id="6a4ef-119">O campo `Manipulation types using elastic feedback` precisa ser habilitado para tipos de transformação específicos para criar a configuração de elásticos e extensões para o tipo selecionado.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-119">The field `Manipulation types using elastic feedback` needs to be enabled for specific transform types to create elastics configuration and extents for the selected type.</span></span>

### <a name="elastics-configurations"></a><span data-ttu-id="6a4ef-120">Configurações de elásticos</span><span class="sxs-lookup"><span data-stu-id="6a4ef-120">Elastics configurations</span></span>

<span data-ttu-id="6a4ef-121">Semelhante às [configurações de controle de limites](../ux-building-blocks/bounds-control.md#configuration-objects), o Gerenciador elástico vem com um conjunto de objetos de configuração que podem ser armazenados como objetos programáveis e compartilhados entre diferentes instâncias ou pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-121">Similar to [bounds control configurations](../ux-building-blocks/bounds-control.md#configuration-objects), elastic manager comes with a set of configuration objects that can be stored as scriptable objects and shared between different instances or prefabs.</span></span> <span data-ttu-id="6a4ef-122">As configurações podem ser compartilhadas e vinculadas como arquivos de ativo programáveis por script ou ativos de script aninhados individuais dentro do pré-fabricados.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-122">Configurations can be shared and linked either as individual scriptable asset files or nested scriptable assets inside of prefabs.</span></span> <span data-ttu-id="6a4ef-123">Outras configurações também podem ser definidas diretamente na instância sem vincular a um ativo externo ou aninhado que pode ser script.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-123">Further configurations can also be defined directly on the instance without linking to an external or nested scriptable asset.</span></span>

<span data-ttu-id="6a4ef-124">O inspetor do gerenciador de elásticos indicará se uma configuração é compartilhada ou emlinada como parte da instância atual mostrando uma mensagem no inspetor de propriedade.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-124">The elastics manager inspector will indicate whether a configuration is shared or inlined as part of the current instance by showing a message in the property inspector.</span></span> <span data-ttu-id="6a4ef-125">Além disso, as instâncias compartilhadas não serão editáveis diretamente na própria janela de propriedades do gerenciador de elásticos, mas, em vez disso, o ativo ao que está vinculando precisa ser diretamente modfiado para evitar alterações acidentais em configurações compartilhadas.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-125">In addition, shared instances won't be editable directly in the elastics manager property window itself, but instead the asset it's linking to has to be directly modfied to avoid any accidental changes on shared configurations.</span></span>

<span data-ttu-id="6a4ef-126">O Elastics Manager oferece opções de objetos de configuração para os seguintes tipos de transformação, cada um deles representado por [um objeto de configuração elástica](#elastic-configuration-object):</span><span class="sxs-lookup"><span data-stu-id="6a4ef-126">Elastics manager offers configuration objects options for the following transform types, each of them represented by a [elastic configuration object](#elastic-configuration-object):</span></span>

- <span data-ttu-id="6a4ef-127">Tradução elástica</span><span class="sxs-lookup"><span data-stu-id="6a4ef-127">Translation Elastic</span></span>
- <span data-ttu-id="6a4ef-128">Rotação elástica</span><span class="sxs-lookup"><span data-stu-id="6a4ef-128">Rotation Elastic</span></span>
- <span data-ttu-id="6a4ef-129">Dimensionar Elástico</span><span class="sxs-lookup"><span data-stu-id="6a4ef-129">Scale Elastic</span></span>

#### <a name="elastic-configuration-object"></a><span data-ttu-id="6a4ef-130">Objeto de configuração elástica</span><span class="sxs-lookup"><span data-stu-id="6a4ef-130">Elastic configuration object</span></span>

<span data-ttu-id="6a4ef-131">Uma configuração elástica define as propriedades de um sistema diferencial de oscilador insuceso escuros.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-131">A elastics configuration defines properties for a damped harmonic oscillator differential system.</span></span>
<span data-ttu-id="6a4ef-132">As propriedades a seguir podem ser ajustadas, mas já vêm com um conjunto de padrões no MRTK:</span><span class="sxs-lookup"><span data-stu-id="6a4ef-132">The following properties can be adjusted but already come with a set of defaults in MRTK:</span></span>

- <span data-ttu-id="6a4ef-133">**Massa:** massa do elemento de oscilador simulado.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-133">**Mass**: mass of the simulated oscillator element.</span></span>
- <span data-ttu-id="6a4ef-134">**HandK:** constante de spring da mão.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-134">**HandK**: hand spring constant.</span></span>
- <span data-ttu-id="6a4ef-135">**EndK:** constante spring end cap.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-135">**EndK**: end cap spring constant.</span></span>
- <span data-ttu-id="6a4ef-136">**SnapK:** constante spring do ponto de encaixe.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-136">**SnapK**: snap point spring constant.</span></span>
- <span data-ttu-id="6a4ef-137">**Arraste**: fator de arrastar/damper, proporcional à velocidade.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-137">**Drag**: drag/damper factor, proportional to velocity.</span></span>

### <a name="elastics-extents"></a><span data-ttu-id="6a4ef-138">Extensão elástica</span><span class="sxs-lookup"><span data-stu-id="6a4ef-138">Elastics extents</span></span>

<span data-ttu-id="6a4ef-139">As configurações de extensão elástica variam dependendo do tipo de manipulação.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-139">Elastics extents settings vary depending on the type of manipulation.</span></span> <span data-ttu-id="6a4ef-140">A tradução e a escala são representadas por extensão [elástica de volume](#volume-elastic-extent) e a rotação é representada por uma [extensão elástica de quatternion](#quaternion-elastic-extent).</span><span class="sxs-lookup"><span data-stu-id="6a4ef-140">Translation and scale are represented by [volume elastic extents](#volume-elastic-extent) and rotation is represented by a [quaternion elastic extent](#quaternion-elastic-extent).</span></span>

#### <a name="volume-elastic-extent"></a><span data-ttu-id="6a4ef-141">Extensão elástica do volume</span><span class="sxs-lookup"><span data-stu-id="6a4ef-141">Volume elastic extent</span></span>

<span data-ttu-id="6a4ef-142">As extensão de volume definem um espaço tridimensional no qual o oscilador harmônico sem gravidade está livre para se mover.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-142">Volume extents define a three dimensional space in which the damped harmonic oscillator is free to move.</span></span>

![Limites de ampliação do volume elástico](../images/elastics/Elastics_Volume_Bounds.gif)

- <span data-ttu-id="6a4ef-144">**StretchBounds**: representa os limites inferiores do espaço elástico.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-144">**StretchBounds**: represents the lower bounds of the elastic space.</span></span>
- <span data-ttu-id="6a4ef-145">**UseBounds**: se os limites de ampliação devem ser respeitados pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-145">**UseBounds**: whether the stretch bounds should be respected by the system.</span></span> <span data-ttu-id="6a4ef-146">Se for true, quando a iteração atual da posição de destino estiver fora dos limites de ampliação, a força final será aplicada.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-146">If true, when the current iteration of the target position is outside the stretch bounds, the end force will be applied.</span></span>
- <span data-ttu-id="6a4ef-147">**SnapPoints**: aponta para dentro do espaço no qual o sistema será ajustado.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-147">**SnapPoints**: points inside the space to which the system will snap.</span></span>
- <span data-ttu-id="6a4ef-148">**RepeatSnapPoints**: repete os pontos de ajuste para infinito.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-148">**RepeatSnapPoints**: repeats the snap points to infinity.</span></span> <span data-ttu-id="6a4ef-149">Os pontos de ajuste existentes servirão como um módulo em que os pontos de ajuste reais são mapeados para os múltiplos inteiros mais próximos de cada ponto de ajuste.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-149">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="6a4ef-150">**SnapRadius**: distância em que os pontos de encaixe começam a forçar a mola.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-150">**SnapRadius**: distance at which snap points begin forcing the spring.</span></span>

![Grade de ajuste de volume elástico](../images/elastics/Elastics_Volume_Snap.gif)

#### <a name="quaternion-elastic-extent"></a><span data-ttu-id="6a4ef-152">Extensão elástica do Quaternion</span><span class="sxs-lookup"><span data-stu-id="6a4ef-152">Quaternion elastic extent</span></span>

<span data-ttu-id="6a4ef-153">Extensões de Quaternion definem um espaço de rotação dimensional em que o Oscillator harmônica úmido é livre para girar.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-153">Quaternion extents define a four dimensional rotation space in which the damped harmonic oscillator is free to rotate.</span></span>

![Exemplo de rotação elástica](../images/elastics/Elastics_Rotation.gif)

- <span data-ttu-id="6a4ef-155">**SnapPoints**: ângulos de Euler para os quais o sistema será ajustado.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-155">**SnapPoints**: euler angles to which the system will snap.</span></span>
- <span data-ttu-id="6a4ef-156">**RepeatSnapPoints**: repete os pontos de ajuste.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-156">**RepeatSnapPoints**: repeats the snap points.</span></span> <span data-ttu-id="6a4ef-157">Os pontos de ajuste existentes servirão como um módulo em que os pontos de ajuste reais são mapeados para os múltiplos inteiros mais próximos de cada ponto de ajuste.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-157">Existing snap points will serve as a modulo where the actual snap points are mapped to the closest integer multiples of every snap point.</span></span>
- <span data-ttu-id="6a4ef-158">**SnapRadius**: arco-ângulo no qual os pontos de encaixe começam a forçar a mola em graus de Euler.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-158">**SnapRadius**: arc-angle at which snap points begin forcing the spring in euler degrees.</span></span>

## <a name="elastics-example-scene"></a><span data-ttu-id="6a4ef-159">Exemplo de cena de elásticos</span><span class="sxs-lookup"><span data-stu-id="6a4ef-159">Elastics example scene</span></span>

<span data-ttu-id="6a4ef-160">Você pode encontrar exemplos de configurações de elásticos na `ElasticSystemExample` cena.</span><span class="sxs-lookup"><span data-stu-id="6a4ef-160">You can find examples of elastics configurations in the `ElasticSystemExample` scene.</span></span>

![Exemplo de cena de elásticos](../images/elastics/Elastics_Example_Scene.png)
