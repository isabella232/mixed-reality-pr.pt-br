---
title: Recomendações de desempenho para o Unreal
description: Saiba como obter o melhor desempenho dos seus aplicativos de realidade misturada com as configurações recomendadas do projeto do Unreal.
author: hferrone
ms.author: safarooq
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: e956f12d27c826cff35e0b65957060953073a28b
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583063"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="1f793-104">Recomendações de desempenho para o Unreal</span><span class="sxs-lookup"><span data-stu-id="1f793-104">Performance recommendations for Unreal</span></span>

<span data-ttu-id="1f793-105">O Unreal Engine traz vários recursos que podem aumentar o desempenho de um aplicativo, tudo isso com base na discussão descrita em [Recomendações de desempenho para realidade misturada](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span><span class="sxs-lookup"><span data-stu-id="1f793-105">Unreal Engine has several features that can increase an apps performance, all based on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md).</span></span> <span data-ttu-id="1f793-106">Você é incentivado a detectar os gargalos do aplicativo, analisar e criar o perfil de aplicativos de realidade misturada e correções de desempenho gerais antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1f793-106">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="1f793-107">Configurações recomendadas de projetos do Unreal</span><span class="sxs-lookup"><span data-stu-id="1f793-107">Recommended Unreal project settings</span></span>

<span data-ttu-id="1f793-108">Você pode encontrar cada uma das configurações a seguir em **Editar > Configurações do Projeto**.</span><span class="sxs-lookup"><span data-stu-id="1f793-108">You can find each of the following settings in **Edit > Project Settings**.</span></span>

1. <span data-ttu-id="1f793-109">Como usar o renderizador de VR para dispositivos móveis:</span><span class="sxs-lookup"><span data-stu-id="1f793-109">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="1f793-110">Role até a seção **Projeto**, selecione **Hardware de Destino** e defina a plataforma de destino como **Celular/Tablet**</span><span class="sxs-lookup"><span data-stu-id="1f793-110">Scroll to the **Project** section, select **Target Hardware**, and set the target platform to **Mobile/Tablet**</span></span>

![Configuração de destino para dispositivos móveis](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="1f793-112">Como usar o Renderizador de Encaminhamento:</span><span class="sxs-lookup"><span data-stu-id="1f793-112">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="1f793-113">O Renderizador de Encaminhamento é muito melhor para a Realidade Misturada do que o pipeline de renderização Adiado padrão devido ao número de recursos que podem ser desabilitados individualmente.</span><span class="sxs-lookup"><span data-stu-id="1f793-113">Forward Renderer is much better for Mixed Reality than the default Deferred rendering pipeline because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="1f793-114">Você pode encontrar mais informações na [documentação do Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="1f793-114">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Renderização de encaminhamento](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="1f793-116">Uso da exibição múltipla em dispositivos móveis:</span><span class="sxs-lookup"><span data-stu-id="1f793-116">Using mobile multi-view:</span></span>
    * <span data-ttu-id="1f793-117">Role a página até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **VR** e habilite **Estéreo Instanciado** e **Exibição Múltipla em Dispositivos Móveis**.</span><span class="sxs-lookup"><span data-stu-id="1f793-117">Scroll to the **Engine** section, select **Rendering**, expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View**.</span></span> <span data-ttu-id="1f793-118">O HDR móvel deve estar desmarcado.</span><span class="sxs-lookup"><span data-stu-id="1f793-118">Mobile HDR should be unchecked.</span></span>

![Configurações de renderização de VR](images/unreal/performance-recommendations-img-03.png)

4. <span data-ttu-id="1f793-120">**[Somente em OpenXR]** Verifique se **Padrão** ou **D3D12** é o **RHI Padrão** selecionado:</span><span class="sxs-lookup"><span data-stu-id="1f793-120">**[OpenXR only]** Ensure **Default** or **D3D12** is the selected **Default RHI**:</span></span>
    * <span data-ttu-id="1f793-121">A seleção de **D3D11** terá um impacto negativo no desempenho devido à plataforma que executa uma passagem de renderização adicional.</span><span class="sxs-lookup"><span data-stu-id="1f793-121">Selecting **D3D11** will have a negative performance impact due to the platform performing an additional render pass.</span></span> <span data-ttu-id="1f793-122">O **D3D12** deve oferecer aprimoramentos de desempenho de renderização além de evitar a passagem de renderização adicional.</span><span class="sxs-lookup"><span data-stu-id="1f793-122">**D3D12** should provide rendering performance improvements besides avoiding the additional render pass.</span></span>

![RHI Padrão](images/unreal/performance-recommendations-img-09.png)

5. <span data-ttu-id="1f793-124">Como desabilitar a aplicação de neblina de vértice:</span><span class="sxs-lookup"><span data-stu-id="1f793-124">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="1f793-125">a aplicação de neblina de vértice se aplica a cálculos de neblina em cada vértice em um polígono e interpola os resultados na face do polígono.</span><span class="sxs-lookup"><span data-stu-id="1f793-125">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="1f793-126">Se o jogo não usar a neblina, recomendamos desabilitar a Neblina de Vértice para aumentar o desempenho do sombreamento.</span><span class="sxs-lookup"><span data-stu-id="1f793-126">If your game does not use fog, we recommend disabling Vertex Fogging to increase shading performance.</span></span>

![Opções de aplicação de neblina do vértice](images/unreal/performance-recommendations-img-05.png)

6. <span data-ttu-id="1f793-128">Desabilitando a remoção por oclusão:</span><span class="sxs-lookup"><span data-stu-id="1f793-128">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="1f793-129">Role até a seção **Mecanismo**, selecione **Renderização**, expanda a seção **Remoção** e desmarque **Remoção por Oclusão**.</span><span class="sxs-lookup"><span data-stu-id="1f793-129">Scroll to the **Engine** section, select **Rendering**, expand the **Culling** section, and uncheck **Occlusion Culling**.</span></span>
        + <span data-ttu-id="1f793-130">Se você precisa usar a remoção por oclusão em uma cena detalhada que está sendo renderizada, recomendamos habilitar o **Suporte a Remoção por Oclusão de Software** em **Mecanismo > Renderização**.</span><span class="sxs-lookup"><span data-stu-id="1f793-130">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering**.</span></span> <span data-ttu-id="1f793-131">O Unreal fará o trabalho na CPU e evitará consultas de oclusão de GPU, que têm um desempenho insatisfatório no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="1f793-131">Unreal will do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="1f793-132">A remoção da oclusão na GPU em dispositivos móveis é lenta.</span><span class="sxs-lookup"><span data-stu-id="1f793-132">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="1f793-133">Em geral, convém que a GPU se preocupe principalmente com a renderização.</span><span class="sxs-lookup"><span data-stu-id="1f793-133">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="1f793-134">Se você achar que a oclusão ajudará o desempenho, tente habilitar a oclusão do software.</span><span class="sxs-lookup"><span data-stu-id="1f793-134">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> 

> [!NOTE]
> <span data-ttu-id="1f793-135">A habilitação da oclusão do software pode piorar o desempenho se você já está vinculado à CPU por um grande número de chamadas de desenho.</span><span class="sxs-lookup"><span data-stu-id="1f793-135">Enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Desabilitar a remoção de oclusão](images/unreal/performance-recommendations-img-02.png)

7. <span data-ttu-id="1f793-137">Desabilitando a passagem personalizada do estêncil de profundidade:</span><span class="sxs-lookup"><span data-stu-id="1f793-137">Disabling Custom Depth-Stencil Pass:</span></span>
    * <span data-ttu-id="1f793-138">A desabilitação do Estêncil de Profundidade Personalizada exige uma passagem extra, o que significa que ele é lento.</span><span class="sxs-lookup"><span data-stu-id="1f793-138">Disabling Custom Depth-Stencil requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="1f793-139">A translucência também é lenta no Unreal.</span><span class="sxs-lookup"><span data-stu-id="1f793-139">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="1f793-140">Você pode encontrar mais informações na [documentação do Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="1f793-140">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Estêncil de profundidade](images/unreal/performance-recommendations-img-06.png)

8. <span data-ttu-id="1f793-142">Como reduzir os mapas de sombra em cascata:</span><span class="sxs-lookup"><span data-stu-id="1f793-142">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="1f793-143">a redução do número de mapas de sombra vai aprimorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="1f793-143">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="1f793-144">Em geral, você deve definir a propriedade como 1, a menos que haja uma perda de qualidade visível.</span><span class="sxs-lookup"><span data-stu-id="1f793-144">Generally, you should set the property to 1 unless there's a visible quality loss.</span></span> 

![Mapas de sombra em cascata](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="1f793-146">Configurações opcionais</span><span class="sxs-lookup"><span data-stu-id="1f793-146">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="1f793-147">As configurações a seguir podem aprimorar o desempenho, mas à custa de desabilitar determinados recursos.</span><span class="sxs-lookup"><span data-stu-id="1f793-147">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="1f793-148">Use essas configurações somente se tiver certeza de que não precisa dos recursos em questão.</span><span class="sxs-lookup"><span data-stu-id="1f793-148">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="1f793-149">Redução da Permuta do Sombreador Móvel</span><span class="sxs-lookup"><span data-stu-id="1f793-149">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="1f793-150">Se as luzes não forem movidas independentemente da câmera, você poderá definir o valor da propriedade com segurança como 0.</span><span class="sxs-lookup"><span data-stu-id="1f793-150">If your lights don't move independently of the camera, then you can safely set the property value to 0.</span></span> <span data-ttu-id="1f793-151">O principal benefício é que ele permitirá que o Unreal remova várias permutações de sombreador, acelerando a compilação do sombreador.</span><span class="sxs-lookup"><span data-stu-id="1f793-151">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Redução da permuta do sombreador móvel](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="1f793-153">Confira também</span><span class="sxs-lookup"><span data-stu-id="1f793-153">See also</span></span>

* [<span data-ttu-id="1f793-154">Diretrizes de desempenho de dispositivos móveis do mecanismo do Unreal</span><span class="sxs-lookup"><span data-stu-id="1f793-154">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)