---
title: Mapeamento espacial no Unity
description: Saiba como usar e gerenciar a renderização e a união com a geometria do mundo real ao seu redor em aplicativos de realidade misturada do Unity.
author: davidkline-ms
ms.author: davidkl
ms.date: 03/21/2018
ms.topic: article
keywords: Unity, mapeamento espacial, renderador, colisor, malha, verificação, componente, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: fa571a13ce192b29b2a35033b55061f3ffb707da
ms.sourcegitcommit: ec80ef1e496bf0b17a161735535517e87ffdd364
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/25/2021
ms.locfileid: "110351774"
---
# <a name="spatial-mapping-in-unity"></a><span data-ttu-id="718db-104">Mapeamento espacial no Unity</span><span class="sxs-lookup"><span data-stu-id="718db-104">Spatial mapping in Unity</span></span>

<span data-ttu-id="718db-105">[O mapeamento](../../design/spatial-mapping.md) espacial permite recuperar malhas de triângulo que representam as superfícies no mundo em torno de um dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="718db-105">[spatial mapping](../../design/spatial-mapping.md) lets you retrieve triangle meshes that represent the surfaces in the world around a HoloLens device.</span></span> <span data-ttu-id="718db-106">Você pode usar dados de superfície para posicionamento, oclusão e análise de sala para dar aos seus projetos do Unity uma experiência extra de imersão.</span><span class="sxs-lookup"><span data-stu-id="718db-106">You can use surface data for placement, occlusion, and room analysis to give your Unity projects an extra dose of immersion.</span></span>

<span data-ttu-id="718db-107">O Unity inclui suporte completo para mapeamento espacial, que é exposto aos desenvolvedores das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="718db-107">Unity includes full support for spatial mapping, which is exposed to developers in the following ways:</span></span>

1. <span data-ttu-id="718db-108">Componentes de mapeamento espacial disponíveis no MixedRealityToolkit, que fornecem um caminho conveniente e rápido para começar a usar o mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="718db-108">Spatial mapping components available in the MixedRealityToolkit, which provide a convenient and rapid path for getting started with spatial mapping</span></span>
2. <span data-ttu-id="718db-109">APIs de mapeamento espacial de nível inferior, que fornecem controle total e permitem uma personalização mais sofisticada específica do aplicativo</span><span class="sxs-lookup"><span data-stu-id="718db-109">Lower-level spatial mapping APIs, which provide full control and enable more sophisticated application-specific customization</span></span>

<span data-ttu-id="718db-110">Para usar o mapeamento espacial em seu aplicativo, a funcionalidade spatialPerception precisa ser definida em seu AppxManifest.</span><span class="sxs-lookup"><span data-stu-id="718db-110">To use spatial mapping in your app, the spatialPerception capability needs to be set in your AppxManifest.</span></span>

## <a name="device-support"></a><span data-ttu-id="718db-111">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="718db-111">Device support</span></span>

| <span data-ttu-id="718db-112">Recurso</span><span class="sxs-lookup"><span data-stu-id="718db-112">Feature</span></span> | [<span data-ttu-id="718db-113">HoloLens (primeira geração)</span><span class="sxs-lookup"><span data-stu-id="718db-113">HoloLens (first gen)</span></span>](/hololens/hololens1-hardware) | [<span data-ttu-id="718db-114">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="718db-114">HoloLens 2</span></span>](/hololens/hololens2-hardware) | [<span data-ttu-id="718db-115">Headsets imersivos</span><span class="sxs-lookup"><span data-stu-id="718db-115">Immersive headsets</span></span>](../../discover/immersive-headset-hardware-details.md) |
| ---- | ---- | ---- | ---- |
| <span data-ttu-id="718db-116">mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="718db-116">Spatial mapping</span></span> | <span data-ttu-id="718db-117">✔️</span><span class="sxs-lookup"><span data-stu-id="718db-117">✔️</span></span> | <span data-ttu-id="718db-118">✔️</span><span class="sxs-lookup"><span data-stu-id="718db-118">✔️</span></span> | ❌ |

## <a name="setting-the-spatialperception-capability"></a><span data-ttu-id="718db-119">Definindo a funcionalidade SpatialPerception</span><span class="sxs-lookup"><span data-stu-id="718db-119">Setting the SpatialPerception capability</span></span>

<span data-ttu-id="718db-120">Para que um aplicativo consuma dados de mapeamento espacial, a funcionalidade SpatialPerception deve ser habilitada.</span><span class="sxs-lookup"><span data-stu-id="718db-120">In order for an app to consume spatial mapping data, the SpatialPerception capability must be enabled.</span></span>

<span data-ttu-id="718db-121">Como habilitar a funcionalidade SpatialPerception:</span><span class="sxs-lookup"><span data-stu-id="718db-121">How to enable the SpatialPerception capability:</span></span>

1. <span data-ttu-id="718db-122">No Editor do Unity, abra o **painel "Configurações** do Player" (Editar > Configurações do Projeto > Player)</span><span class="sxs-lookup"><span data-stu-id="718db-122">In the Unity Editor, open the **"Player Settings"** pane (Edit > Project Settings > Player)</span></span>
2. <span data-ttu-id="718db-123">Selecione na **guia "Windows Store"**</span><span class="sxs-lookup"><span data-stu-id="718db-123">Select on the **"Windows Store"** tab</span></span>
3. <span data-ttu-id="718db-124">Expanda **"Configurações de Publicação"** e verifique a **funcionalidade "SpatialPerception"** na **lista "Funcionalidades"**</span><span class="sxs-lookup"><span data-stu-id="718db-124">Expand **"Publishing Settings"** and check the **"SpatialPerception"** capability in the **"Capabilities"** list</span></span>

> [!NOTE]
> <span data-ttu-id="718db-125">Se você já tiver exportado seu projeto do Unity para uma solução Visual Studio, precisará exportar para uma nova pasta ou definir manualmente essa funcionalidade no [AppxManifest](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability)no Visual Studio .</span><span class="sxs-lookup"><span data-stu-id="718db-125">If you have already exported your Unity project to a Visual Studio solution, you will need to either export to a new folder or manually [set this capability in the AppxManifest in Visual Studio](../native/spatial-mapping-in-directx.md#set-up-your-app-to-use-the-spatialperception-capability).</span></span>

<span data-ttu-id="718db-126">O mapeamento espacial também requer um MaxVersionTested de pelo menos 10.0.10586.0:</span><span class="sxs-lookup"><span data-stu-id="718db-126">Spatial mapping also requires a MaxVersionTested of at least 10.0.10586.0:</span></span>

1. <span data-ttu-id="718db-127">No Visual Studio, clique com o botão direito do mouse **em Package.appxmanifest** no Gerenciador de Soluções e selecione **Exibir Código**</span><span class="sxs-lookup"><span data-stu-id="718db-127">In Visual Studio, right-click on **Package.appxmanifest** in the Solution Explorer and select **View Code**</span></span>
2. <span data-ttu-id="718db-128">Encontre a linha que especifica **TargetDeviceFamily** e altere **MaxVersionTested="10.0.10240.0"** para **MaxVersionTested="10.0.10586.0"**</span><span class="sxs-lookup"><span data-stu-id="718db-128">Find the line specifying **TargetDeviceFamily** and change **MaxVersionTested="10.0.10240.0"** to **MaxVersionTested="10.0.10586.0"**</span></span>
3. <span data-ttu-id="718db-129">**Salve** o Package.appxmanifest.</span><span class="sxs-lookup"><span data-stu-id="718db-129">**Save** the Package.appxmanifest.</span></span>

## <a name="getting-started-with-unitys-built-in-spatial-mapping-components"></a><span data-ttu-id="718db-130">Como começar a trabalhar com os componentes de mapeamento espacial internos do Unity</span><span class="sxs-lookup"><span data-stu-id="718db-130">Getting started with Unity's built-in spatial mapping components</span></span>

<span data-ttu-id="718db-131">O Unity oferece dois componentes para adicionar facilmente o mapeamento espacial ao seu aplicativo, o **Renderador** de Mapeamento Espacial e **o Colisor de Mapeamento Espacial.**</span><span class="sxs-lookup"><span data-stu-id="718db-131">Unity offers two components for easily adding spatial mapping to your app, **Spatial Mapping Renderer** and **Spatial Mapping Collider**.</span></span>

### <a name="spatial-mapping-renderer"></a><span data-ttu-id="718db-132">Renderdor de Mapeamento Espacial</span><span class="sxs-lookup"><span data-stu-id="718db-132">Spatial Mapping Renderer</span></span>

<span data-ttu-id="718db-133">O Renderador de Mapeamento Espacial permite a visualização da malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="718db-133">The Spatial Mapping Renderer allows for visualization of the spatial mapping mesh.</span></span>

![Renderdor de Mapeamento Espacial no Unity](images/spatialmappingrenderer.png)

### <a name="spatial-mapping-collider"></a><span data-ttu-id="718db-135">Colisor de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="718db-135">Spatial Mapping Collider</span></span>

<span data-ttu-id="718db-136">O Colisor de Mapeamento Espacial permite a interação de conteúdo holográfico (ou caractere), como física, com a malha de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="718db-136">The Spatial Mapping Collider allows for holographic content (or character) interaction, such as physics, with the spatial mapping mesh.</span></span>

![Colisor de mapeamento espacial no Unity](images/spatialmappingcollider.png)

### <a name="using-the-built-in-spatial-mapping-components"></a><span data-ttu-id="718db-138">Usando os componentes internos de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="718db-138">Using the built-in spatial mapping components</span></span>

<span data-ttu-id="718db-139">Você pode adicionar ambos os componentes ao seu aplicativo se quiser visualizar e interagir com superfícies físicas.</span><span class="sxs-lookup"><span data-stu-id="718db-139">You may add both components to your app if you'd like to both visualize and interact with physical surfaces.</span></span>

<span data-ttu-id="718db-140">Para usar esses dois componentes em seu aplicativo Unity:</span><span class="sxs-lookup"><span data-stu-id="718db-140">To use these two components in your Unity app:</span></span>

1. <span data-ttu-id="718db-141">Selecione um GameObject no centro da área na qual você gostaria de detectar malhas de superfície espacial.</span><span class="sxs-lookup"><span data-stu-id="718db-141">Select a GameObject at the center of the area in which you'd like to detect spatial surface meshes.</span></span>
2. <span data-ttu-id="718db-142">Na janela Inspetor, Adicione **Colisor**  >  **de Mapeamento Espacial XR** do Componente  >  **ou** **Renderador de Mapeamento Espacial**.</span><span class="sxs-lookup"><span data-stu-id="718db-142">In the Inspector window, **Add Component** > **XR** > **Spatial Mapping Collider** or **Spatial Mapping Renderer**.</span></span>

<span data-ttu-id="718db-143">Você pode encontrar mais detalhes sobre como usar esses componentes no <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">site de documentação do Unity</a>.</span><span class="sxs-lookup"><span data-stu-id="718db-143">You can find more details on how to use these components at the <a href="https://docs.unity3d.com/Manual/SpatialMappingComponents.html" target="_blank">Unity documentation site</a>.</span></span>

### <a name="going-beyond-the-built-in-spatial-mapping-components"></a><span data-ttu-id="718db-144">Ir além dos componentes internos de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="718db-144">Going beyond the built-in spatial mapping components</span></span>

<span data-ttu-id="718db-145">Esses componentes facilitam a começar a trabalhar com o Mapeamento Espacial.</span><span class="sxs-lookup"><span data-stu-id="718db-145">These components make it drag-and-drop easy to get started with Spatial Mapping.</span></span>  <span data-ttu-id="718db-146">Quando você quiser ir além, há dois caminhos principais a serem explorados:</span><span class="sxs-lookup"><span data-stu-id="718db-146">When you want to go further, there are two main paths to explore:</span></span>

* <span data-ttu-id="718db-147">Para fazer seu próprio processamento de malha de nível inferior, consulte a seção abaixo sobre a API de script de mapeamento espacial de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="718db-147">To do your own lower-level mesh processing, see the section below about the low-level Spatial Mapping script API.</span></span>
* <span data-ttu-id="718db-148">Para fazer uma análise de malha de nível superior, consulte a seção abaixo sobre a biblioteca SpatialUnderstanding no <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit.</a></span><span class="sxs-lookup"><span data-stu-id="718db-148">To do higher-level mesh analysis, see the section below about the SpatialUnderstanding library in <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity/tree/htk_release/Assets/HoloToolkit/SpatialUnderstanding" target="_blank">MixedRealityToolkit</a>.</span></span>

## <a name="using-the-low-level-unity-spatial-mapping-api"></a><span data-ttu-id="718db-149">Usando a API de Mapeamento Espacial do Unity de baixo nível</span><span class="sxs-lookup"><span data-stu-id="718db-149">Using the low-level Unity Spatial Mapping API</span></span>

<span data-ttu-id="718db-150">Se você precisar de mais controle do que os componentes renderista de mapeamento espacial e colisor de mapeamento espacial oferecem, use as APIs de mapeamento espacial de baixo nível.</span><span class="sxs-lookup"><span data-stu-id="718db-150">If you need more control than the Spatial Mapping Renderer and Spatial Mapping Collider components offer, use the low-level Spatial Mapping APIs.</span></span>

<span data-ttu-id="718db-151">**Namespace:** *UnityEngine.XR.WSA*</span><span class="sxs-lookup"><span data-stu-id="718db-151">**Namespace:** *UnityEngine.XR.WSA*</span></span><br>
<span data-ttu-id="718db-152">**Tipos:** *SurfaceObserver,* *SurfaceChange,* *SurfaceData,* *SurfaceId*</span><span class="sxs-lookup"><span data-stu-id="718db-152">**Types**: *SurfaceObserver*, *SurfaceChange*, *SurfaceData*, *SurfaceId*</span></span>

<span data-ttu-id="718db-153">Descrevemos o fluxo sugerido para um aplicativo que usa as APIs de mapeamento espacial nas seções abaixo.</span><span class="sxs-lookup"><span data-stu-id="718db-153">We've outlined the suggested flow for an application that uses the spatial mapping APIs in the sections below.</span></span>

### <a name="set-up-the-surfaceobservers"></a><span data-ttu-id="718db-154">Configurar o(s) SurfaceObserver(s)</span><span class="sxs-lookup"><span data-stu-id="718db-154">Set up the SurfaceObserver(s)</span></span>

<span data-ttu-id="718db-155">Insinue um objeto SurfaceObserver para cada região de espaço definida pelo aplicativo para a qual você precisa de dados de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="718db-155">Instantiate one SurfaceObserver object for each application-defined region of space that you need spatial mapping data for.</span></span>

```cs
SurfaceObserver surfaceObserver;

private void Start()
{
    surfaceObserver = new SurfaceObserver();
}
```

<span data-ttu-id="718db-156">Especifique a região do espaço para a qual cada objeto SurfaceObserver fornecerá dados chamando SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox ou SetVolumeAsFrustum.</span><span class="sxs-lookup"><span data-stu-id="718db-156">Specify the region of space that each SurfaceObserver object will provide data for by calling either SetVolumeAsSphere, SetVolumeAsAxisAlignedBox, SetVolumeAsOrientedBox, or SetVolumeAsFrustum.</span></span> <span data-ttu-id="718db-157">Você pode redefinir a região do espaço no futuro simplesmente chamando um desses métodos novamente.</span><span class="sxs-lookup"><span data-stu-id="718db-157">You can redefine the region of space in the future by simply calling one of these methods again.</span></span>

```cs
private void Start()
{
    surfaceObserver.SetVolumeAsAxisAlignedBox(Vector3.zero, new Vector3(3, 3, 3));
}
```

<span data-ttu-id="718db-158">Ao chamar SurfaceObserver.Update(), você deve fornecer um manipulador para cada superfície espacial na região de espaço do SurfaceObserver para a que o sistema de mapeamento espacial tenha novas informações.</span><span class="sxs-lookup"><span data-stu-id="718db-158">When you call SurfaceObserver.Update(), you must provide a handler for each spatial surface in the SurfaceObserver's region of space that the spatial mapping system has new information for.</span></span> <span data-ttu-id="718db-159">O manipulador recebe, para uma superfície espacial:</span><span class="sxs-lookup"><span data-stu-id="718db-159">The handler receives, for one spatial surface:</span></span>

```cs
private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    // see Handling Surface Changes
}
```

### <a name="handling-surface-changes"></a><span data-ttu-id="718db-160">Manipulando alterações na superfície</span><span class="sxs-lookup"><span data-stu-id="718db-160">Handling Surface Changes</span></span>

<span data-ttu-id="718db-161">Há vários casos principais para lidar – adicionados e atualizados, que podem usar o mesmo caminho de código e removidos.</span><span class="sxs-lookup"><span data-stu-id="718db-161">There are several main cases to handle - added and updated, which can use the same code path, and removed.</span></span>

* <span data-ttu-id="718db-162">Nos casos adicionados e atualizados, adicionamos ou obteremos o GameObject que representa essa malha do dicionário, criaremos um struct SurfaceData com os componentes necessários e, em seguida, chamaremos RequestMeshDataAsync para preencher o GameObject com os dados e a posição da malha na cena.</span><span class="sxs-lookup"><span data-stu-id="718db-162">In the added and updated cases, we add or get the GameObject representing this mesh from the dictionary, create a SurfaceData struct with the necessary components, then call RequestMeshDataAsync to populate the GameObject with the mesh data and position in the scene.</span></span>
* <span data-ttu-id="718db-163">No caso removido, removemos o GameObject que representa essa malha do dicionário e a destrói.</span><span class="sxs-lookup"><span data-stu-id="718db-163">In the removed case, we remove the GameObject representing this mesh from the dictionary and destroy it.</span></span>

```cs
System.Collections.Generic.Dictionary<SurfaceId, GameObject> spatialMeshObjects =
    new System.Collections.Generic.Dictionary<SurfaceId, GameObject>();

private void OnSurfaceChanged(SurfaceId surfaceId, SurfaceChange changeType, Bounds bounds, System.DateTime updateTime)
{
    switch (changeType)
    {
        case SurfaceChange.Added:
        case SurfaceChange.Updated:
            if (!spatialMeshObjects.ContainsKey(surfaceId))
            {
                spatialMeshObjects[surfaceId] = new GameObject("spatial-mapping-" + surfaceId);
                spatialMeshObjects[surfaceId].transform.parent = this.transform;
                spatialMeshObjects[surfaceId].AddComponent<MeshRenderer>();
            }
            GameObject target = spatialMeshObjects[surfaceId];
            SurfaceData sd = new SurfaceData(
                // the surface id returned from the system
                surfaceId,
                // the mesh filter that is populated with the spatial mapping data for this mesh
                target.GetComponent<MeshFilter>() ?? target.AddComponent<MeshFilter>(),
                // the world anchor used to position the spatial mapping mesh in the world
                target.GetComponent<WorldAnchor>() ?? target.AddComponent<WorldAnchor>(),
                // the mesh collider that is populated with collider data for this mesh, if true is passed to bakeMeshes below
                target.GetComponent<MeshCollider>() ?? target.AddComponent<MeshCollider>(),
                // triangles per cubic meter requested for this mesh
                1000,
                // bakeMeshes - if true, the mesh collider is populated, if false, the mesh collider is empty.
                true
            );

            SurfaceObserver.RequestMeshAsync(sd, OnDataReady);
            break;
        case SurfaceChange.Removed:
            var obj = spatialMeshObjects[surfaceId];
            spatialMeshObjects.Remove(surfaceId);
            if (obj != null)
            {
                GameObject.Destroy(obj);
            }
            break;
        default:
            break;
    }
}
```

### <a name="handling-data-ready"></a><span data-ttu-id="718db-164">Manipulando dados prontos</span><span class="sxs-lookup"><span data-stu-id="718db-164">Handling Data Ready</span></span>

<span data-ttu-id="718db-165">O manipulador OnDataReady recebe um objeto SurfaceData.</span><span class="sxs-lookup"><span data-stu-id="718db-165">The OnDataReady handler receives a SurfaceData object.</span></span> <span data-ttu-id="718db-166">Os objetos WorldAnchor, MeshFilter e (opcionalmente) MeshCollider que ele contém refletem o estado mais recente da superfície espacial associada.</span><span class="sxs-lookup"><span data-stu-id="718db-166">The WorldAnchor, MeshFilter, and (optionally) MeshCollider objects it contains reflect the latest state of the associated spatial surface.</span></span> <span data-ttu-id="718db-167">Opcionalmente, analise e/ou [processe](../../design/spatial-mapping.md#mesh-processing) os dados da malha acessando o membro da Malha do objeto MeshFilter.</span><span class="sxs-lookup"><span data-stu-id="718db-167">Optionally, analyze and/or [process](../../design/spatial-mapping.md#mesh-processing) the mesh data by accessing the Mesh member of the MeshFilter object.</span></span> <span data-ttu-id="718db-168">Renderizar a superfície espacial com a malha mais recente e (opcionalmente) usá-la para colisões físicas e raycasts.</span><span class="sxs-lookup"><span data-stu-id="718db-168">Render the spatial surface with the latest mesh and (optionally) use it for physics collisions and raycasts.</span></span> <span data-ttu-id="718db-169">É importante confirmar se o conteúdo do SurfaceData não é nulo.</span><span class="sxs-lookup"><span data-stu-id="718db-169">It's important to confirm that the contents of the SurfaceData aren't null.</span></span>

### <a name="start-processing-on-updates"></a><span data-ttu-id="718db-170">Iniciar o processamento em atualizações</span><span class="sxs-lookup"><span data-stu-id="718db-170">Start processing on updates</span></span>

<span data-ttu-id="718db-171">SurfaceObserver.Update() deve ser chamado em um atraso, não em todos os quadros.</span><span class="sxs-lookup"><span data-stu-id="718db-171">SurfaceObserver.Update() should be called on a delay, not every frame.</span></span>

```cs
void Start ()
{
    StartCoroutine(UpdateLoop());
}

IEnumerator UpdateLoop()
{
    var wait = new WaitForSeconds(2.5f);
    while(true)
    {
        surfaceObserver.Update(OnSurfaceChanged);
        yield return wait;
    }
}
```

## <a name="higher-level-mesh-analysis-spatial-understanding"></a><span data-ttu-id="718db-172">Análise de malha de nível superior: Compreensão espacial</span><span class="sxs-lookup"><span data-stu-id="718db-172">Higher-level mesh analysis: Spatial Understanding</span></span>

> [!CAUTION]
> <span data-ttu-id="718db-173">O Entendimento Espacial foi preterido em favor do Entendimento [de Cena.](../../design/scene-understanding.md)</span><span class="sxs-lookup"><span data-stu-id="718db-173">Spatial Understanding has been deprecated in favor of [Scene Understanding](../../design/scene-understanding.md).</span></span>

<span data-ttu-id="718db-174">O <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit é</a> uma coleção de código utilitário para desenvolvimento holográfico criado nas APIs holográficas do Unity.</span><span class="sxs-lookup"><span data-stu-id="718db-174">The <a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a> is a collection of utility code for holographic development built on Unity's holographic APIs.</span></span>

### <a name="spatial-understanding"></a><span data-ttu-id="718db-175">Compreensão espacial</span><span class="sxs-lookup"><span data-stu-id="718db-175">Spatial Understanding</span></span>

<span data-ttu-id="718db-176">Ao colocar hologramas no mundo físico, geralmente é desejável ir além da malha e dos planos de superfície do mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="718db-176">When placing holograms in the physical world, it's often desirable to go beyond spatial mapping’s mesh and surface planes.</span></span> <span data-ttu-id="718db-177">Quando o posicionamento é feito proceduralmente, um nível mais alto de compreensão ambiental é desejável.</span><span class="sxs-lookup"><span data-stu-id="718db-177">When placement is done procedurally, a higher level of environmental understanding is desirable.</span></span> <span data-ttu-id="718db-178">Isso geralmente requer a tomada de decisões sobre o que é piso, teto e paredes.</span><span class="sxs-lookup"><span data-stu-id="718db-178">This usually requires making decisions about what is floor, ceiling, and walls.</span></span> <span data-ttu-id="718db-179">Você também tem a capacidade de otimizar em relação a um conjunto de restrições de posicionamento para determinar os melhores locais físicos para objetos holográficos.</span><span class="sxs-lookup"><span data-stu-id="718db-179">You also have the ability to optimize against a set of placement constraints to determine the most best physical locations for holographic objects.</span></span>

<span data-ttu-id="718db-180">Durante o desenvolvimento de Conker e Fragmentos, a Asobo Estúdios encarou esse problema ao desenvolver um solucionador de sala.</span><span class="sxs-lookup"><span data-stu-id="718db-180">During development of Young Conker and Fragments, Asobo Studios faced this problem head on by developing a room solver.</span></span> <span data-ttu-id="718db-181">Cada um desses jogos tinha necessidades específicas do jogo, mas compartilhavam a tecnologia de compreensão espacial principal.</span><span class="sxs-lookup"><span data-stu-id="718db-181">Each of these games had game-specific needs, but they shared core spatial understanding technology.</span></span> <span data-ttu-id="718db-182">A biblioteca HoloToolkit.SpatialUnderstanding encapsula essa tecnologia, permitindo que você encontre rapidamente espaços vazios nas paredes, coloque objetos no limite, identifique colocado para que o caractere fique e uma infinidade de outras consultas de compreensão espacial.</span><span class="sxs-lookup"><span data-stu-id="718db-182">The HoloToolkit.SpatialUnderstanding library encapsulates this technology, allowing you to quickly find empty spaces on the walls, place objects on the ceiling, identify placed for character to sit, and a myriad of other spatial understanding queries.</span></span>

<span data-ttu-id="718db-183">Todo o código-fonte está incluído, permitindo que você personalize-o de acordo com suas necessidades e compartilhe suas melhorias com a comunidade.</span><span class="sxs-lookup"><span data-stu-id="718db-183">All of the source code is included, allowing you to customize it to your needs and share your improvements with the community.</span></span> <span data-ttu-id="718db-184">O código do solucionador C++ foi envolvido em uma dll UWP e exposto ao Unity com uma queda no pré-fab contido no MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="718db-184">The code for the C++ solver has been wrapped into a UWP dll and exposed to Unity with a drop in prefab contained within the MixedRealityToolkit.</span></span>

### <a name="understanding-modules"></a><span data-ttu-id="718db-185">Noções básicas sobre módulos</span><span class="sxs-lookup"><span data-stu-id="718db-185">Understanding Modules</span></span>

<span data-ttu-id="718db-186">Há três interfaces principais expostas pelo módulo: topologia para consultas espaciais e de superfície simples, forma para detecção de objeto e o solucionador de posicionamento de objeto para posicionamento baseado em restrição de conjuntos de objetos.</span><span class="sxs-lookup"><span data-stu-id="718db-186">There are three primary interfaces exposed by the module: topology for simple surface and spatial queries, shape for object detection, and the object placement solver for constraint-based placement of object sets.</span></span> <span data-ttu-id="718db-187">Veja a descrição das duas maneiras abaixo.</span><span class="sxs-lookup"><span data-stu-id="718db-187">Each of these is described below.</span></span> <span data-ttu-id="718db-188">Além das três interfaces de módulo primário, uma interface de transmissão de raios pode ser usada para recuperar tipos de superfície marcados e uma malha personalizada do playspace watergged pode ser copiada.</span><span class="sxs-lookup"><span data-stu-id="718db-188">In addition to the three primary module interfaces, a ray casting interface can be used to retrieve tagged surface types and a custom watertight playspace mesh can be copied out.</span></span>

### <a name="ray-casting"></a><span data-ttu-id="718db-189">Ray Casting</span><span class="sxs-lookup"><span data-stu-id="718db-189">Ray Casting</span></span>

<span data-ttu-id="718db-190">Após a conclusão da verificação da sala, os rótulos são gerados internamente para superfícies como piso, teto e paredes.</span><span class="sxs-lookup"><span data-stu-id="718db-190">After the room scan is completed, labels are internally generated for surfaces like the floor, ceiling, and walls.</span></span> <span data-ttu-id="718db-191">A função recebe um raio e retorna se o raio colide com uma superfície conhecida e, nesse caso, informações sobre essa superfície na `PlayspaceRaycast` forma de um `RaycastResult` .</span><span class="sxs-lookup"><span data-stu-id="718db-191">The `PlayspaceRaycast` function takes a ray and returns if the ray collides with a known surface and if so, information about that surface in the form of a `RaycastResult`.</span></span>

```cpp
struct RaycastResult
{
    enum SurfaceTypes
    {
        Invalid,    // No intersection
        Other,
        Floor,
        FloorLike,  // Not part of the floor topology,
                    //  but close to the floor and looks like the floor
        Platform,   // Horizontal platform between the ground and
                    //  the ceiling
        Ceiling,
        WallExternal,
        WallLike,   // Not part of the external wall surface,
                    //  but vertical surface that looks like a
                    //  wall structure
    };
    SurfaceTypes SurfaceType;
    float SurfaceArea;  // Zero if unknown
                        //  (i.e. if not part of the topology analysis)
    DirectX::XMFLOAT3 IntersectPoint;
    DirectX::XMFLOAT3 IntersectNormal;
};
```

<span data-ttu-id="718db-192">Internamente, o raycast é calculado em relação à representação de voxel computada de 8 cm do playspace.</span><span class="sxs-lookup"><span data-stu-id="718db-192">Internally, the raycast is computed against the computed 8-cm cubed voxel representation of the playspace.</span></span> <span data-ttu-id="718db-193">Cada voxel contém um conjunto de elementos de superfície com dados de topologia processados (também conhecidos como surfels).</span><span class="sxs-lookup"><span data-stu-id="718db-193">Each voxel contains a set of surface elements with processed topology data (aka surfels).</span></span> <span data-ttu-id="718db-194">Os surfels contidos na célula de voxel interseccionar são comparados e a melhor combinação usada para procurar as informações de topologia.</span><span class="sxs-lookup"><span data-stu-id="718db-194">The surfels contained within the intersected voxel cell is compared and the best match used to look up the topology information.</span></span> <span data-ttu-id="718db-195">Esses dados de topologia contêm a rotulagem retornada na forma da enum "SurfaceTypes", bem como a área de superfície da superfície interseccionar.</span><span class="sxs-lookup"><span data-stu-id="718db-195">This topology data contains the labeling returned in the form of the “SurfaceTypes” enum, as well as the surface area of the intersected surface.</span></span>

<span data-ttu-id="718db-196">No exemplo do Unity, o cursor lança um raio para cada quadro.</span><span class="sxs-lookup"><span data-stu-id="718db-196">In the Unity sample, the cursor casts a ray each frame.</span></span> <span data-ttu-id="718db-197">Primeiro, em relação aos colisores do Unity.</span><span class="sxs-lookup"><span data-stu-id="718db-197">First, against Unity’s colliders.</span></span> <span data-ttu-id="718db-198">Segundo, em relação à representação mundial do módulo de compreensão.</span><span class="sxs-lookup"><span data-stu-id="718db-198">Second, against the understanding module’s world representation.</span></span> <span data-ttu-id="718db-199">E, por fim, novamente os elementos da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="718db-199">And finally, again UI elements.</span></span> <span data-ttu-id="718db-200">Nesse aplicativo, a interface do usuário obtém prioridade, em seguida, o resultado de compreensão e, por fim, os colisores do Unity.</span><span class="sxs-lookup"><span data-stu-id="718db-200">In this application, UI gets priority, next the understanding result, and lastly, Unity’s colliders.</span></span> <span data-ttu-id="718db-201">O SurfaceType é relatado como texto ao lado do cursor.</span><span class="sxs-lookup"><span data-stu-id="718db-201">The SurfaceType is reported as text next to the cursor.</span></span>

<span data-ttu-id="718db-202">![O tipo de superfície é rotulado ao lado do cursor](images/su-raycastresults-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="718db-202">![Surface type is labeled next to the cursor](images/su-raycastresults-300px.jpg)</span></span><br>
<span data-ttu-id="718db-203">*O tipo de superfície é rotulado ao lado do cursor*</span><span class="sxs-lookup"><span data-stu-id="718db-203">*Surface type is labeled next to the cursor*</span></span>

### <a name="topology-queries"></a><span data-ttu-id="718db-204">Consultas de topologia</span><span class="sxs-lookup"><span data-stu-id="718db-204">Topology Queries</span></span>

<span data-ttu-id="718db-205">Na DLL, o gerenciador de topologia lida com a rotulagem do ambiente.</span><span class="sxs-lookup"><span data-stu-id="718db-205">Within the DLL, the topology manager handles labeling of the environment.</span></span> <span data-ttu-id="718db-206">Conforme mencionado acima, grande parte dos dados é armazenada em surfels, contidos em um volume voxel.</span><span class="sxs-lookup"><span data-stu-id="718db-206">As mentioned above, much of the data is stored within surfels, contained within a voxel volume.</span></span> <span data-ttu-id="718db-207">Além disso, a estrutura "PlaySpaceInfos" é usada para armazenar informações sobre o playspace, incluindo o alinhamento do mundo (mais detalhes sobre isso abaixo), o piso e a altura do teto.</span><span class="sxs-lookup"><span data-stu-id="718db-207">In addition, the “PlaySpaceInfos” structure is used to store information about the playspace, including the world alignment (more details on this below), floor, and ceiling height.</span></span> <span data-ttu-id="718db-208">Heurística é usada para determinar piso, teto e paredes.</span><span class="sxs-lookup"><span data-stu-id="718db-208">Heuristics are used for determining floor, ceiling, and walls.</span></span> <span data-ttu-id="718db-209">Por exemplo, a maior e a menor superfície horizontal com área de superfície maior que 1 m2 é considerada o piso.</span><span class="sxs-lookup"><span data-stu-id="718db-209">For example, the largest and lowest horizontal surface with greater than 1-m2 surface area is considered the floor.</span></span>

> [!NOTE]
> <span data-ttu-id="718db-210">O caminho da câmera durante o processo de verificação também é usado nesse processo.</span><span class="sxs-lookup"><span data-stu-id="718db-210">The camera path during the scanning process is also used in this process.</span></span>

<span data-ttu-id="718db-211">Um subconjunto das consultas expostas pelo gerenciador de Topologia é exposto por meio da dll.</span><span class="sxs-lookup"><span data-stu-id="718db-211">A subset of the queries exposed by the Topology manager are exposed out through the dll.</span></span> <span data-ttu-id="718db-212">As consultas de topologia expostas são as a seguir.</span><span class="sxs-lookup"><span data-stu-id="718db-212">The exposed topology queries are as follows.</span></span>

```cpp
QueryTopology_FindPositionsOnWalls
QueryTopology_FindLargePositionsOnWalls
QueryTopology_FindLargestWall
QueryTopology_FindPositionsOnFloor
QueryTopology_FindLargestPositionsOnFloor
QueryTopology_FindPositionsSittable
```

<span data-ttu-id="718db-213">Cada uma das consultas tem um conjunto de parâmetros, específicos para o tipo de consulta.</span><span class="sxs-lookup"><span data-stu-id="718db-213">Each of the queries has a set of parameters, specific to the query type.</span></span> <span data-ttu-id="718db-214">No exemplo a seguir, o usuário especifica a altura mínima & largura do volume desejado, a altura mínima do posicionamento acima do piso e a quantidade mínima de liberação na frente do volume.</span><span class="sxs-lookup"><span data-stu-id="718db-214">In the following example, the user specifies the minimum height & width of the desired volume, minimum placement height above the floor, and the minimum amount of clearance in front of the volume.</span></span> <span data-ttu-id="718db-215">Todas as medidas estão em metros.</span><span class="sxs-lookup"><span data-stu-id="718db-215">All measurements are in meters.</span></span>

```cpp
EXTERN_C __declspec(dllexport) int QueryTopology_FindPositionsOnWalls(
    _In_ float minHeightOfWallSpace,
    _In_ float minWidthOfWallSpace,
    _In_ float minHeightAboveFloor,
    _In_ float minFacingClearance,
    _In_ int locationCount,
    _Inout_ Dll_Interface::TopologyResult* locationData)
```

<span data-ttu-id="718db-216">Cada uma dessas consultas recebe uma matriz pré-alocada de estruturas "TopologyResult".</span><span class="sxs-lookup"><span data-stu-id="718db-216">Each of these queries takes a pre-allocated array of “TopologyResult” structures.</span></span> <span data-ttu-id="718db-217">O parâmetro "locationCount" especifica o comprimento da matriz passada.</span><span class="sxs-lookup"><span data-stu-id="718db-217">The “locationCount” parameter specifies the length of the passed in array.</span></span> <span data-ttu-id="718db-218">O valor retornado informa o número de locais retornados.</span><span class="sxs-lookup"><span data-stu-id="718db-218">The return value reports the number of returned locations.</span></span> <span data-ttu-id="718db-219">Esse número nunca é maior que o passado no parâmetro "locationCount".</span><span class="sxs-lookup"><span data-stu-id="718db-219">This number is never greater than the passed in “locationCount” parameter.</span></span>

<span data-ttu-id="718db-220">O "TopologyResult" contém a posição central do volume retornado, a direção voltada (ou seja, normal) e as dimensões do espaço encontrado.</span><span class="sxs-lookup"><span data-stu-id="718db-220">The “TopologyResult” contains the center position of the returned volume, the facing direction (i.e. normal), and the dimensions of the found space.</span></span>

```cpp
struct TopologyResult
{
    DirectX::XMFLOAT3 position;
    DirectX::XMFLOAT3 normal;
    float width;
    float length;
};
```

> [!NOTE]
> <span data-ttu-id="718db-221">No exemplo do Unity, cada uma dessas consultas é vinculada a um botão no painel de interface do usuário virtual.</span><span class="sxs-lookup"><span data-stu-id="718db-221">In the Unity sample, each of these queries is linked up to a button in the virtual UI panel.</span></span> <span data-ttu-id="718db-222">O exemplo codifica os parâmetros para cada uma dessas consultas para valores razoáveis.</span><span class="sxs-lookup"><span data-stu-id="718db-222">The sample hard codes the parameters for each of these queries to reasonable values.</span></span> <span data-ttu-id="718db-223">Consulte SpaceVisualizer.cs no código de exemplo para obter mais exemplos.</span><span class="sxs-lookup"><span data-stu-id="718db-223">See SpaceVisualizer.cs in the sample code for more examples.</span></span>

### <a name="shape-queries"></a><span data-ttu-id="718db-224">Consultas de forma</span><span class="sxs-lookup"><span data-stu-id="718db-224">Shape Queries</span></span>

<span data-ttu-id="718db-225">Na dll, o analisador de forma ("ShapeAnalyzer_W") usa o analisador de topologia para corresponder às formas personalizadas definidas pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="718db-225">In the dll, the shape analyzer (“ShapeAnalyzer_W”) uses the topology analyzer to match against custom shapes defined by the user.</span></span> <span data-ttu-id="718db-226">O exemplo do Unity define um conjunto de formas e expõe os resultados por meio do menu de consulta no aplicativo, dentro da guia forma. A intenção é que o usuário possa definir suas próprias consultas de forma de objeto e usá-los, conforme necessário para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="718db-226">The Unity sample defines a set of shapes and exposes the results out through the in-app query menu, within the shape tab. The intention is that the user can define their own object shape queries and make use of those, as needed by their application.</span></span>

<span data-ttu-id="718db-227">A análise de forma funciona apenas em superfícies horizontais.</span><span class="sxs-lookup"><span data-stu-id="718db-227">The shape analysis works on horizontal surfaces only.</span></span> <span data-ttu-id="718db-228">Um diviso, por exemplo, é definido pela superfície do banco simples e pela parte superior plana do diviso.</span><span class="sxs-lookup"><span data-stu-id="718db-228">A couch, for example, is defined by the flat seat surface and the flat top of the couch back.</span></span> <span data-ttu-id="718db-229">A consulta de forma procura duas superfícies de um tamanho, altura e intervalo de aspecto específicos, com as duas superfícies alinhadas e conectadas.</span><span class="sxs-lookup"><span data-stu-id="718db-229">The shape query looks for two surfaces of a specific size, height, and aspect range, with the two surfaces aligned and connected.</span></span> <span data-ttu-id="718db-230">Usando a terminologia de APIs, a mesa do couch e a parte superior são componentes de forma e os requisitos de alinhamento são restrições de componente de forma.</span><span class="sxs-lookup"><span data-stu-id="718db-230">Using the APIs terminology, the couch seat and back top are shape components and the alignment requirements are shape component constraints.</span></span>

<span data-ttu-id="718db-231">Uma consulta de exemplo definida no exemplo do Unity (ShapeDefinition.cs), para objetos "sittable" é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="718db-231">An example query defined in the Unity sample (ShapeDefinition.cs), for “sittable” objects is as follows.</span></span>

```cs
shapeComponents = new List<ShapeComponent>()
{
    new ShapeComponent(
        new List<ShapeComponentConstraint>()
        {
            ShapeComponentConstraint.Create_SurfaceHeight_Between(0.2f, 0.6f),
            ShapeComponentConstraint.Create_SurfaceCount_Min(1),
            ShapeComponentConstraint.Create_SurfaceArea_Min(0.035f),
        }
    ),
};
AddShape("Sittable", shapeComponents);
```

<span data-ttu-id="718db-232">Cada consulta de forma é definida por um conjunto de componentes de forma, cada um com um conjunto de restrições de componente e um conjunto de restrições de forma que lista as dependências entre os componentes.</span><span class="sxs-lookup"><span data-stu-id="718db-232">Each shape query is defined by a set of shape components, each with a set of component constraints and a set of shape constraints which listing dependencies between the components.</span></span> <span data-ttu-id="718db-233">Este exemplo inclui três restrições em uma única definição de componente e nenhuma restrição de forma entre componentes (pois há apenas um componente).</span><span class="sxs-lookup"><span data-stu-id="718db-233">This example includes three constraints in a single component definition and no shape constraints between components (as there's only one component).</span></span>

<span data-ttu-id="718db-234">Por outro lado, a forma do diviso tem dois componentes de forma e quatro restrições de forma.</span><span class="sxs-lookup"><span data-stu-id="718db-234">In contrast, the couch shape has two shape components and four shape constraints.</span></span> <span data-ttu-id="718db-235">Os componentes são identificados pelo índice na lista de componentes do usuário (0 e 1 neste exemplo).</span><span class="sxs-lookup"><span data-stu-id="718db-235">Components are identified by their index in the user’s component list (0 and 1 in this example).</span></span>

```cs
shapeConstraints = new List<ShapeConstraint>()
{
    ShapeConstraint.Create_RectanglesSameLength(0, 1, 0.6f),
    ShapeConstraint.Create_RectanglesParallel(0, 1),
    ShapeConstraint.Create_RectanglesAligned(0, 1, 0.3f),
    ShapeConstraint.Create_AtBackOf(1, 0),
};
```

<span data-ttu-id="718db-236">As funções wrapper são fornecidas no módulo do Unity para facilitar a criação de definições de forma personalizadas.</span><span class="sxs-lookup"><span data-stu-id="718db-236">Wrapper functions are provided in the Unity module for easy creation of custom shape definitions.</span></span> <span data-ttu-id="718db-237">A lista completa de restrições de componente e forma pode ser encontrada em "SpatialUnderstandingDll.cs" nas estruturas "ShapeComponentConstraint" e "ShapeConstraint".</span><span class="sxs-lookup"><span data-stu-id="718db-237">The full list of component and shape constraints can be found in “SpatialUnderstandingDll.cs” within the “ShapeComponentConstraint” and the “ShapeConstraint” structures.</span></span>

<span data-ttu-id="718db-238">![A forma do retângulo é encontrada nessa superfície](images/su-shapequery-300px.jpg)</span><span class="sxs-lookup"><span data-stu-id="718db-238">![Rectangle shape is found on this surface](images/su-shapequery-300px.jpg)</span></span><br>
<span data-ttu-id="718db-239">*A forma do retângulo é encontrada nessa superfície*</span><span class="sxs-lookup"><span data-stu-id="718db-239">*Rectangle shape is found on this surface*</span></span>

### <a name="object-placement-solver"></a><span data-ttu-id="718db-240">Solucionador de Posicionamento de Objeto</span><span class="sxs-lookup"><span data-stu-id="718db-240">Object Placement Solver</span></span>

<span data-ttu-id="718db-241">O solucionador de posicionamento de objeto pode ser usado para identificar os locais ideais na sala física para colocar seus objetos.</span><span class="sxs-lookup"><span data-stu-id="718db-241">The object placement solver can be used to identify ideal locations in the physical room to place your objects.</span></span> <span data-ttu-id="718db-242">O solucionador encontrará o local mais adequado, considerando as regras e restrições do objeto.</span><span class="sxs-lookup"><span data-stu-id="718db-242">The solver will find the best fit location given the object rules and constraints.</span></span> <span data-ttu-id="718db-243">Além disso, as consultas de objeto persistem até que o objeto seja removido com chamadas "Solver_RemoveObject" ou "Solver_RemoveAllObjects", permitindo o posicionamento restrito de vários objetos.</span><span class="sxs-lookup"><span data-stu-id="718db-243">In addition, object queries persist until the object is removed with “Solver_RemoveObject” or “Solver_RemoveAllObjects” calls, allowing constrained multi-object placement.</span></span> <span data-ttu-id="718db-244">As consultas de posicionamento de objetos consistem em três partes: tipo de posicionamento com parâmetros, uma lista de regras e uma lista de restrições.</span><span class="sxs-lookup"><span data-stu-id="718db-244">Objects placement queries consist of three parts: placement type with parameters, a list of rules, and a list of constraints.</span></span> <span data-ttu-id="718db-245">Para executar uma consulta, use a API a seguir.</span><span class="sxs-lookup"><span data-stu-id="718db-245">To run a query, use the following API.</span></span>

```cpp
public static int Solver_PlaceObject(
            [In] string objectName,
            [In] IntPtr placementDefinition,        // ObjectPlacementDefinition
            [In] int placementRuleCount,
            [In] IntPtr placementRules,             // ObjectPlacementRule
            [In] int constraintCount,
            [In] IntPtr placementConstraints,       // ObjectPlacementConstraint
            [Out] IntPtr placementResult)
```

<span data-ttu-id="718db-246">Essa função recebe um nome de objeto, definição de posicionamento e uma lista de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="718db-246">This function takes an object name, placement definition, and a list of rules and constraints.</span></span> <span data-ttu-id="718db-247">Os wrappers C# fornece funções auxiliares de construção para facilitar a construção de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="718db-247">The C# wrappers provides construction helper functions to make rule and constraint construction easy.</span></span> <span data-ttu-id="718db-248">A definição de posicionamento contém o tipo de consulta , ou seja, um dos seguintes.</span><span class="sxs-lookup"><span data-stu-id="718db-248">The placement definition contains the query type – that is, one of the following.</span></span>

```cpp
public enum PlacementType
{
    Place_OnFloor,
    Place_OnWall,
    Place_OnCeiling,
    Place_OnShape,
    Place_OnEdge,
    Place_OnFloorAndCeiling,
    Place_RandomInAir,
    Place_InMidAir,
    Place_UnderFurnitureEdge,
};
```

<span data-ttu-id="718db-249">Cada um dos tipos de posicionamento tem um conjunto de parâmetros exclusivos para o tipo.</span><span class="sxs-lookup"><span data-stu-id="718db-249">Each of the placement types has a set of parameters unique to the type.</span></span> <span data-ttu-id="718db-250">A estrutura "ObjectPlacementDefinition" contém um conjunto de funções auxiliares estáticas para criar essas definições.</span><span class="sxs-lookup"><span data-stu-id="718db-250">The “ObjectPlacementDefinition” structure contains a set of static helper functions for creating these definitions.</span></span> <span data-ttu-id="718db-251">Por exemplo, para encontrar um local para colocar um objeto no chão, você pode usar a função a seguir.</span><span class="sxs-lookup"><span data-stu-id="718db-251">For example, to find a place to put an object on the floor, you can use the following function.</span></span> <span data-ttu-id="718db-252">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) Além do tipo de posicionamento, você pode fornecer um conjunto de regras e restrições.</span><span class="sxs-lookup"><span data-stu-id="718db-252">public static ObjectPlacementDefinition Create_OnFloor(Vector3 halfDims) In addition to the placement type, you can provide a set of rules and constraints.</span></span> <span data-ttu-id="718db-253">As regras não podem ser violadas.</span><span class="sxs-lookup"><span data-stu-id="718db-253">Rules cannot be violated.</span></span> <span data-ttu-id="718db-254">Os locais de posicionamento possíveis que atendem ao tipo e às regras são otimizados em relação ao conjunto de restrições para selecionar o local de posicionamento ideal.</span><span class="sxs-lookup"><span data-stu-id="718db-254">Possible placement locations that satisfy the type and rules are then optimized against the set of constraints in order to select the optimal placement location.</span></span> <span data-ttu-id="718db-255">Cada uma das regras e restrições pode ser criada pelas funções de criação estática fornecidas.</span><span class="sxs-lookup"><span data-stu-id="718db-255">Each of the rules and constraints can be created by the provided static creation functions.</span></span> <span data-ttu-id="718db-256">Uma função de construção de restrição e regra de exemplo é fornecida abaixo.</span><span class="sxs-lookup"><span data-stu-id="718db-256">An example rule and constraint construction function is provided below.</span></span>

```cs
public static ObjectPlacementRule Create_AwayFromPosition(
    Vector3 position, float minDistance)
public static ObjectPlacementConstraint Create_NearPoint(
    Vector3 position, float minDistance = 0.0f, float maxDistance = 0.0f)
```

<span data-ttu-id="718db-257">A consulta de posicionamento de objeto abaixo está procurando um local para colocar um cubo de meio medidor na borda de uma superfície, longe de outros objetos colocados anteriormente e próximo ao centro da sala.</span><span class="sxs-lookup"><span data-stu-id="718db-257">The below object placement query is looking for a place to put a half meter cube on the edge of a surface, away from other previously place objects and near the center of the room.</span></span>

```cs
List<ObjectPlacementRule> rules =
    new List<ObjectPlacementRule>() {
        ObjectPlacementRule.Create_AwayFromOtherObjects(1.0f),
    };

List<ObjectPlacementConstraint> constraints =
    new List<ObjectPlacementConstraint> {
        ObjectPlacementConstraint.Create_NearCenter(),
    };

Solver_PlaceObject(
    “MyCustomObject”,
    new ObjectPlacementDefinition.Create_OnEdge(
        new Vector3(0.25f, 0.25f, 0.25f),
        new Vector3(0.25f, 0.25f, 0.25f)),
    rules.Count,
    UnderstandingDLL.PinObject(rules.ToArray()),
    constraints.Count,
    UnderstandingDLL.PinObject(constraints.ToArray()),
    UnderstandingDLL.GetStaticObjectPlacementResultPtr());
```

<span data-ttu-id="718db-258">Se for bem-sucedida, uma estrutura "ObjectPlacementResult" que contém a posição de posicionamento, as dimensões e a orientação será retornada.</span><span class="sxs-lookup"><span data-stu-id="718db-258">If successful, a “ObjectPlacementResult” structure containing the placement position, dimensions, and orientation is returned.</span></span> <span data-ttu-id="718db-259">Além disso, o posicionamento é adicionado à lista interna de objetos colocados da dll.</span><span class="sxs-lookup"><span data-stu-id="718db-259">In addition, the placement is added to the dll’s internal list of placed objects.</span></span> <span data-ttu-id="718db-260">As consultas de posicionamento subsequentes levarão esse objeto em consideração.</span><span class="sxs-lookup"><span data-stu-id="718db-260">Subsequent placement queries will take this object into account.</span></span> <span data-ttu-id="718db-261">O arquivo "LevelSolver.cs" no exemplo do Unity contém mais consultas de exemplo.</span><span class="sxs-lookup"><span data-stu-id="718db-261">The “LevelSolver.cs” file in the Unity sample contains more example queries.</span></span>

<span data-ttu-id="718db-262">![Resultados do posicionamento do objeto](images/su-objectplacement-1000px.jpg)</span><span class="sxs-lookup"><span data-stu-id="718db-262">![Results of object placement](images/su-objectplacement-1000px.jpg)</span></span><br>
<span data-ttu-id="718db-263">*Figura 3: As caixas azuis como o resultado de três consultas de piso com regras de posição da câmera distantes*</span><span class="sxs-lookup"><span data-stu-id="718db-263">*Figure 3: The blue boxes how the result from three place on floor queries with away from camera position rules*</span></span>

<span data-ttu-id="718db-264">Ao resolver o local de posicionamento de vários objetos necessários para um cenário de nível ou de aplicativo, primeiro resolva objetos grandes e desamarados para maximizar a probabilidade de que um espaço possa ser encontrado.</span><span class="sxs-lookup"><span data-stu-id="718db-264">When solving for placement location of multiple objects required for a level or application scenario, first solve indispensable and large objects in order to maximizing the probability that a space can be found.</span></span> <span data-ttu-id="718db-265">A ordem de posicionamento é importante.</span><span class="sxs-lookup"><span data-stu-id="718db-265">Placement order is important.</span></span> <span data-ttu-id="718db-266">Se não for possível encontrar posicionamentos de objeto, tente configurações menos restritas.</span><span class="sxs-lookup"><span data-stu-id="718db-266">If object placements cannot be found, try less constrained configurations.</span></span> <span data-ttu-id="718db-267">Ter um conjunto de configurações de fallback é essencial para dar suporte à funcionalidade em várias configurações de sala.</span><span class="sxs-lookup"><span data-stu-id="718db-267">Having a set of fallback configurations is critical to supporting functionality across many room configurations.</span></span>

### <a name="room-scanning-process"></a><span data-ttu-id="718db-268">Processo de verificação de sala</span><span class="sxs-lookup"><span data-stu-id="718db-268">Room Scanning Process</span></span>

<span data-ttu-id="718db-269">Embora a solução de mapeamento espacial fornecida pelo HoloLens seja projetada para ser genérica o suficiente para atender às necessidades de toda a gama de espaços com problemas, o módulo de compreensão espacial foi criado para dar suporte às necessidades de dois jogos específicos.</span><span class="sxs-lookup"><span data-stu-id="718db-269">While the spatial mapping solution provided by the HoloLens is designed to be generic enough to meet the needs of the entire gamut of problem spaces, the spatial understanding module was built to support the needs of two specific games.</span></span> <span data-ttu-id="718db-270">Sua solução é estruturada em torno de um processo específico e um conjunto de suposições, resumidos abaixo.</span><span class="sxs-lookup"><span data-stu-id="718db-270">Its solution is structured around a specific process and set of assumptions, summarized below.</span></span>

```txt
Fixed size playspace – The user specifies the maximum playspace size in the init call.

One-time scan process –
    The process requires a discrete scanning phase where the user walks around,
    defining the playspace.
    Query functions will not function until after the scan has been finalized.
```

<span data-ttu-id="718db-271">"pintura" do playspace orientado pelo usuário – durante a fase de verificação, o usuário se move e procura o ritmo das peças, pintando efetivamente as áreas que devem ser incluídas.</span><span class="sxs-lookup"><span data-stu-id="718db-271">User driven playspace “painting” – During the scanning phase, the user moves and looks around the plays pace, effectively painting the areas, which should be included.</span></span> <span data-ttu-id="718db-272">A malha gerada é importante para fornecer comentários do usuário durante essa fase.</span><span class="sxs-lookup"><span data-stu-id="718db-272">The generated mesh is important to provide user feedback during this phase.</span></span> <span data-ttu-id="718db-273">Configuração interna ou de escritório – as funções de consulta são projetadas em torno de superfícies planas e paredes em ângulos direito.</span><span class="sxs-lookup"><span data-stu-id="718db-273">Indoors home or office setup – The query functions are designed around flat surfaces and walls at right angles.</span></span> <span data-ttu-id="718db-274">Essa é uma limitação suave.</span><span class="sxs-lookup"><span data-stu-id="718db-274">This is a soft limitation.</span></span> <span data-ttu-id="718db-275">No entanto, durante a fase de verificação, uma análise de eixo primário é concluída para otimizar o mosaico de malha ao longo dos eixos principal e secundário.</span><span class="sxs-lookup"><span data-stu-id="718db-275">However, during the scanning phase, a primary axis analysis is completed to optimize the mesh tessellation along major and minor axis.</span></span> <span data-ttu-id="718db-276">O arquivo SpatialUnderstanding.cs incluído gerencia o processo de fase de verificação.</span><span class="sxs-lookup"><span data-stu-id="718db-276">The included SpatialUnderstanding.cs file manages the scanning phase process.</span></span> <span data-ttu-id="718db-277">Ele chama as funções a seguir.</span><span class="sxs-lookup"><span data-stu-id="718db-277">It calls the following functions.</span></span>

```txt
SpatialUnderstanding_Init – Called once at the start.

GeneratePlayspace_InitScan – Indicates that the scan phase should begin.

GeneratePlayspace_UpdateScan_DynamicScan –
    Called each frame to update the scanning process. The camera position and
    orientation is passed in and is used for the playspace painting process,
    described above.

GeneratePlayspace_RequestFinish –
    Called to finalize the playspace. This will use the areas “painted” during
    the scan phase to define and lock the playspace. The application can query
    statistics during the scanning phase as well as query the custom mesh for
    providing user feedback.

Import_UnderstandingMesh –
    During scanning, the “SpatialUnderstandingCustomMesh” behavior provided by
    the module and placed on the understanding prefab will periodically query the
    custom mesh generated by the process. In addition, this is done once more
    after scanning has been finalized.
```

<span data-ttu-id="718db-278">O fluxo de verificação, orientado pelo comportamento "SpatialUnderstanding", chama InitScan e, em seguida, UpdateScan em cada quadro.</span><span class="sxs-lookup"><span data-stu-id="718db-278">The scanning flow, driven by the “SpatialUnderstanding” behavior calls InitScan, then UpdateScan each frame.</span></span> <span data-ttu-id="718db-279">Quando a consulta de estatísticas relata uma cobertura razoável, o usuário tem permissão para fazer airtap para chamar RequestFinish para indicar o final da fase de verificação.</span><span class="sxs-lookup"><span data-stu-id="718db-279">When the statistics query reports reasonable coverage, the user is allowed to airtap to call RequestFinish to indicate the end of the scanning phase.</span></span> <span data-ttu-id="718db-280">UpdateScan continuará a ser chamado até que seu valor de retorno indique que a dll concluiu o processamento.</span><span class="sxs-lookup"><span data-stu-id="718db-280">UpdateScan continues to be called until its return value indicates that the dll has completed processing.</span></span>

### <a name="understanding-mesh"></a><span data-ttu-id="718db-281">Noções básicas sobre malha</span><span class="sxs-lookup"><span data-stu-id="718db-281">Understanding Mesh</span></span>

<span data-ttu-id="718db-282">A dll de compreensão armazena internamente o playspace como uma grade de cubos voxel de tamanho de 8 cm.</span><span class="sxs-lookup"><span data-stu-id="718db-282">The understanding dll internally stores the playspace as a grid of 8 cm sized voxel cubes.</span></span> <span data-ttu-id="718db-283">Durante a parte inicial da verificação, uma análise de componente primário é concluída para determinar os eixos da sala.</span><span class="sxs-lookup"><span data-stu-id="718db-283">During the initial part of scanning, a primary component analysis is completed to determine the axes of the room.</span></span> <span data-ttu-id="718db-284">Internamente, ele armazena seu espaço voxel alinhado a esses eixos.</span><span class="sxs-lookup"><span data-stu-id="718db-284">Internally, it stores its voxel space aligned to these axes.</span></span> <span data-ttu-id="718db-285">Uma malha é gerada aproximadamente a cada segundo extraindo a isosurface do volume voxel.</span><span class="sxs-lookup"><span data-stu-id="718db-285">A mesh is generated approximately every second by extracting the isosurface from the voxel volume.</span></span>

<span data-ttu-id="718db-286">![Malha gerada produzida a partir do volume de voxel](images/su-custommesh.jpg)</span><span class="sxs-lookup"><span data-stu-id="718db-286">![Generated mesh produced from the voxel volume](images/su-custommesh.jpg)</span></span><br>
<span data-ttu-id="718db-287">*Malha gerada produzida a partir do volume de voxel*</span><span class="sxs-lookup"><span data-stu-id="718db-287">*Generated mesh produced from the voxel volume*</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="718db-288">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="718db-288">Troubleshooting</span></span>

* <span data-ttu-id="718db-289">Verifique se você definiu a [funcionalidade SpatialPerception](#setting-the-spatialperception-capability)</span><span class="sxs-lookup"><span data-stu-id="718db-289">Ensure you have set the [SpatialPerception](#setting-the-spatialperception-capability) capability</span></span>
* <span data-ttu-id="718db-290">Quando o acompanhamento é perdido, o próximo evento OnSurfaceChanged removerá todas as malhas.</span><span class="sxs-lookup"><span data-stu-id="718db-290">When tracking is lost, the next OnSurfaceChanged event will remove all meshes.</span></span>

## <a name="spatial-mapping-in-mixed-reality-toolkit"></a><span data-ttu-id="718db-291">Mapeamento espacial no Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="718db-291">Spatial Mapping in Mixed Reality Toolkit</span></span>

<span data-ttu-id="718db-292">Para obter mais informações sobre como usar o Mapeamento Espacial com o Kit de Ferramentas de Realidade Misturada, consulte a seção de reconhecimento [espacial](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) dos documentos do MRTK.</span><span class="sxs-lookup"><span data-stu-id="718db-292">For more information on using Spatial Mapping with Mixed Reality Toolkit, see the [spatial awareness section](/windows/mixed-reality/mrtk-unity/features/spatial-awareness/spatial-awareness-getting-started) of the MRTK docs.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="718db-293">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="718db-293">Next Development Checkpoint</span></span>

<span data-ttu-id="718db-294">Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK.</span><span class="sxs-lookup"><span data-stu-id="718db-294">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="718db-295">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="718db-295">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="718db-296">Text</span><span class="sxs-lookup"><span data-stu-id="718db-296">Text</span></span>](text-in-unity.md)

<span data-ttu-id="718db-297">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="718db-297">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="718db-298">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="718db-298">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="718db-299">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="718db-299">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="718db-300">Confira também</span><span class="sxs-lookup"><span data-stu-id="718db-300">See also</span></span>

* [<span data-ttu-id="718db-301">Sistemas de coordenadas</span><span class="sxs-lookup"><span data-stu-id="718db-301">Coordinate systems</span></span>](../../design/coordinate-systems.md)
* [<span data-ttu-id="718db-302">Sistemas de coordenadas no Unity</span><span class="sxs-lookup"><span data-stu-id="718db-302">Coordinate systems in Unity</span></span>](coordinate-systems-in-unity.md)
* <span data-ttu-id="718db-303"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span><span class="sxs-lookup"><span data-stu-id="718db-303"><a href="https://github.com/Microsoft/MixedRealityToolkit-Unity" target="_blank">MixedRealityToolkit</a></span></span>
* <span data-ttu-id="718db-304"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span><span class="sxs-lookup"><span data-stu-id="718db-304"><a href="https://docs.unity3d.com/ScriptReference/MeshFilter.html" target="_blank">UnityEngine.MeshFilter</a></span></span>
* <span data-ttu-id="718db-305"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span><span class="sxs-lookup"><span data-stu-id="718db-305"><a href="https://docs.unity3d.com/ScriptReference/MeshCollider.html" target="_blank">UnityEngine.MeshCollider</a></span></span>
* <span data-ttu-id="718db-306"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span><span class="sxs-lookup"><span data-stu-id="718db-306"><a href="https://docs.unity3d.com/ScriptReference/Bounds.html" target="_blank">UnityEngine.Bounds</a></span></span>
