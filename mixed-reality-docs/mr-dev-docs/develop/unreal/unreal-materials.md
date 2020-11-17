---
title: Recomendações de material no Unreal
description: Visão geral dos materiais no mecanismo inreal.
author: hferrone
ms.author: v-hferrone
ms.date: 09/18/2020
ms.topic: article
keywords: Inreal, Engine 4, UE4, HoloLens, HoloLens 2, desenvolvimento, materiais, documentação, guias, recursos, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: d57689e9427ab5877e3afb49b0d19f35df6c47d2
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94678935"
---
# <a name="material-recommendations-in-unreal"></a><span data-ttu-id="dfb14-104">Recomendações de material no Unreal</span><span class="sxs-lookup"><span data-stu-id="dfb14-104">Material recommendations in Unreal</span></span>

<span data-ttu-id="dfb14-105">Os materiais podem fazer ou interromper o desempenho em um mecanismo inreal.</span><span class="sxs-lookup"><span data-stu-id="dfb14-105">Materials can make or break performance in Unreal Engine.</span></span> <span data-ttu-id="dfb14-106">Esta página atua como um início rápido sobre as configurações básicas que você deve usar para obter o melhor desempenho.</span><span class="sxs-lookup"><span data-stu-id="dfb14-106">This page acts as a quick-start on the basic settings you should be using in order to get the best performance.</span></span>

## <a name="using-customizeduvs"></a><span data-ttu-id="dfb14-107">Usando CustomizedUVs</span><span class="sxs-lookup"><span data-stu-id="dfb14-107">Using CustomizedUVs</span></span>

<span data-ttu-id="dfb14-108">Se você precisar fornecer um lado de UVs em seu material, deverá usar CustomizedUVs em vez de modificar a UV do nó de textura diretamente.</span><span class="sxs-lookup"><span data-stu-id="dfb14-108">If you need to provide tiling of UVs on your material, you should use CustomizedUVs rather than modifying the UV of the texture node directly.</span></span> <span data-ttu-id="dfb14-109">CustomizedUVs permite que a manipulação UV aconteça nos sombreadores de vértice em vez de sombreador de pixel.</span><span class="sxs-lookup"><span data-stu-id="dfb14-109">CustomizedUVs allow UV manipulation to happen in the Vertex shaders rather than Pixel shader.</span></span> 

![Configurações de material em inreal](images/unreal-materials-img-01c.png)

<span data-ttu-id="dfb14-111">Você pode encontrar mais detalhes sobre materiais na [documentação do mecanismo inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) e exemplos de práticas recomendadas nas capturas de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="dfb14-111">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html) and best practice examples in the screenshots below:</span></span>

<span data-ttu-id="dfb14-112">[ ![ Configurações de material recomendadas em ](images/unreal-materials-img-01.png) configuração de ](images/unreal-materials-img-01.png#lightbox) 
 *material recomendado* inreal</span><span class="sxs-lookup"><span data-stu-id="dfb14-112">[ ![Recommended material settings in Unreal](images/unreal-materials-img-01.png) ](images/unreal-materials-img-01.png#lightbox)
*Recommended material setup*</span></span>

<span data-ttu-id="dfb14-113">[ ![ Configurações de material não recomendadas em ](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox) 
 *configuração de material não recomendável não recomendada*</span><span class="sxs-lookup"><span data-stu-id="dfb14-113">[ ![Non recommended material settings in Unreal](images/unreal-materials-img-01b.png) ](images/unreal-materials-img-01b.png#lightbox)
*Non-recommended material setup*</span></span>

## <a name="changing-blend-mode"></a><span data-ttu-id="dfb14-114">Alterando o modo de mesclagem</span><span class="sxs-lookup"><span data-stu-id="dfb14-114">Changing Blend Mode</span></span>

<span data-ttu-id="dfb14-115">Você deve definir o modo de mesclagem como opaco, a menos que haja um motivo forte para fazer o contrário.</span><span class="sxs-lookup"><span data-stu-id="dfb14-115">You should set blend mode to opaque unless there is a strong reason to do otherwise.</span></span> <span data-ttu-id="dfb14-116">Os materiais mascarados e translúcidas são lentos.</span><span class="sxs-lookup"><span data-stu-id="dfb14-116">Masked and Translucent materials are slow.</span></span> <span data-ttu-id="dfb14-117">Você pode encontrar mais detalhes sobre materiais na [documentação do mecanismo inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="dfb14-117">You can find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Alterando o modo de mesclagem](images/unreal-materials-img-02.jpg)

## <a name="updating-lighting-for-mobile"></a><span data-ttu-id="dfb14-119">Atualizando a iluminação para dispositivos móveis</span><span class="sxs-lookup"><span data-stu-id="dfb14-119">Updating lighting for mobile</span></span>

<span data-ttu-id="dfb14-120">A precisão total deve ser desativada.</span><span class="sxs-lookup"><span data-stu-id="dfb14-120">Full precision should be turned off.</span></span> <span data-ttu-id="dfb14-121">A iluminação lightmap pode ser discada por meio da ativação de informações direcionais.</span><span class="sxs-lookup"><span data-stu-id="dfb14-121">Lightmap lighting can be dialed down by turning of directional information.</span></span> <span data-ttu-id="dfb14-122">Quando desabilitada, a iluminação de lightmaps será simples, mas mais barata.</span><span class="sxs-lookup"><span data-stu-id="dfb14-122">When disabled, lighting from lightmaps will be flat but cheaper.</span></span>

![Configurações de material móvel em não real](images/unreal-materials-img-03.jpg)

## <a name="adjusting-forward-shading"></a><span data-ttu-id="dfb14-124">Ajustando o sombreamento de encaminhamento</span><span class="sxs-lookup"><span data-stu-id="dfb14-124">Adjusting Forward Shading</span></span>

<span data-ttu-id="dfb14-125">Essas opções melhoram a fidelidade visual ao custo do desempenho.</span><span class="sxs-lookup"><span data-stu-id="dfb14-125">These options improve visual fidelity at the cost of performance.</span></span> <span data-ttu-id="dfb14-126">Eles devem ser desativados para o desempenho máximo.</span><span class="sxs-lookup"><span data-stu-id="dfb14-126">They should be turned off for maximum performance.</span></span>

![Encaminhe as configurações de material de sombreamento em um espaço inreal](images/unreal-materials-img-04.jpg)

## <a name="setting-material-translucency"></a><span data-ttu-id="dfb14-128">Configurando material Translucency</span><span class="sxs-lookup"><span data-stu-id="dfb14-128">Setting material translucency</span></span>

<span data-ttu-id="dfb14-129">Indica que o material translúcida não deve ser afetado por flor ou DOF.</span><span class="sxs-lookup"><span data-stu-id="dfb14-129">Indicates that the translucent material should not be affected by bloom or DOF.</span></span> <span data-ttu-id="dfb14-130">Como ambos os efeitos são raros no Sr, essa configuração deve estar ativada por padrão.</span><span class="sxs-lookup"><span data-stu-id="dfb14-130">Since both those effects are rare in MR, this setting should be on by default.</span></span>

![Configuração de Translucency separada para dispositivos móveis em não real](images/unreal-materials-img-05.jpg)

## <a name="optional-settings"></a><span data-ttu-id="dfb14-132">Configurações opcionais</span><span class="sxs-lookup"><span data-stu-id="dfb14-132">Optional settings</span></span>

<span data-ttu-id="dfb14-133">As configurações a seguir podem melhorar o desempenho, mas observe que elas desabilitam determinados recursos.</span><span class="sxs-lookup"><span data-stu-id="dfb14-133">The following settings may improve performance, but note that they disable certain features.</span></span> <span data-ttu-id="dfb14-134">Use essas configurações somente se você tiver certeza de que não precisa dos recursos em questão.</span><span class="sxs-lookup"><span data-stu-id="dfb14-134">Only use these settings if you are sure you don't need the features in question.</span></span>

![Configurações de material opcionais em inreal](images/unreal-materials-img-06.jpg)

<span data-ttu-id="dfb14-136">Se seu material não exigir reflexo ou brilho, a definição dessa opção pode fornecer um enorme aumento de desempenho.</span><span class="sxs-lookup"><span data-stu-id="dfb14-136">If your material doesn't require reflections or shine, then setting this option can provide a tremendous performance boost.</span></span> <span data-ttu-id="dfb14-137">No teste interno, é tão rápido quanto "unlit" ao fornecer informações de iluminação.</span><span class="sxs-lookup"><span data-stu-id="dfb14-137">In internal testing, it is as fast as "unlit" while providing lighting information.</span></span>

## <a name="best-practices"></a><span data-ttu-id="dfb14-138">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="dfb14-138">Best practices</span></span>

<span data-ttu-id="dfb14-139">As opções a seguir não são "configurações", assim como as práticas recomendadas relacionadas aos materiais.</span><span class="sxs-lookup"><span data-stu-id="dfb14-139">The following are not "settings" as much as they are best practices related to Materials.</span></span>

<span data-ttu-id="dfb14-140">Ao criar parâmetros, prefira usar "parâmetros estáticos" sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="dfb14-140">When creating parameters, prefer to use "Static Parameters" wherever possible.</span></span> <span data-ttu-id="dfb14-141">Opções estáticas podem ser usadas para remover uma ramificação inteira de um material sem custo de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dfb14-141">Static Switches can be used to remove an entire branch of a material with no runtime cost.</span></span> <span data-ttu-id="dfb14-142">As instâncias podem ter valores diferentes, tornando possível ter uma configuração de sombreador de modelo sem perda de desempenho.</span><span class="sxs-lookup"><span data-stu-id="dfb14-142">Instances can have different values, making it possible to have a templated shader setup with no performance loss.</span></span> <span data-ttu-id="dfb14-143">No entanto, a desvantagem é que isso cria muitas permutações que causarão muita recompilação de sombreador.</span><span class="sxs-lookup"><span data-stu-id="dfb14-143">The downside, however, is that this creates many permutations that will cause a lot of shader recompilation.</span></span> <span data-ttu-id="dfb14-144">Tente minimizar o número de parâmetros estáticos no material e o número de permutações desses parâmetros estáticos que são realmente usados.</span><span class="sxs-lookup"><span data-stu-id="dfb14-144">Try to minimize the number of static parameters in the material and the number of permutations of those static parameters that are actually used.</span></span> <span data-ttu-id="dfb14-145">Você pode encontrar mais detalhes sobre como renderizar os parâmetros de material na [documentação do mecanismo inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span><span class="sxs-lookup"><span data-stu-id="dfb14-145">You can find more details on rendering material parameters in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/ExpressionReference/Parameters/index.html#staticswitchparameter).</span></span>

![Práticas recomendadas para configurações de material](images/unreal-materials-img-07.jpg)

<span data-ttu-id="dfb14-147">Ao criar instâncias de material, a preferência deve ser dada à **constante da instância material** sobre a instância de material dinâmica.</span><span class="sxs-lookup"><span data-stu-id="dfb14-147">When creating Material Instances, preference should be given to **Material Instance Constant** over Material Instance Dynamic.</span></span> <span data-ttu-id="dfb14-148">**Constante de instância de material** é um material de instância que calcula apenas uma vez, antes do tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dfb14-148">**Material Instance Constant** is an instanced Material that calculates only once, prior to runtime.</span></span>

<span data-ttu-id="dfb14-149">A instância de material criada por meio do navegador de conteúdo (**clique com o botão direito do mouse > criar instância de material**) é uma constante de instância de material.</span><span class="sxs-lookup"><span data-stu-id="dfb14-149">The material instance created via the Content Browser (**right-click > Create Material Instance**) is a Material Instance Constant.</span></span> <span data-ttu-id="dfb14-150">A instância de material dinâmica é criada por meio de código.</span><span class="sxs-lookup"><span data-stu-id="dfb14-150">Material Instance Dynamic are created via code.</span></span> <span data-ttu-id="dfb14-151">Você pode encontrar mais detalhes sobre as instâncias de material na [documentação do mecanismo inreal](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span><span class="sxs-lookup"><span data-stu-id="dfb14-151">You can find more details on material instances in the [Unreal Engine documentation](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html).</span></span>

![Criando instâncias de material em um não real](images/unreal-materials-img-08.png)

<span data-ttu-id="dfb14-153">Fique atento à complexidade dos seus materiais/sombreadores.</span><span class="sxs-lookup"><span data-stu-id="dfb14-153">Keep an eye on the complexity of your materials/shaders.</span></span> <span data-ttu-id="dfb14-154">Você pode exibir o custo de seu material em várias plataformas clicando no ícone de estatísticas de plataforma.</span><span class="sxs-lookup"><span data-stu-id="dfb14-154">You can view the cost of your Material on various platforms by clicking on the Platform Stats icon.</span></span> <span data-ttu-id="dfb14-155">Você também pode encontrar mais detalhes sobre materiais na [documentação do mecanismo inreal](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span><span class="sxs-lookup"><span data-stu-id="dfb14-155">You can also find more details on materials in the [Unreal Engine documentation](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html).</span></span>

![Criando configurações dinâmicas da instância de material em um inreal](images/unreal-materials-img-09.png)

<span data-ttu-id="dfb14-157">Você pode obter uma ideia rápida da complexidade relativa do seu sombreador por meio do [modo de exibição](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)de complexidade do sombreador.</span><span class="sxs-lookup"><span data-stu-id="dfb14-157">You can get a quick idea of the relative complexity of your shader via the Shader Complexity [View mode](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html).</span></span>

* <span data-ttu-id="dfb14-158">Tecla de atalho do modo de exibição: Alt + 8</span><span class="sxs-lookup"><span data-stu-id="dfb14-158">View Mode Hotkey: Alt + 8</span></span>
* <span data-ttu-id="dfb14-159">Comando de console: ViewMode shadercomplexity</span><span class="sxs-lookup"><span data-stu-id="dfb14-159">Console command: viewmode shadercomplexity</span></span>

![Complexidade de material em não real](images/unreal-materials-img-10.png)

## <a name="see-also"></a><span data-ttu-id="dfb14-161">Veja também</span><span class="sxs-lookup"><span data-stu-id="dfb14-161">See also</span></span>
* [<span data-ttu-id="dfb14-162">Materiais móveis</span><span class="sxs-lookup"><span data-stu-id="dfb14-162">Mobile materials</span></span>](https://docs.unrealengine.com/Platforms/Mobile/Materials/index.html)
* [<span data-ttu-id="dfb14-163">Modos de exibição</span><span class="sxs-lookup"><span data-stu-id="dfb14-163">View modes</span></span>](https://docs.unrealengine.com/Engine/UI/LevelEditor/Viewports/ViewModes/index.html)
* [<span data-ttu-id="dfb14-164">Instâncias de material</span><span class="sxs-lookup"><span data-stu-id="dfb14-164">Material instances</span></span>](https://docs.unrealengine.com/Engine/Rendering/Materials/MaterialInstances/index.html)
