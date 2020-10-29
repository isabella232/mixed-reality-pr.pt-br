---
title: Recomendações de desempenho para o Unreal
description: Recomendações para um desempenho ideal para aplicativos de realidade misturada no Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 5/5/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, mixed reality, performance, optimization, settings, documentation
ms.openlocfilehash: 64c8cdf4900234a4486cf9b575671321a8430160
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91695178"
---
# <a name="performance-recommendations-for-unreal"></a><span data-ttu-id="6f631-104">Recomendações de desempenho para o Unreal</span><span class="sxs-lookup"><span data-stu-id="6f631-104">Performance recommendations for Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="6f631-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="6f631-105">Overview</span></span>

<span data-ttu-id="6f631-106">Este artigo se baseia na discussão descrita em [recomendações de desempenho para realidade misturada](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), mas se concentra em recursos específicos do Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="6f631-106">This article builds on the discussion outlined in [performance recommendations for mixed reality](../platform-capabilities-and-apis/understanding-performance-for-mixed-reality.md), but focuses on features specific to Unreal Engine.</span></span> <span data-ttu-id="6f631-107">Você é incentivado a detectar os gargalos do aplicativo, analisar e criar o perfil de aplicativos de realidade misturada e correções de desempenho gerais antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="6f631-107">You're encouraged to read up on application bottlenecks, analyzing and profiling mixed reality apps, and general performance fixes before continuing.</span></span>

## <a name="recommended-unreal-project-settings"></a><span data-ttu-id="6f631-108">Configurações recomendadas de projetos do Unreal</span><span class="sxs-lookup"><span data-stu-id="6f631-108">Recommended Unreal project settings</span></span>
<span data-ttu-id="6f631-109">Você pode encontrar cada uma das configurações a seguir em **Editar > Configurações do Projeto** .</span><span class="sxs-lookup"><span data-stu-id="6f631-109">You can find each of the following settings in **Edit > Project Settings** .</span></span>

1. <span data-ttu-id="6f631-110">Como usar o renderizador de VR para dispositivos móveis:</span><span class="sxs-lookup"><span data-stu-id="6f631-110">Using the mobile VR renderer:</span></span>
    * <span data-ttu-id="6f631-111">Role até a seção **Projeto** , selecione **Hardware de Destino** e defina a plataforma de destino como **Celular/Tablet**</span><span class="sxs-lookup"><span data-stu-id="6f631-111">Scroll to the **Project** section, select **Target Hardware** , and set the target platform to **Mobile/Tablet**</span></span>

![Configuração de destino para dispositivos móveis](images/unreal/performance-recommendations-img-01.png)

2. <span data-ttu-id="6f631-113">Como usar o Renderizador de Encaminhamento:</span><span class="sxs-lookup"><span data-stu-id="6f631-113">Using the Forward Renderer:</span></span> 
    * <span data-ttu-id="6f631-114">Esse recurso é muito melhor para a Realidade Misturada do que o pipeline de renderização Adiado padrão.</span><span class="sxs-lookup"><span data-stu-id="6f631-114">This feature is much better for Mixed Reality than the default Deferred rendering pipeline.</span></span> <span data-ttu-id="6f631-115">Isso ocorre principalmente devido ao número de recursos que podem ser desativados individualmente.</span><span class="sxs-lookup"><span data-stu-id="6f631-115">This is primarily because of the number of features that can be individually turned off.</span></span> 
    * <span data-ttu-id="6f631-116">Você pode encontrar mais informações na [documentação do Unreal](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span><span class="sxs-lookup"><span data-stu-id="6f631-116">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Platforms/VR/DevelopVR/VRPerformance/index.html).</span></span>

![Renderização de encaminhamento](images/unreal/performance-recommendations-img-04.png)

3. <span data-ttu-id="6f631-118">Como desabilitar a aplicação de neblina de vértice:</span><span class="sxs-lookup"><span data-stu-id="6f631-118">Disabling Vertex Fogging:</span></span> 
    * <span data-ttu-id="6f631-119">a aplicação de neblina de vértice se aplica a cálculos de neblina em cada vértice em um polígono e interpola os resultados na face do polígono.</span><span class="sxs-lookup"><span data-stu-id="6f631-119">Vertex fogging applies fog calculations at each vertex in a polygon and then interpolates the results across the face of the polygon.</span></span> <span data-ttu-id="6f631-120">Se o jogo não usar neblina, você deverá escolher essa configuração para desabilitar a neblina a fim de aumentar o desempenho do sombreamento.</span><span class="sxs-lookup"><span data-stu-id="6f631-120">If your game does not use fog, you should choose this setting to disable fog to increase shading performance.</span></span>

![Opções de aplicação de neblina do vértice](images/unreal/performance-recommendations-img-05.png)

4. <span data-ttu-id="6f631-122">Desabilitando a remoção por oclusão:</span><span class="sxs-lookup"><span data-stu-id="6f631-122">Disabling occlusion culling:</span></span>
    * <span data-ttu-id="6f631-123">Role até a seção **Mecanismo** , selecione **Renderização** , expanda a seção **Remoção** e desmarque **Remoção por Oclusão** .</span><span class="sxs-lookup"><span data-stu-id="6f631-123">Scroll to the **Engine** section, select **Rendering** , expand the **Culling** section, and uncheck **Occlusion Culling** .</span></span>
        + <span data-ttu-id="6f631-124">Se você precisa usar a remoção por oclusão em uma cena detalhada que está sendo renderizada, recomendamos habilitar o **Suporte a Remoção por Oclusão de Software** em **Mecanismo > Renderização** .</span><span class="sxs-lookup"><span data-stu-id="6f631-124">If you need occlusion culling for a detailed scene being rendered, it's recommended that you enable **Support Software Occlusion Culling** in **Engine > Rendering** .</span></span> <span data-ttu-id="6f631-125">Isso permite que o Unreal faça o trabalho na CPU e evite consultas de oclusão de GPU, que têm mau desempenho no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6f631-125">This lets Unreal to do the work on the CPU and avoid GPU occlusion queries, which perform poorly on HoloLens 2.</span></span>
    * <span data-ttu-id="6f631-126">A remoção da oclusão na GPU em dispositivos móveis é lenta.</span><span class="sxs-lookup"><span data-stu-id="6f631-126">Occlusion culling on the GPU on mobile devices is slow.</span></span> <span data-ttu-id="6f631-127">Em geral, convém que a GPU se preocupe principalmente com a renderização.</span><span class="sxs-lookup"><span data-stu-id="6f631-127">Generally, you want the GPU to be primarily concerned with rendering.</span></span> <span data-ttu-id="6f631-128">Se você achar que a oclusão ajudará o desempenho, tente habilitar a oclusão do software.</span><span class="sxs-lookup"><span data-stu-id="6f631-128">If you feel that occlusion will help performance, try enabling software occlusion instead.</span></span> <span data-ttu-id="6f631-129">Observe que a habilitação da oclusão do software poderá piorar o desempenho se você já estiver vinculado à CPU por um grande número de chamadas de desenho.</span><span class="sxs-lookup"><span data-stu-id="6f631-129">Note that enabling software occlusion could make performance worse if you're already CPU bound by a large number of draw-calls.</span></span>

![Desabilitar a remoção de oclusão](images/unreal/performance-recommendations-img-02.png)

    
5. <span data-ttu-id="6f631-131">Como desabilitar o estêncil de profundidade:</span><span class="sxs-lookup"><span data-stu-id="6f631-131">Disabling Depth-Stencil:</span></span>
    * <span data-ttu-id="6f631-132">esse recurso requer uma passagem extra, o que significa que ele é lento.</span><span class="sxs-lookup"><span data-stu-id="6f631-132">This feature requires an extra pass, meaning it's slow.</span></span> <span data-ttu-id="6f631-133">A translucência também é lenta no Unreal.</span><span class="sxs-lookup"><span data-stu-id="6f631-133">Translucency is also slow on Unreal.</span></span> <span data-ttu-id="6f631-134">Você pode encontrar mais informações na [documentação do Unreal](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span><span class="sxs-lookup"><span data-stu-id="6f631-134">You can find more information in [Unreal's documentation](https://docs.unrealengine.com/Engine/Performance/Guidelines/index.html).</span></span>

![Estêncil de profundidade](images/unreal/performance-recommendations-img-06.png)

6. <span data-ttu-id="6f631-136">Uso da exibição múltipla em dispositivos móveis:</span><span class="sxs-lookup"><span data-stu-id="6f631-136">Using mobile multi-view:</span></span>
    * <span data-ttu-id="6f631-137">Role a página até a seção **Mecanismo** , selecione **Renderização** , expanda a seção **VR** e habilite **Estéreo Instanciado** e **Exibição Múltipla em Dispositivos Móveis** .</span><span class="sxs-lookup"><span data-stu-id="6f631-137">Scroll to the **Engine** section, select **Rendering** , expand the **VR** section, and enable both **Instanced Stereo** and **Mobile Multi-View** .</span></span> <span data-ttu-id="6f631-138">O HDR móvel deve estar desmarcado.</span><span class="sxs-lookup"><span data-stu-id="6f631-138">Mobile HDR should be unchecked.</span></span>

![Configurações de renderização de VR](images/unreal/performance-recommendations-img-03.png)

7. <span data-ttu-id="6f631-140">Como reduzir os mapas de sombra em cascata:</span><span class="sxs-lookup"><span data-stu-id="6f631-140">Reducing Cascaded Shadow Maps:</span></span> 
    * <span data-ttu-id="6f631-141">a redução do número de mapas de sombra vai aprimorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="6f631-141">Reducing the number of shadow maps will improve performance.</span></span> <span data-ttu-id="6f631-142">Em geral, isso deve ser definido como 1, a menos que haja uma perda de qualidade visível.</span><span class="sxs-lookup"><span data-stu-id="6f631-142">Generally, this should be set to 1 unless there is a visible quality loss.</span></span> 

![Mapas de sombra em cascata](images/unreal/performance-recommendations-img-07.png)

## <a name="optional-settings"></a><span data-ttu-id="6f631-144">Configurações opcionais</span><span class="sxs-lookup"><span data-stu-id="6f631-144">Optional settings</span></span>

> [!NOTE]
> <span data-ttu-id="6f631-145">As configurações a seguir podem aprimorar o desempenho, mas à custa de desabilitar determinados recursos.</span><span class="sxs-lookup"><span data-stu-id="6f631-145">The following settings may improve performance, but at the cost of disabling certain features.</span></span> <span data-ttu-id="6f631-146">Use essas configurações somente se tiver certeza de que não precisa dos recursos em questão.</span><span class="sxs-lookup"><span data-stu-id="6f631-146">Only use these settings if you're sure you don't need the features in question.</span></span>

1. <span data-ttu-id="6f631-147">Redução da Permuta do Sombreador Móvel</span><span class="sxs-lookup"><span data-stu-id="6f631-147">Mobile Shader Permutation Reduction</span></span>
    * <span data-ttu-id="6f631-148">Se as luzes não forem movidas independentemente da câmera, você poderá definir esse valor com segurança como 0.</span><span class="sxs-lookup"><span data-stu-id="6f631-148">If your lights don't move independently of the camera, then you can safely set this value to 0.</span></span> <span data-ttu-id="6f631-149">O principal benefício é que ele permitirá que o Unreal remova várias permutações de sombreador, acelerando a compilação do sombreador.</span><span class="sxs-lookup"><span data-stu-id="6f631-149">The primary benefit is that it will allow Unreal to cull several shader permutations, speeding up shader compilation.</span></span>

![Redução da permuta do sombreador móvel](images/unreal/performance-recommendations-img-08.png)

## <a name="see-also"></a><span data-ttu-id="6f631-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="6f631-151">See also</span></span>
* [<span data-ttu-id="6f631-152">Diretrizes de desempenho de dispositivos móveis do mecanismo do Unreal</span><span class="sxs-lookup"><span data-stu-id="6f631-152">Unreal Engine mobile performance guidelines</span></span>]( https://docs.unrealengine.com/Platforms/Mobile/Performance/index.html)