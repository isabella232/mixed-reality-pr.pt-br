---
title: Observador de malha de objeto espacial
description: Documentação sobre o observador de malha espacial no MRTK
author: davidkline-ms
ms.author: davidkl
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 51963fca4fa76340089b84e400f2882763977f72
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144451"
---
# <a name="configuring-mesh-observers-for-the-editor"></a><span data-ttu-id="c42ae-104">Configurando os observadores de malha para o editor</span><span class="sxs-lookup"><span data-stu-id="c42ae-104">Configuring mesh observers for the editor</span></span>

<span data-ttu-id="c42ae-105">Uma maneira conveniente de fornecer dados de malha de ambiente no editor do Unity é usar a [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) classe.</span><span class="sxs-lookup"><span data-stu-id="c42ae-105">A convenient way to provide environment mesh data in the Unity editor is to use the [`SpatialObjectMeshObserver`](xref:Microsoft.MixedReality.Toolkit.SpatialObjectMeshObserver.SpatialObjectMeshObserver) class.</span></span> <span data-ttu-id="c42ae-106">O *observador de malha de objeto espacial* é um provedor de dados somente editor para o [sistema de conscientização espacial](spatial-awareness-getting-started.md) que permite a importação de dados de modelo 3D para representar uma malha espacial.</span><span class="sxs-lookup"><span data-stu-id="c42ae-106">The *Spatial Object Mesh Observer* is an editor-only data provider for the [Spatial Awareness system](spatial-awareness-getting-started.md) that enables importing 3D model data to represent a spatial mesh.</span></span> <span data-ttu-id="c42ae-107">Um uso comum do *observador de malha de objetos espaciais* é importar dados verificados por meio de um Microsoft HoloLens para testar como uma experiência se adapta a diferentes ambientes no Unity.</span><span class="sxs-lookup"><span data-stu-id="c42ae-107">One common use of the *Spatial Object Mesh Observer* is to import data scanned via a Microsoft HoloLens to test how an experience adapts to different environments from within Unity.</span></span>

## <a name="getting-started"></a><span data-ttu-id="c42ae-108">Introdução</span><span class="sxs-lookup"><span data-stu-id="c42ae-108">Getting started</span></span>

<span data-ttu-id="c42ae-109">Este guia explicará a configuração de um *observador de malha de objeto espacial*.</span><span class="sxs-lookup"><span data-stu-id="c42ae-109">This guide will walk through setting up a *Spatial Object Mesh Observer*.</span></span> <span data-ttu-id="c42ae-110">Há três etapas principais para habilitar esse recurso.</span><span class="sxs-lookup"><span data-stu-id="c42ae-110">There are three key steps to enable this feature.</span></span>

1. <span data-ttu-id="c42ae-111">Adicionar um *observador de malha de objeto espacial* ao perfil do sistema de conscientização espacial</span><span class="sxs-lookup"><span data-stu-id="c42ae-111">Add a *Spatial Object Mesh Observer* to the Spatial Awareness system profile</span></span>
1. <span data-ttu-id="c42ae-112">Definir o objeto de dados de malha do ambiente</span><span class="sxs-lookup"><span data-stu-id="c42ae-112">Set the Environment Mesh Data object</span></span>
1. [<span data-ttu-id="c42ae-113">Configurar o restante das propriedades do perfil de observador de malha</span><span class="sxs-lookup"><span data-stu-id="c42ae-113">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

### <a name="set-up-a-spatial-object-mesh-observer-profile"></a><span data-ttu-id="c42ae-114">Configurar um perfil de *observador de malha de objeto espacial*</span><span class="sxs-lookup"><span data-stu-id="c42ae-114">Set up a *spatial object mesh observer* profile</span></span>

1. <span data-ttu-id="c42ae-115">Selecione o perfil de configuração do *Kit de ferramentas de realidade misturada* desejado ou selecione o objeto de *Kit de ferramentas do reality*</span><span class="sxs-lookup"><span data-stu-id="c42ae-115">Select the desired *Mixed Reality Toolkit* configuration profile or select the *Mixed Reality Toolkit* object in scene</span></span>
1. <span data-ttu-id="c42ae-116">Abrir ou expandir a guia *sistema de conscientização espacial*</span><span class="sxs-lookup"><span data-stu-id="c42ae-116">Open or expand the *Spatial Awareness System* tab</span></span>
1. <span data-ttu-id="c42ae-117">Clique no botão *"Adicionar observador espacial"*</span><span class="sxs-lookup"><span data-stu-id="c42ae-117">Click on *"Add Spatial Observer"* button</span></span>

    ![Adicionar observador espacial](../images/spatial-awareness/AddObserver.png)

1. <span data-ttu-id="c42ae-119">Selecione o tipo de *SpatialObjectMeshObserver*</span><span class="sxs-lookup"><span data-stu-id="c42ae-119">Select the *SpatialObjectMeshObserver* type</span></span>

    ![Selecionar observador de malha de objeto espacial](../images/spatial-awareness/SelectObjectObserver.png)

1. <span data-ttu-id="c42ae-121">Selecione o *objeto de malha espacial* desejado.</span><span class="sxs-lookup"><span data-stu-id="c42ae-121">Select the desired *Spatial Mesh Object*.</span></span> <span data-ttu-id="c42ae-122">Por padrão, o observador é configurado com um modelo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c42ae-122">By default, the observer is configured with an example model.</span></span> <span data-ttu-id="c42ae-123">Esse modelo foi criado usando um Microsoft HoloLens, mas é possível [criar um novo objeto de malha de digitalização](#acquiring-environment-scans).</span><span class="sxs-lookup"><span data-stu-id="c42ae-123">This model was created using a Microsoft HoloLens but it is possible to [create a new scan mesh object](#acquiring-environment-scans).</span></span>
1. [<span data-ttu-id="c42ae-124">Configurar o restante das propriedades do perfil Observador de Malha</span><span class="sxs-lookup"><span data-stu-id="c42ae-124">Configure rest of the Mesh Observer profile properties</span></span>](configuring-spatial-awareness-mesh-observer.md)

    ![Selecionar o objeto de malha](../images/spatial-awareness/ObjectObserverProfile.png)

### <a name="spatial-object-mesh-observer-profile-notes"></a><span data-ttu-id="c42ae-126">Notas de perfil do observador da malha de objeto espacial</span><span class="sxs-lookup"><span data-stu-id="c42ae-126">Spatial object mesh observer profile notes</span></span>

<span data-ttu-id="c42ae-127">Como o *Observador* de Malha de Objeto Espacial carrega dados de um modelo 3D, ele não segue algumas das configurações de observador de malha padrão descritas abaixo.</span><span class="sxs-lookup"><span data-stu-id="c42ae-127">Since the *Spatial Object Mesh Observer* loads data from a 3D model, it does not honor some of the standard mesh observer settings which are outlined below.</span></span>

<span data-ttu-id="c42ae-128">**Intervalo de atualização**</span><span class="sxs-lookup"><span data-stu-id="c42ae-128">**Update Interval**</span></span>

<span data-ttu-id="c42ae-129">O  *Observador de Malha de Objeto Espacial* envia todas as malhas para um aplicativo quando o modelo é carregado.</span><span class="sxs-lookup"><span data-stu-id="c42ae-129">The  *Spatial Object Mesh Observer* sends all meshes to an application when the model is loaded.</span></span> <span data-ttu-id="c42ae-130">Ele não simula deltas de tempo entre atualizações.</span><span class="sxs-lookup"><span data-stu-id="c42ae-130">It does not simulate time deltas between updates.</span></span> <span data-ttu-id="c42ae-131">Um aplicativo pode receber os eventos de malha chamando [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) e [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume) .</span><span class="sxs-lookup"><span data-stu-id="c42ae-131">An application can re-receive the mesh events by calling [`myObserver.ClearObservation()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.ClearObservations) and [`myObserver.Resume()`](xref:Microsoft.MixedReality.Toolkit.SpatialAwareness.IMixedRealitySpatialAwarenessObserver.Resume).</span></span>

<span data-ttu-id="c42ae-132">**É Observador Estacionário**</span><span class="sxs-lookup"><span data-stu-id="c42ae-132">**Is Stationary Observer**</span></span>

<span data-ttu-id="c42ae-133">O *Observador de Malha de Objeto Espacial* considera todos os objetos de malha 3D como estacionários e desconsidera a origem.</span><span class="sxs-lookup"><span data-stu-id="c42ae-133">The *Spatial Object Mesh Observer* considers all 3D mesh objects to be stationary and disregards origin.</span></span>

<span data-ttu-id="c42ae-134">**Forma e extensão do observador**</span><span class="sxs-lookup"><span data-stu-id="c42ae-134">**Observer Shape and Extents**</span></span>

<span data-ttu-id="c42ae-135">O  *Observador de Malha de Objeto Espacial* envia toda a malha 3D para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c42ae-135">The  *Spatial Object Mesh Observer* sends the entire 3D mesh to the application.</span></span> <span data-ttu-id="c42ae-136">A forma e as extensão do observador não são consideradas.</span><span class="sxs-lookup"><span data-stu-id="c42ae-136">Observer shape and extents are not considered.</span></span>

<span data-ttu-id="c42ae-137">**Nível de detalhes e triângulos/medidor cúbica**</span><span class="sxs-lookup"><span data-stu-id="c42ae-137">**Level of Detail and Triangles / Cubic Meter**</span></span>

<span data-ttu-id="c42ae-138">O Observador não tenta encontrar LODs de modelo 3D ao enviar as malhas para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c42ae-138">The Observer does not attempt to find 3D model LODs when sending the meshes to the application.</span></span>

## <a name="acquiring-environment-scans"></a><span data-ttu-id="c42ae-139">Adquirir verificações de ambiente</span><span class="sxs-lookup"><span data-stu-id="c42ae-139">Acquiring environment scans</span></span>

<span data-ttu-id="c42ae-140">Esta seção descreve informações adicionais  para criar e coletar arquivos de Objeto de Malha Espacial para uso com o Observador de *Malha de Objeto Espacial*.</span><span class="sxs-lookup"><span data-stu-id="c42ae-140">This section outlines additional information to create and gather *Spatial Mesh Object* files for use with the *Spatial Object Mesh Observer*.</span></span>

### <a name="windows-device-portal"></a><span data-ttu-id="c42ae-141">Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="c42ae-141">Windows Device Portal</span></span>

<span data-ttu-id="c42ae-142">O [Portal de Dispositivos do Windows](/windows/mixed-reality/using-the-windows-device-portal) pode ser usado para baixar a malha espacial, como um arquivo .obj, de um Microsoft HoloLens dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c42ae-142">The [Windows Device Portal](/windows/mixed-reality/using-the-windows-device-portal) can be used to download the spatial mesh, as a .obj file, from a Microsoft HoloLens device.</span></span>

1. <span data-ttu-id="c42ae-143">Digitalizar simplesmente passeando e exibindo o ambiente desejado com um HoloLens</span><span class="sxs-lookup"><span data-stu-id="c42ae-143">Scan by simply walking and viewing the desired environment with a HoloLens</span></span>
1. <span data-ttu-id="c42ae-144">Conectar-se ao HoloLens usando o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="c42ae-144">Connect to the HoloLens using the Windows Device Portal</span></span>
1. <span data-ttu-id="c42ae-145">Navegar até a página *exibição 3D*</span><span class="sxs-lookup"><span data-stu-id="c42ae-145">Navigate to the *3D View* page</span></span>
1. <span data-ttu-id="c42ae-146">Clique no botão *Atualizar* na seção *mapeamento espacial*</span><span class="sxs-lookup"><span data-stu-id="c42ae-146">Click the *Update* button under *Spatial Mapping* section</span></span>
1. <span data-ttu-id="c42ae-147">Clique no botão *salvar* na seção *mapeamento espacial* para salvar o arquivo obj no PC</span><span class="sxs-lookup"><span data-stu-id="c42ae-147">Click the *Save* button under *Spatial Mapping* section to save the obj file to PC</span></span>

> [!NOTE]
> <span data-ttu-id="c42ae-148">**Arquivos HoloToolkit. Room**</span><span class="sxs-lookup"><span data-stu-id="c42ae-148">**HoloToolkit .room files**</span></span>
>
> <span data-ttu-id="c42ae-149">Muitos desenvolvedores já usaram o HoloToolkit para verificar ambientes e criar arquivos. Room.</span><span class="sxs-lookup"><span data-stu-id="c42ae-149">Many developers will have previously used HoloToolkit to scan environments and create .room files.</span></span> <span data-ttu-id="c42ae-150">O kit de ferramentas de realidade misturada agora dá suporte à importação desses arquivos como GameObjects no Unity e usá-los como *objetos de malha espacial* no observador.</span><span class="sxs-lookup"><span data-stu-id="c42ae-150">The Mixed Reality Toolkit now supports importing these files as GameObjects in Unity and use them as *Spatial Mesh Objects* in the observer.</span></span>

## <a name="see-also"></a><span data-ttu-id="c42ae-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="c42ae-151">See also</span></span>

- [<span data-ttu-id="c42ae-152">Perfis</span><span class="sxs-lookup"><span data-stu-id="c42ae-152">Profiles</span></span>](../profiles/profiles.md)
- [<span data-ttu-id="c42ae-153">Guia de configuração do perfil do reality Toolkit misto</span><span class="sxs-lookup"><span data-stu-id="c42ae-153">Mixed Reality Toolkit Profile configuration guide</span></span>](../../configuration/mixed-reality-configuration-guide.md)
- [<span data-ttu-id="c42ae-154">Introdução ao reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="c42ae-154">Spatial Awareness Getting started</span></span>](spatial-awareness-getting-started.md)
- [<span data-ttu-id="c42ae-155">Configurando observadores de malha no dispositivo</span><span class="sxs-lookup"><span data-stu-id="c42ae-155">Configuring Mesh Observers on Device</span></span>](configuring-spatial-awareness-mesh-observer.md)
- [<span data-ttu-id="c42ae-156">Configurando os observadores de malha por meio do código</span><span class="sxs-lookup"><span data-stu-id="c42ae-156">Configuring Mesh Observers via code</span></span>](usage-guide.md)
- [<span data-ttu-id="c42ae-157">Como usar o Portal de Dispositivos do Windows</span><span class="sxs-lookup"><span data-stu-id="c42ae-157">Using the Windows Device Portal</span></span>](/windows/mixed-reality/using-the-windows-device-portal)