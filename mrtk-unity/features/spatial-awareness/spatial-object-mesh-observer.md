---
title: Observador de malha de objeto espacial
description: Documentação sobre o observador de malha espacial no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: db0b2f14d0a5d65140223d3fa3f4f5324ef2ba76
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176692"
---
# <a name="spatial-object-mesh-observer"></a><span data-ttu-id="ffca8-104">Observador de malha de objeto espacial</span><span class="sxs-lookup"><span data-stu-id="ffca8-104">Spatial object mesh observer</span></span>

<span data-ttu-id="ffca8-105">Uma maneira conveniente de fornecer dados de malha de ambiente no editor do Unity é usar a [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe.</span><span class="sxs-lookup"><span data-stu-id="ffca8-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="ffca8-106">O *observador de malha de objeto espacial* é um provedor de dados somente editor para o [sistema de conscientização espacial](spatial-awareness-getting-started.md) que permite a importação de dados de modelo 3D para representar uma malha espacial.</span><span class="sxs-lookup"><span data-stu-id="ffca8-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="ffca8-107">um uso comum do *observador de malha de objetos espaciais* é importar dados verificados por meio de um Microsoft HoloLens para testar como uma experiência se adapta a diferentes ambientes de dentro do Unity.</span><span class="sxs-lookup"><span data-stu-id="ffca8-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="ffca8-108">Introdução</span><span class="sxs-lookup"><span data-stu-id="ffca8-108">Getting started</span></span>

<span data-ttu-id="ffca8-109">Este guia explicará a configuração de um *observador de malha de objeto espacial*.</span><span class="sxs-lookup"><span data-stu-id="ffca8-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="ffca8-110">Há três etapas principais para habilitar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="ffca8-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="ffca8-111">Adicionar um *observador de malha de objeto espacial* ao perfil do sistema de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="ffca8-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="ffca8-112">Definir o objeto de dados de malha do ambiente</span><span class="sxs-lookup"><span data-stu-id="ffca8-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="ffca8-113">Configurar o restante das propriedades do perfil de observador de malha</span><span class="sxs-lookup"><span data-stu-id="ffca8-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="ffca8-114">Configurar um perfil de *observador de malha de objeto espacial*</span><span class="sxs-lookup"><span data-stu-id="ffca8-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="ffca8-115">selecione o perfil de configuração *Toolkit realidade misturada* desejada ou selecione o objeto de *Toolkit realidade misturada* em cena</span><span class="sxs-lookup"><span data-stu-id="ffca8-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="ffca8-116">Abrir ou expandir a guia *sistema de conscientização espacial*</span><span class="sxs-lookup"><span data-stu-id="ffca8-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="ffca8-117">Clique no botão *"Adicionar observador espacial"*</span><span class="sxs-lookup"><span data-stu-id="ffca8-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Adicionar observador espacial](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="ffca8-119">Selecione o tipo de *SpatialObjectMeshObserver*</span><span class="sxs-lookup"><span data-stu-id="ffca8-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Selecionar observador de malha de objeto espacial](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="ffca8-121">Selecione o *objeto de malha espacial* desejado.</span><span class="sxs-lookup"><span data-stu-id="ffca8-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="ffca8-122">Por padrão, o observador é configurado com um modelo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="ffca8-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="ffca8-123">esse modelo foi criado usando um Microsoft HoloLens, mas é possível [criar um novo objeto de malha de digitalização](#acquiring-environment-scans).</span><span class="sxs-lookup"><span data-stu-id="ffca8-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="ffca8-124">Configurar o restante das propriedades do perfil de observador de malha</span><span class="sxs-lookup"><span data-stu-id="ffca8-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![Selecionar o objeto de malha](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="ffca8-126">Notas de perfil do observador de malha de objetos espaciais</span><span class="sxs-lookup"><span data-stu-id="ffca8-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="ffca8-127">Como o *observador de malha de objeto espacial* carrega dados de um modelo 3D, ele não respeita algumas das configurações de observador de malha padrão que são descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="ffca8-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="ffca8-128">**Intervalo de atualização**</span><span class="sxs-lookup"><span data-stu-id="ffca8-128">**Update Interval**</span></span>

<span data-ttu-id="ffca8-129">O  *observador de malha de objeto espacial* envia todas as malhas para um aplicativo quando o modelo é carregado.</span><span class="sxs-lookup"><span data-stu-id="ffca8-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="ffca8-130">Ele não simula os deltas de tempo entre as atualizações.</span><span class="sxs-lookup"><span data-stu-id="ffca8-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="ffca8-131">Um aplicativo pode receber novamente os eventos de malha chamando [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) e [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="ffca8-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="ffca8-132">**É observador estacionário**</span><span class="sxs-lookup"><span data-stu-id="ffca8-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="ffca8-133">O *observador de malha de objetos espaciais* considera que todos os objetos de malha 3D sejam estáticos e desconsideram a origem.</span><span class="sxs-lookup"><span data-stu-id="ffca8-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="ffca8-134">**Formas e extensões do observador**</span><span class="sxs-lookup"><span data-stu-id="ffca8-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="ffca8-135">O  *observador de malha de objeto espacial* envia a malha 3D inteira para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ffca8-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="ffca8-136">A forma e as extensões do observador não são consideradas.</span><span class="sxs-lookup"><span data-stu-id="ffca8-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="ffca8-137">**Nível de detalhe e triângulos/medidor cúbico**</span><span class="sxs-lookup"><span data-stu-id="ffca8-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="ffca8-138">O observador não tenta localizar o modelo 3D LODs ao enviar as malhas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ffca8-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="ffca8-139">Adquirindo verificações de ambiente</span><span class="sxs-lookup"><span data-stu-id="ffca8-139">Acquiring environment scans</span></span>

<span data-ttu-id="ffca8-140">Esta seção descreve informações adicionais para criar e coletar arquivos de *objeto de malha espacial* para uso com o *observador de malha de objeto espacial*.</span><span class="sxs-lookup"><span data-stu-id="ffca8-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="ffca8-141">Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="ffca8-141">Windows Device Portal</span></span>

<span data-ttu-id="ffca8-142">o [Portal do dispositivo Windows](/windows/mixed-reality/using-the-windows-device-portal) pode ser usado para baixar a malha espacial, como um arquivo. obj, de um dispositivo Microsoft HoloLens.</span><span class="sxs-lookup"><span data-stu-id="ffca8-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="ffca8-143">Examine simplesmente movimentando e exibindo o ambiente desejado com um HoloLens</span><span class="sxs-lookup"><span data-stu-id="ffca8-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="ffca8-144">Conexão ao HoloLens usando o Portal do dispositivo Windows</span><span class="sxs-lookup"><span data-stu-id="ffca8-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="ffca8-145">Navegar até a página *exibição 3D*</span><span class="sxs-lookup"><span data-stu-id="ffca8-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="ffca8-146">Clique no botão *Atualizar* na seção *mapeamento espacial*</span><span class="sxs-lookup"><span data-stu-id="ffca8-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="ffca8-147">Clique no botão *salvar* na seção *mapeamento espacial* para salvar o arquivo obj no PC</span><span class="sxs-lookup"><span data-stu-id="ffca8-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="ffca8-148">**Arquivos HoloToolkit. Room**</span><span class="sxs-lookup"><span data-stu-id="ffca8-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="ffca8-149">Muitos desenvolvedores já usaram o HoloToolkit para verificar ambientes e criar arquivos. Room.</span><span class="sxs-lookup"><span data-stu-id="ffca8-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="ffca8-150">a realidade misturada Toolkit agora dá suporte à importação desses arquivos como GameObjects no Unity e usá-los como *objetos de malha espacial* no observador.</span><span class="sxs-lookup"><span data-stu-id="ffca8-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="ffca8-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="ffca8-151">See also</span></span>

- [<span data-ttu-id="ffca8-152">Perfis</span><span class="sxs-lookup"><span data-stu-id="ffca8-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="ffca8-153">guia de configuração do perfil da realidade mista Toolkit</span><span class="sxs-lookup"><span data-stu-id="ffca8-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="ffca8-154">Introdução ao reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="ffca8-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="ffca8-155">Configurando observadores de malha no dispositivo</span><span class="sxs-lookup"><span data-stu-id="ffca8-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="ffca8-156">Configurando os observadores de malha por meio do código</span><span class="sxs-lookup"><span data-stu-id="ffca8-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="ffca8-157">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="ffca8-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)
