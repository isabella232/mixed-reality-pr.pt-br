---
title: Âncoras Espaciais locais no Unreal
description: Guia para uso de âncoras espaciais em Unreal
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, recursos, documentação, guias, hologramas, âncoras espaciais, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 8be1521d44a9dda521c1570d3ac55955e475bc30
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354457"
---
# <a name="local-spatial-anchors-in-unreal"></a><span data-ttu-id="05fd2-104">Âncoras Espaciais locais no Unreal</span><span class="sxs-lookup"><span data-stu-id="05fd2-104">Local Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="05fd2-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="05fd2-105">Overview</span></span>

<span data-ttu-id="05fd2-106">As âncoras espaciais são usadas para salvar os hologramas no espaço do mundo real entre as sessões do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="05fd2-106">Spatial anchors are used to save holograms in real-world space between application sessions.</span></span> <span data-ttu-id="05fd2-107">Elas são exibidas por meio do Unreal como **ARPin** s e são salvas no repositório de âncoras do HoloLens, que é carregado em sessões futuras.</span><span class="sxs-lookup"><span data-stu-id="05fd2-107">These get surfaced through Unreal as **ARPin** s and saved in the HoloLens’ anchor store, which is loaded in future sessions.</span></span> <span data-ttu-id="05fd2-108">As âncoras locais são ideais como fallback quando não há nenhuma conectividade com a Internet.</span><span class="sxs-lookup"><span data-stu-id="05fd2-108">Local anchors are ideal as a fallback when there is no internet connectivity.</span></span>

> [!NOTE]
> <span data-ttu-id="05fd2-109">As funções de âncora do UE 4.25 estão obsoletas na versão 4.26 e devem ser substituídas por outras mais recentes.</span><span class="sxs-lookup"><span data-stu-id="05fd2-109">Anchor functions from UE 4.25 are obsolete in 4.26 and should be replaced with newer ones.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="05fd2-110">Elas são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem.</span><span class="sxs-lookup"><span data-stu-id="05fd2-110">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="05fd2-111">Se você pretende usar os serviços de nuvem do Azure para armazenar suas âncoras, temos um documento que pode orientar você na integração das [Âncoras Espaciais do Azure](unreal-azure-spatial-anchors.md).</span><span class="sxs-lookup"><span data-stu-id="05fd2-111">If you're looking to use Azure cloud services to store your anchors, we have a document that can walk you through integrating [Azure Spatial Anchors](unreal-azure-spatial-anchors.md).</span></span> <span data-ttu-id="05fd2-112">Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.</span><span class="sxs-lookup"><span data-stu-id="05fd2-112">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="checking-the-anchor-store"></a><span data-ttu-id="05fd2-113">Como verificar o repositório de âncoras</span><span class="sxs-lookup"><span data-stu-id="05fd2-113">Checking the anchor store</span></span>

<span data-ttu-id="05fd2-114">Antes de salvar ou carregar âncoras, você precisa verificar se o repositório de âncoras está pronto.</span><span class="sxs-lookup"><span data-stu-id="05fd2-114">Before saving or loading anchors, you need to check if the anchor store is ready.</span></span>  <span data-ttu-id="05fd2-115">A tentativa de chamar qualquer uma das funções de âncora do HoloLens antes que o repositório de âncora esteja pronto não terá sucesso.</span><span class="sxs-lookup"><span data-stu-id="05fd2-115">Calling any of the HoloLens anchor functions before the anchor store is ready will not succeed.</span></span>  

[!INCLUDE[](includes/tabs-sa-1.md)]

## <a name="saving-anchors"></a><span data-ttu-id="05fd2-116">Como salvar âncoras</span><span class="sxs-lookup"><span data-stu-id="05fd2-116">Saving anchors</span></span>

<span data-ttu-id="05fd2-117">Quando o aplicativo tem um componente que precisa ser fixado no mundo, ele pode ser salvo no repositório de âncoras com a seguinte sequência:</span><span class="sxs-lookup"><span data-stu-id="05fd2-117">Once the application has a component that needs to be pinned to the world, it can be saved to the anchor store with the following sequence:</span></span> 

[!INCLUDE[](includes/tabs-sa-2.md)]

<span data-ttu-id="05fd2-118">Passo a passo detalhado:</span><span class="sxs-lookup"><span data-stu-id="05fd2-118">Breaking this down:</span></span>
1. <span data-ttu-id="05fd2-119">Gere um ator em um local conhecido.</span><span class="sxs-lookup"><span data-stu-id="05fd2-119">Spawn an actor at a known location.</span></span>
2. <span data-ttu-id="05fd2-120">Crie um **ARPin** com esse local e um nome com base na classe do ator.</span><span class="sxs-lookup"><span data-stu-id="05fd2-120">Create an **ARPin** with that location and a name based on the actor’s class.</span></span> 
3. <span data-ttu-id="05fd2-121">Adicione o ator ao **ARPin** e salve o marcador no repositório de âncoras do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="05fd2-121">Add the actor to the **ARPin** and save the pin to the HoloLens anchor store.</span></span>  
    * <span data-ttu-id="05fd2-122">O nome da âncora que você escolhe, que neste exemplo é o carimbo de data/hora atual, precisa ser exclusivo.</span><span class="sxs-lookup"><span data-stu-id="05fd2-122">The anchor name you choose must be unique, which in this example is the current timestamp.</span></span> 

4. <span data-ttu-id="05fd2-123">Se a âncora for salva com êxito no repositório de âncoras, você poderá inspecioná-la no portal do dispositivo do HoloLens em **Sistema > Gerenciador de mapas > Arquivos de Âncora Salvos no Dispositivo**.</span><span class="sxs-lookup"><span data-stu-id="05fd2-123">If the anchor is successfully saved to the anchor store, you can be inspect it in the HoloLens device portal under **System > Map manager > Anchor Files Saved On Device**.</span></span> 

## <a name="loading-anchors"></a><span data-ttu-id="05fd2-124">Como carregar âncoras</span><span class="sxs-lookup"><span data-stu-id="05fd2-124">Loading anchors</span></span>

<span data-ttu-id="05fd2-125">Quando um aplicativo é iniciado, é possível usar o blueprint a seguir para restaurar os componentes aos respectivos locais de âncora:</span><span class="sxs-lookup"><span data-stu-id="05fd2-125">When an application starts, you can use the following blueprint to restore components to their anchor locations:</span></span>

[!INCLUDE[](includes/tabs-sa-3.md)]

<span data-ttu-id="05fd2-126">Passo a passo detalhado:</span><span class="sxs-lookup"><span data-stu-id="05fd2-126">Breaking this down:</span></span>
1. <span data-ttu-id="05fd2-127">Itere por todas as âncoras no repositório de âncoras.</span><span class="sxs-lookup"><span data-stu-id="05fd2-127">Iterate over all of the anchors in the anchor store.</span></span> 
2. <span data-ttu-id="05fd2-128">Gere um ator na identidade.</span><span class="sxs-lookup"><span data-stu-id="05fd2-128">Spawn an actor at identity.</span></span>
3. <span data-ttu-id="05fd2-129">Fixe esse ator no **ARPin** do repositório de âncoras.</span><span class="sxs-lookup"><span data-stu-id="05fd2-129">Pin that actor to the **ARPin** from the anchor store.</span></span>  

    * <span data-ttu-id="05fd2-130">É importante gerar o ator na identidade, uma vez que a âncora é responsável por reposicionar o holograma no mundo com base no local em que ele foi salvo.</span><span class="sxs-lookup"><span data-stu-id="05fd2-130">It's important to spawn the actor at identity since the anchor is responsible for repositioning the hologram in the world based on where it was saved.</span></span> <span data-ttu-id="05fd2-131">Transformações adicionadas aqui adicionarão um deslocamento à âncora.</span><span class="sxs-lookup"><span data-stu-id="05fd2-131">Any transform added here will add an offset to the anchor.</span></span> 

<span data-ttu-id="05fd2-132">A ID da âncora também é consultada para que atores diferentes possam ser gerados dependendo do nome salvo da âncora.</span><span class="sxs-lookup"><span data-stu-id="05fd2-132">The anchor ID is also queried so that different actors can be spawned depending on the anchor’s saved name.</span></span> 

## <a name="removing-anchors"></a><span data-ttu-id="05fd2-133">Como remover âncoras</span><span class="sxs-lookup"><span data-stu-id="05fd2-133">Removing anchors</span></span> 

<span data-ttu-id="05fd2-134">Quando você terminar de usar uma âncora, poderá limpar âncoras individuais ou o repositório de âncoras inteiro com os componentes **Remover ARPin do Repositório WMRAnchor** e **Remover Todos os ARPins do Repositório WMRAnchor**.</span><span class="sxs-lookup"><span data-stu-id="05fd2-134">When you're done with an anchor you can clear individual anchors or the entire anchor store with the **Remove ARPin from WMRAnchor Store** and **Remove All ARPins from WMRAnchor Store** components.</span></span>

[!INCLUDE[](includes/tabs-sa-4.md)]

> [!NOTE]
> <span data-ttu-id="05fd2-135">Tenha em mente que as Âncoras Espaciais ainda estão na versão beta, portanto, lembre-se de conferir este material novamente para obter informações e recursos atualizados.</span><span class="sxs-lookup"><span data-stu-id="05fd2-135">Bear in mind that Spatial Anchors are still in Beta, so be sure to check back for updated information and features.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="05fd2-136">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="05fd2-136">Next Development Checkpoint</span></span>

<span data-ttu-id="05fd2-137">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="05fd2-137">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="05fd2-138">A partir daí, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="05fd2-138">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="05fd2-139">Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="05fd2-139">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)

<span data-ttu-id="05fd2-140">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="05fd2-140">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="05fd2-141">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="05fd2-141">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="05fd2-142">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="05fd2-142">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="05fd2-143">Veja também</span><span class="sxs-lookup"><span data-stu-id="05fd2-143">See also</span></span>
* [<span data-ttu-id="05fd2-144">Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="05fd2-144">Azure Spatial Anchors</span></span>](unreal-azure-spatial-anchors.md)
* [<span data-ttu-id="05fd2-145">Âncoras espaciais</span><span class="sxs-lookup"><span data-stu-id="05fd2-145">Spatial anchors</span></span>](../../design/spatial-anchors.md)
* [<span data-ttu-id="05fd2-146">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="05fd2-146">Coordinate systems</span></span>](../../design/coordinate-systems.md)
