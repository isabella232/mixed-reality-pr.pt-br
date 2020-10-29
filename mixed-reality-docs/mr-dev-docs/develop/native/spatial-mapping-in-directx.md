---
title: Mapeamento espacial no DirectX
description: Explica como implementar o mapeamento espacial em seu aplicativo DirectX. Isso inclui uma explicação detalhada do aplicativo de exemplo de mapeamento espacial incluído no SDK do Plataforma Universal do Windows.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: Realidade mista do Windows, mapeamento espacial, ambiente, interação, DirectX, winrt, API, código de exemplo, UWP, SDK, passo a passos
ms.openlocfilehash: 3e20f0b7a677ba522f8a1140284a2aa0e96eedcd
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675546"
---
# <a name="spatial-mapping-in-directx"></a><span data-ttu-id="08da3-105">Mapeamento espacial no DirectX</span><span class="sxs-lookup"><span data-stu-id="08da3-105">Spatial mapping in DirectX</span></span>

> [!NOTE]
> <span data-ttu-id="08da3-106">Este artigo está relacionado às APIs nativas do WinRT herdadas.</span><span class="sxs-lookup"><span data-stu-id="08da3-106">This article relates to the legacy WinRT native APIs.</span></span>  <span data-ttu-id="08da3-107">Para novos projetos de aplicativos nativos, é recomendável usar a **[API OpenXR](openxr-getting-started.md)** .</span><span class="sxs-lookup"><span data-stu-id="08da3-107">For new native app projects, we recommend using the **[OpenXR API](openxr-getting-started.md)** .</span></span>

<span data-ttu-id="08da3-108">Este tópico descreve como implementar o [mapeamento espacial](../../design/spatial-mapping.md) em seu aplicativo DirectX.</span><span class="sxs-lookup"><span data-stu-id="08da3-108">This topic describes how to implement [spatial mapping](../../design/spatial-mapping.md) in your DirectX app.</span></span> <span data-ttu-id="08da3-109">Isso inclui uma explicação detalhada do aplicativo de exemplo de mapeamento espacial incluído no SDK do Plataforma Universal do Windows.</span><span class="sxs-lookup"><span data-stu-id="08da3-109">This includes a detailed explanation of the spatial mapping sample application that is included with the Universal Windows Platform SDK.</span></span>

<span data-ttu-id="08da3-110">Este tópico usa código do exemplo de código [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP.</span><span class="sxs-lookup"><span data-stu-id="08da3-110">This topic uses code from the [HolographicSpatialMapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) UWP code sample.</span></span>

>[!NOTE]
><span data-ttu-id="08da3-111">Os trechos de código neste artigo demonstram atualmente o uso de C++/CX em vez de c++/WinRT compatível com C + +17, conforme usado no [modelo de projeto do C++ Holographic](creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="08da3-111">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="08da3-112">Os conceitos são equivalentes a um projeto/WinRT do C++, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="08da3-112">The concepts are equivalent for a C++/WinRT project, though you will need to translate the code.</span></span>

## <a name="device-support"></a><span data-ttu-id="08da3-113">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="08da3-113">Device support</span></span>

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><span data-ttu-id="08da3-114"><strong>Recurso</strong></span><span class="sxs-lookup"><span data-stu-id="08da3-114"><strong>Feature</strong></span></span></td>
        <td><span data-ttu-id="08da3-115"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1ª geração)</strong></a></span><span class="sxs-lookup"><span data-stu-id="08da3-115"><a href="../../hololens-hardware-details.md"><strong>HoloLens (1st gen)</strong></a></span></span></td>
        <td><span data-ttu-id="08da3-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span><span class="sxs-lookup"><span data-stu-id="08da3-116"><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></span></span></td>
        <td><span data-ttu-id="08da3-117"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></span><span class="sxs-lookup"><span data-stu-id="08da3-117"><a href="../../discover/immersive-headset-hardware-details.md"><strong>Immersive headsets</strong></a></span></span></td>
    </tr>
     <tr>
        <td><span data-ttu-id="08da3-118">mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="08da3-118">Spatial mapping</span></span></td>
        <td><span data-ttu-id="08da3-119">✔️</span><span class="sxs-lookup"><span data-stu-id="08da3-119">✔️</span></span></td>
        <td><span data-ttu-id="08da3-120">✔️</span><span class="sxs-lookup"><span data-stu-id="08da3-120">✔️</span></span></td>
        <td>❌</td>
    </tr>
</table>

## <a name="directx-development-overview"></a><span data-ttu-id="08da3-121">Visão geral de desenvolvimento do DirectX</span><span class="sxs-lookup"><span data-stu-id="08da3-121">DirectX development overview</span></span>

<span data-ttu-id="08da3-122">O desenvolvimento de aplicativos nativos para o mapeamento espacial usa as APIs no namespace [Windows. percepção. Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) .</span><span class="sxs-lookup"><span data-stu-id="08da3-122">Native application development for spatial mapping uses the APIs under the [Windows.Perception.Spatial](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx) namespace.</span></span> <span data-ttu-id="08da3-123">Essas APIs fornecem controle total da funcionalidade de mapeamento espacial, de uma maneira diretamente análoga às APIs de mapeamento espacial expostas pelo [Unity](../unity/spatial-mapping-in-unity.md).</span><span class="sxs-lookup"><span data-stu-id="08da3-123">These APIs provide full control of spatial mapping functionality, in a manner directly analogous to the spatial mapping APIs exposed by [Unity](../unity/spatial-mapping-in-unity.md).</span></span>

### <a name="perception-apis"></a><span data-ttu-id="08da3-124">APIs de percepção</span><span class="sxs-lookup"><span data-stu-id="08da3-124">Perception APIs</span></span>

<span data-ttu-id="08da3-125">Os tipos primários fornecidos para o desenvolvimento de mapeamentos espaciais são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="08da3-125">The primary types provided for spatial mapping development are as follows:</span></span>
* <span data-ttu-id="08da3-126">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) fornece informações sobre superfícies em regiões especificadas pelo aplicativo de espaço próximo ao usuário, na forma de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="08da3-126">[SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) provides information about surfaces in application-specified regions of space near the user, in the form of SpatialSurfaceInfo objects.</span></span>
* <span data-ttu-id="08da3-127">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) descreve uma superfície espacial existentes única, incluindo uma ID exclusiva, o volume delimitador e a hora da última alteração.</span><span class="sxs-lookup"><span data-stu-id="08da3-127">[SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) describes a single extant spatial surface, including a unique ID, bounding volume and time of last change.</span></span> <span data-ttu-id="08da3-128">Ele fornecerá um SpatialSurfaceMesh de forma assíncrona após a solicitação.</span><span class="sxs-lookup"><span data-stu-id="08da3-128">It will provide a SpatialSurfaceMesh asynchronously upon request.</span></span>
* <span data-ttu-id="08da3-129">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contém parâmetros usados para personalizar os objetos SpatialSurfaceMesh solicitados de SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="08da3-129">[SpatialSurfaceMeshOptions](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshoptions.aspx) contains parameters used to customize the SpatialSurfaceMesh objects requested from SpatialSurfaceInfo.</span></span>
* <span data-ttu-id="08da3-130">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) representa os dados de malha de uma única superfície espacial.</span><span class="sxs-lookup"><span data-stu-id="08da3-130">[SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) represents the mesh data for a single spatial surface.</span></span> <span data-ttu-id="08da3-131">Os dados para posições de vértice, normais de vértice e índices de triângulo estão contidos em objetos member SpatialSurfaceMeshBuffer.</span><span class="sxs-lookup"><span data-stu-id="08da3-131">The data for vertex positions, vertex normals and triangle indices is contained in member SpatialSurfaceMeshBuffer objects.</span></span>
* <span data-ttu-id="08da3-132">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) encapsula um único tipo de dados de malha.</span><span class="sxs-lookup"><span data-stu-id="08da3-132">[SpatialSurfaceMeshBuffer](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemeshbuffer.aspx) wraps a single type of mesh data.</span></span>

<span data-ttu-id="08da3-133">Ao desenvolver um aplicativo usando essas APIs, o fluxo de programa básico terá esta aparência (conforme demonstrado no aplicativo de exemplo descrito abaixo):</span><span class="sxs-lookup"><span data-stu-id="08da3-133">When developing an application using these APIs, your basic program flow will look like this (as demonstrated in the sample application described below):</span></span>
- <span data-ttu-id="08da3-134">**Configurar seu SpatialSurfaceObserver**</span><span class="sxs-lookup"><span data-stu-id="08da3-134">**Set up your SpatialSurfaceObserver**</span></span>
  - <span data-ttu-id="08da3-135">Chame [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx)para garantir que o usuário tenha concedido permissão para que seu aplicativo use os recursos de mapeamento espacial do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="08da3-135">Call [RequestAccessAsync](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.requestaccessasync.aspx), to ensure that the user has given permission for your application to use the device's spatial mapping capabilities.</span></span>
  - <span data-ttu-id="08da3-136">Crie uma instância de um objeto SpatialSurfaceObserver.</span><span class="sxs-lookup"><span data-stu-id="08da3-136">Instantiate a SpatialSurfaceObserver object.</span></span>
  - <span data-ttu-id="08da3-137">Chame [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) para especificar as regiões de espaço nas quais você deseja obter informações sobre superfícies espaciais.</span><span class="sxs-lookup"><span data-stu-id="08da3-137">Call [SetBoundingVolumes](https://msdn.microsoft.com/library/windows/apps/mt592747.aspx) to specify the regions of space in which you want information about spatial surfaces.</span></span> <span data-ttu-id="08da3-138">Você pode modificar essas regiões no futuro simplesmente chamando essa função novamente.</span><span class="sxs-lookup"><span data-stu-id="08da3-138">You may modify these regions in the future by simply calling this function again.</span></span> <span data-ttu-id="08da3-139">Cada região é especificada usando um [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span><span class="sxs-lookup"><span data-stu-id="08da3-139">Each region is specified using a [SpatialBoundingVolume](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialboundingvolume.aspx).</span></span>
  - <span data-ttu-id="08da3-140">Registre-se no evento [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) , que será acionado sempre que novas informações estiverem disponíveis sobre as superfícies espaciais nas regiões de espaço que você especificou.</span><span class="sxs-lookup"><span data-stu-id="08da3-140">Register for the [ObservedSurfacesChanged](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.observedsurfaceschanged.aspx) event, which will fire whenever new information is available about the spatial surfaces in the regions of space you have specified.</span></span>
- <span data-ttu-id="08da3-141">**Processar eventos ObservedSurfacesChanged**</span><span class="sxs-lookup"><span data-stu-id="08da3-141">**Process ObservedSurfacesChanged events**</span></span>
  - <span data-ttu-id="08da3-142">Em seu manipulador de eventos, chame [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) para receber um mapa de objetos SpatialSurfaceInfo.</span><span class="sxs-lookup"><span data-stu-id="08da3-142">In your event handler, call [GetObservedSurfaces](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.getobservedsurfaces.aspx) to receive a map of SpatialSurfaceInfo objects.</span></span> <span data-ttu-id="08da3-143">Usando esse mapa, você pode atualizar os registros dos quais as superfícies espaciais [existem no ambiente do usuário](../../design/spatial-mapping.md#mesh-caching).</span><span class="sxs-lookup"><span data-stu-id="08da3-143">Using this map, you can update your records of which spatial surfaces [exist in the user's environment](../../design/spatial-mapping.md#mesh-caching).</span></span>
  - <span data-ttu-id="08da3-144">Para cada objeto SpatialSurfaceInfo, você pode consultar [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) para determinar as extensões espaciais da superfície, expressas em um [sistema de coordenadas espaciais](../../design/coordinate-systems.md) de sua escolha.</span><span class="sxs-lookup"><span data-stu-id="08da3-144">For each SpatialSurfaceInfo object, you may query [TryGetBounds](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.trygetbounds.aspx) to determine the spatial extents of the surface, expressed in a [spatial coordinate system](../../design/coordinate-systems.md) of your choosing.</span></span>
  - <span data-ttu-id="08da3-145">Se você decidir solicitar malha para uma superfície espacial, chame [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span><span class="sxs-lookup"><span data-stu-id="08da3-145">If you decide to request mesh for a spatial surface, call [TryComputeLatestMeshAsync](https://msdn.microsoft.com/library/windows/apps/mt592715.aspx).</span></span> <span data-ttu-id="08da3-146">Você pode fornecer opções especificando a densidade desejada de triângulos e o formato dos dados de malha retornados.</span><span class="sxs-lookup"><span data-stu-id="08da3-146">You may provide options specifying the desired density of triangles, and the format of the returned mesh data.</span></span>
- <span data-ttu-id="08da3-147">**Receber e processar malha**</span><span class="sxs-lookup"><span data-stu-id="08da3-147">**Receive and process mesh**</span></span>
  - <span data-ttu-id="08da3-148">Cada chamada para TryComputeLatestMeshAsync irá aysnchronously retornar um objeto SpatialSurfaceMesh.</span><span class="sxs-lookup"><span data-stu-id="08da3-148">Each call to TryComputeLatestMeshAsync will aysnchronously return one SpatialSurfaceMesh object.</span></span>
  - <span data-ttu-id="08da3-149">Desse objeto, você pode acessar os objetos SpatialSurfaceMeshBuffer contidos para acessar os índices de triângulo, as posições de vértice e (se solicitado) vértices normais da malha.</span><span class="sxs-lookup"><span data-stu-id="08da3-149">From this object you can access the contained SpatialSurfaceMeshBuffer objects in order to access the triangle indices, vertex positions and (if requested) vertex normals of the mesh.</span></span> <span data-ttu-id="08da3-150">Esses dados estarão em um formato diretamente compatível com as [APIs do Direct3D 11](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) usadas para renderizar malhas.</span><span class="sxs-lookup"><span data-stu-id="08da3-150">This data will be in a format directly compatible with the [Direct3D 11 APIs](https://msdn.microsoft.com/library/windows/desktop/ff476501(v=vs.85).aspx) used for rendering meshes.</span></span>
  - <span data-ttu-id="08da3-151">A partir daqui, o aplicativo pode opcionalmente executar a análise ou o [processamento](../../design/spatial-mapping.md#mesh-processing) dos dados de malha e usá-lo para [renderização](../../design/spatial-mapping.md#rendering) e [raycasting física e colisão](../../design/spatial-mapping.md#raycasting-and-collision).</span><span class="sxs-lookup"><span data-stu-id="08da3-151">From here your application can optionally perform analysis or [processing](../../design/spatial-mapping.md#mesh-processing) of the mesh data, and use it for [rendering](../../design/spatial-mapping.md#rendering) and physics [raycasting and collision](../../design/spatial-mapping.md#raycasting-and-collision).</span></span>
  - <span data-ttu-id="08da3-152">Um detalhe importante a ser observado é que você deve aplicar uma escala às posições de vértice de malha (por exemplo, no sombreador de vértice usado para renderizar as malhas), para convertê-las das unidades de inteiros otimizadas nas quais elas são armazenadas no buffer, em metros.</span><span class="sxs-lookup"><span data-stu-id="08da3-152">One important detail to note is that you must apply a scale to the mesh vertex positions (for example in the vertex shader used for rendering the meshes), to convert them from the optimized integer units in which they are stored in the buffer, to meters.</span></span> <span data-ttu-id="08da3-153">Você pode recuperar essa escala chamando [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span><span class="sxs-lookup"><span data-stu-id="08da3-153">You can retrieve this scale by calling [VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx).</span></span>

### <a name="troubleshooting"></a><span data-ttu-id="08da3-154">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="08da3-154">Troubleshooting</span></span>
* <span data-ttu-id="08da3-155">Não se esqueça de dimensionar as posições de vértice de malha em seu sombreador de vértice, usando a escala retornada por [SpatialSurfaceMesh. VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span><span class="sxs-lookup"><span data-stu-id="08da3-155">Don't forget to scale mesh vertex positions in your vertex shader, using the scale returned by [SpatialSurfaceMesh.VertexPositionScale](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.vertexpositionscale.aspx)</span></span>

## <a name="spatial-mapping-code-sample-walkthrough"></a><span data-ttu-id="08da3-156">Instruções de exemplo de código de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="08da3-156">Spatial Mapping code sample walkthrough</span></span>

<span data-ttu-id="08da3-157">O exemplo de código de [mapeamento espacial Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) inclui o código que você pode usar para começar a carregar malhas de superfície em seu aplicativo, incluindo a infraestrutura para gerenciar e renderizar malhas de superfície.</span><span class="sxs-lookup"><span data-stu-id="08da3-157">The [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample includes code that you can use to get started loading surface meshes into your app, including infrastructure for managing and rendering surface meshes.</span></span>

<span data-ttu-id="08da3-158">Agora, vamos examinar como adicionar o recurso de mapeamento de superfície ao seu aplicativo DirectX.</span><span class="sxs-lookup"><span data-stu-id="08da3-158">Now, we walk through how to add surface mapping capability to your DirectX app.</span></span> <span data-ttu-id="08da3-159">Você pode adicionar esse código ao seu projeto de [modelo de aplicativo Holographic do Windows](creating-a-holographic-directx-project.md) ou pode acompanhar navegando pelo exemplo de código mencionado acima.</span><span class="sxs-lookup"><span data-stu-id="08da3-159">You can add this code to your [Windows Holographic app template](creating-a-holographic-directx-project.md) project, or you can follow along by browsing through the code sample mentioned above.</span></span> <span data-ttu-id="08da3-160">Este exemplo de código é baseado no modelo de aplicativo Holographic do Windows.</span><span class="sxs-lookup"><span data-stu-id="08da3-160">This code sample is based on the Windows Holographic app template.</span></span>

### <a name="set-up-your-app-to-use-the-spatialperception-capability"></a><span data-ttu-id="08da3-161">Configurar seu aplicativo para usar o recurso spatialPerception</span><span class="sxs-lookup"><span data-stu-id="08da3-161">Set up your app to use the spatialPerception capability</span></span>

<span data-ttu-id="08da3-162">Seu aplicativo deve ser capaz de usar o recurso de mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="08da3-162">Your app must be able to use the spatial mapping capability.</span></span> <span data-ttu-id="08da3-163">Isso é necessário porque a malha espacial é uma representação do ambiente do usuário, que pode ser considerado dados privados.</span><span class="sxs-lookup"><span data-stu-id="08da3-163">This is necessary because the spatial mesh is a representation of the user's environment, which may be considered private data.</span></span> <span data-ttu-id="08da3-164">Declare esse recurso no arquivo Package. appxmanifest para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08da3-164">Declare this capability in the package.appxmanifest file for your app.</span></span> <span data-ttu-id="08da3-165">Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="08da3-165">Here's an example:</span></span>

```xml
<Capabilities>
  <uap2:Capability Name="spatialPerception" />
</Capabilities>
```

<span data-ttu-id="08da3-166">A funcionalidade vem do namespace **uap2** .</span><span class="sxs-lookup"><span data-stu-id="08da3-166">The capability comes from the **uap2** namespace.</span></span> <span data-ttu-id="08da3-167">Para obter acesso a esse namespace em seu manifesto, inclua-o como um atributo *xlmns* no &lt; elemento> do pacote.</span><span class="sxs-lookup"><span data-stu-id="08da3-167">To get access to this namespace in your manifest, include it as an *xlmns* attribute in the &lt;Package> element.</span></span> <span data-ttu-id="08da3-168">Aqui está um exemplo:</span><span class="sxs-lookup"><span data-stu-id="08da3-168">Here's an example:</span></span>

```xml
<Package
    xmlns="https://schemas.microsoft.com/appx/manifest/foundation/windows10"
    xmlns:mp="https://schemas.microsoft.com/appx/2014/phone/manifest"
    xmlns:uap="https://schemas.microsoft.com/appx/manifest/uap/windows10"
    xmlns:uap2="https://schemas.microsoft.com/appx/manifest/uap/windows10/2"
    IgnorableNamespaces="uap uap2 mp"
    >
```

### <a name="check-for-spatial-mapping-feature-support"></a><span data-ttu-id="08da3-169">Verificar o suporte a recursos de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="08da3-169">Check for spatial mapping feature support</span></span>

<span data-ttu-id="08da3-170">O Windows Mixed Reality dá suporte a uma ampla variedade de dispositivos, incluindo dispositivos que não dão suporte ao mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="08da3-170">Windows Mixed Reality supports a wide range of devices, including devices which do not support spatial mapping.</span></span> <span data-ttu-id="08da3-171">Se seu aplicativo pode usar o mapeamento espacial ou deve usar o mapeamento espacial, para fornecer funcionalidade, ele deve verificar se há suporte para o mapeamento espacial antes de tentar usá-lo.</span><span class="sxs-lookup"><span data-stu-id="08da3-171">If your app can use spatial mapping, or must use spatial mapping, to provide functionality, it should check to make sure that spatial mapping is supported before trying to use it.</span></span> <span data-ttu-id="08da3-172">Por exemplo, se o mapeamento espacial for exigido pelo seu aplicativo de realidade misturada, ele deverá exibir uma mensagem para esse efeito se um usuário tentar executá-lo em um dispositivo sem o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="08da3-172">For example, if spatial mapping is required by your mixed reality app, it should display a message to that effect if a user tries running it on a device without spatial mapping.</span></span> <span data-ttu-id="08da3-173">Ou, seu aplicativo pode ser capaz de renderizar seu próprio ambiente virtual no lugar do ambiente do usuário, fornecendo uma experiência semelhante ao que aconteceria se o mapeamento espacial estivesse disponível.</span><span class="sxs-lookup"><span data-stu-id="08da3-173">Or, your app may be able to render its own virtual environment in place of the user's environment, providing an experience that is similar to what would happen if spatial mapping were available.</span></span> <span data-ttu-id="08da3-174">Em qualquer evento, essa API permite que seu aplicativo fique atento quando não obter dados de mapeamento espacial e responder da maneira apropriada.</span><span class="sxs-lookup"><span data-stu-id="08da3-174">In any event, this API allows your app to be aware of when it will not get spatial mapping data and respond in the appropriate way.</span></span>

<span data-ttu-id="08da3-175">Para verificar o dispositivo atual quanto ao suporte de mapeamento espacial, primeiro verifique se o contrato UWP está no nível 4 ou superior e, em seguida, chame SpatialSurfaceObserver:: IsSupported ().</span><span class="sxs-lookup"><span data-stu-id="08da3-175">To check the current device for spatial mapping support, first make sure the UWP contract is at level 4 or greater and then call SpatialSurfaceObserver::IsSupported().</span></span> <span data-ttu-id="08da3-176">Veja como fazer isso no contexto do exemplo de código de [mapeamento espacial do Holographic](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) .</span><span class="sxs-lookup"><span data-stu-id="08da3-176">Here's how to do so in the context of the [Holographic Spatial Mapping](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/HolographicSpatialMapping) code sample.</span></span> <span data-ttu-id="08da3-177">O suporte é verificado logo antes de solicitar acesso.</span><span class="sxs-lookup"><span data-stu-id="08da3-177">Support is checked just before requesting access.</span></span>

<span data-ttu-id="08da3-178">A API SpatialSurfaceObserver:: IsSupported () está disponível a partir da versão 15063 do SDK.</span><span class="sxs-lookup"><span data-stu-id="08da3-178">The SpatialSurfaceObserver::IsSupported() API is available starting in SDK version 15063.</span></span> <span data-ttu-id="08da3-179">Se necessário, redirecione seu projeto para a versão da plataforma 15063 antes de usar essa API.</span><span class="sxs-lookup"><span data-stu-id="08da3-179">If necessary, retarget your project to platform version 15063 before using this API.</span></span>

```cpp
if (m_surfaceObserver == nullptr)
   {
       using namespace Windows::Foundation::Metadata;
       if (ApiInformation::IsApiContractPresent(L"Windows.Foundation.UniversalApiContract", 4))
       {
           if (!SpatialSurfaceObserver::IsSupported())
           {
               // The current system does not have spatial mapping capability.
               // Turn off spatial mapping.
               m_spatialPerceptionAccessRequested = true;
               m_surfaceAccessAllowed = false;
           }
       }

       if (!m_spatialPerceptionAccessRequested)
       {
           /// etc ...
```

<span data-ttu-id="08da3-180">Observe que, quando o contrato UWP é menor que o nível 4, o aplicativo deve continuar como se o dispositivo fosse capaz de fazer o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="08da3-180">Note that when the UWP contract is less than level 4, the app should proceed as though the device is capable of doing spatial mapping.</span></span>

### <a name="request-access-to-spatial-mapping-data"></a><span data-ttu-id="08da3-181">Solicitar acesso aos dados de mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="08da3-181">Request access to spatial mapping data</span></span>

<span data-ttu-id="08da3-182">Seu aplicativo precisa solicitar permissão para acessar dados de mapeamento espacial antes de tentar criar qualquer observador de superfície.</span><span class="sxs-lookup"><span data-stu-id="08da3-182">Your app needs to request permission to access spatial mapping data before trying to create any surface observers.</span></span> <span data-ttu-id="08da3-183">Veja um exemplo com base no exemplo de código de mapeamento de superfície, com mais detalhes fornecidos mais adiante nesta página:</span><span class="sxs-lookup"><span data-stu-id="08da3-183">Here's an example based upon our Surface Mapping code sample, with more details provided later on this page:</span></span>

```cpp
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // Create a surface observer.
    }
    else
    {
        // Handle spatial mapping unavailable.
    }
}
```

### <a name="create-a-surface-observer"></a><span data-ttu-id="08da3-184">Criar um observador de superfície</span><span class="sxs-lookup"><span data-stu-id="08da3-184">Create a surface observer</span></span>

<span data-ttu-id="08da3-185">O namespace **Windows::P erception:: Spatial:: superfícies** inclui a classe [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) , que observa um ou mais volumes que você especifica em um [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span><span class="sxs-lookup"><span data-stu-id="08da3-185">The **Windows::Perception::Spatial::Surfaces** namespace includes the [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) class, which observes one or more volumes that you specify in a [SpatialCoordinateSystem](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialcoordinatesystem.aspx).</span></span> <span data-ttu-id="08da3-186">Use uma instância de [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) para acessar dados de malha de superfície em tempo real.</span><span class="sxs-lookup"><span data-stu-id="08da3-186">Use a [SpatialSurfaceObserver](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceobserver.aspx) instance to access surface mesh data in real time.</span></span>

<span data-ttu-id="08da3-187">De **AppMain. h** :</span><span class="sxs-lookup"><span data-stu-id="08da3-187">From **AppMain.h** :</span></span>

```cpp
// Obtains surface mapping data from the device in real time.
Windows::Perception::Spatial::Surfaces::SpatialSurfaceObserver^     m_surfaceObserver;
Windows::Perception::Spatial::Surfaces::SpatialSurfaceMeshOptions^  m_surfaceMeshOptions;
```

<span data-ttu-id="08da3-188">Conforme observado na seção anterior, você deve solicitar acesso aos dados de mapeamento espacial antes que seu aplicativo possa usá-lo.</span><span class="sxs-lookup"><span data-stu-id="08da3-188">As noted in the previous section, you must request access to spatial mapping data before your app can use it.</span></span> <span data-ttu-id="08da3-189">Esse acesso é concedido automaticamente no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="08da3-189">This access is granted automatically on the HoloLens.</span></span>

```cpp
// The surface mapping API reads information about the user's environment. The user must
// grant permission to the app to use this capability of the Windows Mixed Reality device.
auto initSurfaceObserverTask = create_task(SpatialSurfaceObserver::RequestAccessAsync());
initSurfaceObserverTask.then([this, coordinateSystem](Windows::Perception::Spatial::SpatialPerceptionAccessStatus status)
{
    if (status == SpatialPerceptionAccessStatus::Allowed)
    {
        // If status is allowed, we can create the surface observer.
        m_surfaceObserver = ref new SpatialSurfaceObserver();
```

<span data-ttu-id="08da3-190">Em seguida, você precisa configurar o observador de superfície para observar um volume delimitador específico.</span><span class="sxs-lookup"><span data-stu-id="08da3-190">Next, you need to configure the surface observer to observe a specific bounding volume.</span></span> <span data-ttu-id="08da3-191">Aqui, observamos uma caixa que é 20x20x5 metros, centralizada na origem do sistema de coordenadas.</span><span class="sxs-lookup"><span data-stu-id="08da3-191">Here, we observe a box that is 20x20x5 meters, centered at the origin of the coordinate system.</span></span>

```cpp
// The surface observer can now be configured as needed.

        // In this example, we specify one area to be observed using an axis-aligned
        // bounding box 20 meters in width and 5 meters in height and centered at the
        // origin.
        SpatialBoundingBox aabb =
        {
            { 0.f,  0.f, 0.f },
            {20.f, 20.f, 5.f },
        };

        SpatialBoundingVolume^ bounds = SpatialBoundingVolume::FromBox(coordinateSystem, aabb);
        m_surfaceObserver->SetBoundingVolume(bounds);
```

<span data-ttu-id="08da3-192">Observe que você pode definir vários volumes delimitadores em vez disso.</span><span class="sxs-lookup"><span data-stu-id="08da3-192">Note that you can set multiple bounding volumes instead.</span></span>

<span data-ttu-id="08da3-193">*Este é o pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="08da3-193">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolumes(/* iterable collection of bounding volumes*/);
```

<span data-ttu-id="08da3-194">Também é possível usar outras formas delimitadoras, como uma exibição frustum, ou uma caixa delimitadora que não esteja alinhada ao eixo.</span><span class="sxs-lookup"><span data-stu-id="08da3-194">It is also possible to use other bounding shapes - such as a view frustum, or a bounding box that is not axis aligned.</span></span>

<span data-ttu-id="08da3-195">*Este é o pseudocódigo:*</span><span class="sxs-lookup"><span data-stu-id="08da3-195">*This is pseudocode:*</span></span>

```cpp
m_surfaceObserver->SetBoundingVolume(
            SpatialBoundingVolume::FromFrustum(/*SpatialCoordinateSystem*/, /*SpatialBoundingFrustum*/)
            );
```

<span data-ttu-id="08da3-196">Se seu aplicativo precisar fazer algo diferente quando os dados de mapeamento de superfície não estiverem disponíveis, você poderá escrever código para responder ao caso em que o [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) não é **permitido** ; por exemplo, ele não será permitido em computadores com dispositivos de imersão anexados porque esses dispositivos não têm hardware para o mapeamento espacial.</span><span class="sxs-lookup"><span data-stu-id="08da3-196">If your app needs to do anything differently when surface mapping data is not available, you can write code to respond to the case where the [SpatialPerceptionAccessStatus](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.spatialperceptionaccessstatus.aspx) is not **Allowed** - for example, it will not be allowed on PCs with immersive devices attached because those devices don't have hardware for spatial mapping.</span></span> <span data-ttu-id="08da3-197">Para esses dispositivos, você deve confiar no estágio espacial para obter informações sobre a configuração do ambiente e do dispositivo do usuário.</span><span class="sxs-lookup"><span data-stu-id="08da3-197">For these devices, you should instead rely on the spatial stage for information about the user's environment and device configuration.</span></span>

### <a name="initialize-and-update-the-surface-mesh-collection"></a><span data-ttu-id="08da3-198">Inicializar e atualizar a coleção de malha da superfície</span><span class="sxs-lookup"><span data-stu-id="08da3-198">Initialize and update the surface mesh collection</span></span>

<span data-ttu-id="08da3-199">Se o observador de superfície foi criado com êxito, podemos continuar a inicializar nossa coleção de malha de superfície.</span><span class="sxs-lookup"><span data-stu-id="08da3-199">If the surface observer was successfully created, we can proceed to initialize our surface mesh collection.</span></span> <span data-ttu-id="08da3-200">Aqui, usamos a API do modelo de pull para obter o conjunto atual de superfícies observadas imediatamente:</span><span class="sxs-lookup"><span data-stu-id="08da3-200">Here, we use the pull model API to get the current set of observed surfaces right away:</span></span>

```cpp
auto mapContainingSurfaceCollection = m_surfaceObserver->GetObservedSurfaces();
        for (auto& pair : mapContainingSurfaceCollection)
        {
            // Store the ID and metadata for each surface.
            auto const& id = pair->Key;
            auto const& surfaceInfo = pair->Value;
            m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
        }
```

<span data-ttu-id="08da3-201">Há também um modelo de push disponível para obter dados de malha de superfície.</span><span class="sxs-lookup"><span data-stu-id="08da3-201">There is also a push model available to get surface mesh data.</span></span> <span data-ttu-id="08da3-202">Você tem a liberdade de criar seu aplicativo para usar apenas o modelo de pull se escolher, caso em que você vai sondar os dados a cada hora, com frequência, uma vez por quadro ou durante um período de tempo específico, como durante a configuração do jogo.</span><span class="sxs-lookup"><span data-stu-id="08da3-202">You are free to design your app to use only the pull model if you choose, in which case you'll poll for data every so often - say, once per frame - or during a specific time period, such as during game setup.</span></span> <span data-ttu-id="08da3-203">Nesse caso, o código acima é o que você precisa.</span><span class="sxs-lookup"><span data-stu-id="08da3-203">If so, the above code is what you need.</span></span>

<span data-ttu-id="08da3-204">Em nosso exemplo de código, optamos por demonstrar o uso de ambos os modelos para fins de pedagógicos.</span><span class="sxs-lookup"><span data-stu-id="08da3-204">In our code sample, we chose to demonstrate the use of both models for pedagogical purposes.</span></span> <span data-ttu-id="08da3-205">Aqui, assinamos um evento para receber dados de malha de superfície atualizados sempre que o sistema reconhece uma alteração.</span><span class="sxs-lookup"><span data-stu-id="08da3-205">Here, we subscribe to an event to receive up-to-date surface mesh data whenever the system recognizes a change.</span></span>

```cpp
m_surfaceObserver->ObservedSurfacesChanged += ref new TypedEventHandler<SpatialSurfaceObserver^, Platform::Object^>(
            bind(&HolographicDesktopAppMain::OnSurfacesChanged, this, _1, _2)
            );
```

<span data-ttu-id="08da3-206">Nosso exemplo de código também é configurado para responder a esses eventos.</span><span class="sxs-lookup"><span data-stu-id="08da3-206">Our code sample is also configured to respond to these events.</span></span> <span data-ttu-id="08da3-207">Vamos examinar como fazemos isso.</span><span class="sxs-lookup"><span data-stu-id="08da3-207">Let's walk through how we do this.</span></span>

<span data-ttu-id="08da3-208">**Observação:** Essa pode não ser a maneira mais eficiente para seu aplicativo manipular dados de malha.</span><span class="sxs-lookup"><span data-stu-id="08da3-208">**NOTE:** This might not be the most efficient way for your app to handle mesh data.</span></span> <span data-ttu-id="08da3-209">Esse código é escrito para fins de clareza e não é otimizado.</span><span class="sxs-lookup"><span data-stu-id="08da3-209">This code is written for clarity and is not optimized.</span></span>

<span data-ttu-id="08da3-210">Os dados de malha de superfície são fornecidos em um mapa somente leitura que armazena objetos [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) usando [Platform:: GUIDs](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) como valores de chave.</span><span class="sxs-lookup"><span data-stu-id="08da3-210">The surface mesh data is provided in a read-only map that stores [SpatialSurfaceInfo](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfaceinfo.aspx) objects using [Platform::Guids](https://msdn.microsoft.com/library/windows/desktop/aa373931.aspx) as key values.</span></span>

```cpp
IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection = sender->GetObservedSurfaces();
```

<span data-ttu-id="08da3-211">Para processar esses dados, examinamos primeiro os valores de chave que não estão em nossa coleção.</span><span class="sxs-lookup"><span data-stu-id="08da3-211">To process this data, we look first for key values that aren't in our collection.</span></span> <span data-ttu-id="08da3-212">Os detalhes sobre como os dados são armazenados em nosso aplicativo de exemplo serão apresentados posteriormente neste tópico.</span><span class="sxs-lookup"><span data-stu-id="08da3-212">Details on how the data is stored in our sample app will be presented later in this topic.</span></span>

```cpp
// Process surface adds and updates.
for (const auto& pair : surfaceCollection)
{
    auto id = pair->Key;
    auto surfaceInfo = pair->Value;

    if (m_meshCollection->HasSurface(id))
    {
        // Update existing surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
    else
    {
        // New surface.
        m_meshCollection->AddOrUpdateSurface(id, surfaceInfo);
    }
}
```

<span data-ttu-id="08da3-213">Também precisamos remover as malhas de superfície que estão em nossa coleção de malha de superfície, mas que não estão mais na coleção do sistema.</span><span class="sxs-lookup"><span data-stu-id="08da3-213">We also have to remove surface meshes that are in our surface mesh collection, but that aren't in the system collection anymore.</span></span> <span data-ttu-id="08da3-214">Para fazer isso, precisamos fazer algo semelhante ao oposto do que acabamos de mostrar para adicionar e atualizar malhas; Fazemos um loop sobre a coleção do aplicativo e verificamos se o **GUID** que temos está na coleção System.</span><span class="sxs-lookup"><span data-stu-id="08da3-214">To do so, we need to do something akin to the opposite of what we just showed for adding and updating meshes; we loop on our app's collection, and check to see if the **Guid** we have is in the system collection.</span></span> <span data-ttu-id="08da3-215">Se não estiver na coleção do sistema, remova-o da nossa.</span><span class="sxs-lookup"><span data-stu-id="08da3-215">If it's not in the system collection, we remove it from ours.</span></span>

<span data-ttu-id="08da3-216">Do nosso manipulador de eventos em AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="08da3-216">From our event handler in AppMain.cpp:</span></span>

```cpp
m_meshCollection->PruneMeshCollection(surfaceCollection);
```

<span data-ttu-id="08da3-217">A implementação da remoção de malha no RealtimeSurfaceMeshRenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="08da3-217">The implementation of mesh pruning in RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::PruneMeshCollection(IMapView<Guid, SpatialSurfaceInfo^>^ const& surfaceCollection)
{
    std::lock_guard<std::mutex> guard(m_meshCollectionLock);
    std::vector<Guid> idsToRemove;

    // Remove surfaces that moved out of the culling frustum or no longer exist.
    for (const auto& pair : m_meshCollection)
    {
        const auto& id = pair.first;
        if (!surfaceCollection->HasKey(id))
        {
            idsToRemove.push_back(id);
        }
    }

    for (const auto& id : idsToRemove)
    {
        m_meshCollection.erase(id);
    }
}
```

### <a name="acquire-and-use-surface-mesh-data-buffers"></a><span data-ttu-id="08da3-218">Adquirir e usar buffers de dados de malha de superfície</span><span class="sxs-lookup"><span data-stu-id="08da3-218">Acquire and use surface mesh data buffers</span></span>

<span data-ttu-id="08da3-219">Obter as informações de malha de superfície era tão fácil quanto extrair uma coleta de dados e processar atualizações para essa coleção.</span><span class="sxs-lookup"><span data-stu-id="08da3-219">Getting the surface mesh information was as easy as pulling a data collection and processing updates to that collection.</span></span> <span data-ttu-id="08da3-220">Agora, entraremos em detalhes sobre como você pode usar os dados.</span><span class="sxs-lookup"><span data-stu-id="08da3-220">Now, we'll go into detail on how you can use the data.</span></span>

<span data-ttu-id="08da3-221">Em nosso exemplo de código, optamos por usar as malhas de superfície para renderização.</span><span class="sxs-lookup"><span data-stu-id="08da3-221">In our code example, we chose to use the surface meshes for rendering.</span></span> <span data-ttu-id="08da3-222">Esse é um cenário comum para os hologramas occluding por trás das superfícies do mundo real.</span><span class="sxs-lookup"><span data-stu-id="08da3-222">This is a common scenario for occluding holograms behind real-world surfaces.</span></span> <span data-ttu-id="08da3-223">Você também pode renderizar as malhas ou renderizar as versões processadas delas para mostrar ao usuário quais áreas da sala são verificadas antes de começar a fornecer a funcionalidade do aplicativo ou do jogo.</span><span class="sxs-lookup"><span data-stu-id="08da3-223">You can also render the meshes, or render processed versions of them, to show the user what areas of the room are scanned before you start providing app or game functionality.</span></span>

<span data-ttu-id="08da3-224">O exemplo de código inicia o processo quando recebe atualizações de malha de superfície do manipulador de eventos que descrevemos na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="08da3-224">The code sample starts the process when it receives surface mesh updates from the event handler that we described in the previous section.</span></span> <span data-ttu-id="08da3-225">A linha importante de código nessa função é a chamada para atualizar a *malha* de superfície: neste momento, já processamos as informações de malha e estamos prestes a obter os dados de vértice e de índice para uso, como vemos.</span><span class="sxs-lookup"><span data-stu-id="08da3-225">The important line of code in this function is the call to update the surface *mesh* : by this time we have already processed the mesh info, and we are about to get the vertex and index data for use as we see fit.</span></span>

<span data-ttu-id="08da3-226">De RealtimeSurfaceMeshRenderer. cpp:</span><span class="sxs-lookup"><span data-stu-id="08da3-226">From RealtimeSurfaceMeshRenderer.cpp:</span></span>

```cpp
void RealtimeSurfaceMeshRenderer::AddOrUpdateSurface(Guid id, SpatialSurfaceInfo^ newSurface)
{
    auto options = ref new SpatialSurfaceMeshOptions();
    options->IncludeVertexNormals = true;

    auto createMeshTask = create_task(newSurface->TryComputeLatestMeshAsync(1000, options));
    createMeshTask.then([this, id](SpatialSurfaceMesh^ mesh)
    {
        if (mesh != nullptr)
        {
            std::lock_guard<std::mutex> guard(m_meshCollectionLock);
            '''m_meshCollection[id].UpdateSurface(mesh);'''
        }
    }, task_continuation_context::use_current());
}
```

<span data-ttu-id="08da3-227">Nosso código de exemplo foi projetado para que uma classe de dados, **SurfaceMesh** , lide com processamento e renderização de dados de malha.</span><span class="sxs-lookup"><span data-stu-id="08da3-227">Our sample code is designed so that a data class, **SurfaceMesh** , handles mesh data processing and rendering.</span></span> <span data-ttu-id="08da3-228">Essas malhas são o que o **RealtimeSurfaceMeshRenderer** realmente mantém um mapa.</span><span class="sxs-lookup"><span data-stu-id="08da3-228">These meshes are what the **RealtimeSurfaceMeshRenderer** actually keeps a map of.</span></span> <span data-ttu-id="08da3-229">Cada um tem uma referência para o SpatialSurfaceMesh de origem e nós o usamos sempre que precisamos acessar o vértice de malha ou buffers de índice, ou obter uma transformação para a malha.</span><span class="sxs-lookup"><span data-stu-id="08da3-229">Each one has a reference to the SpatialSurfaceMesh it came from, and we use it any time that we need to access the mesh vertex or index buffers, or get a transform for the mesh.</span></span> <span data-ttu-id="08da3-230">Por enquanto, sinalizamos a malha como precisa de uma atualização.</span><span class="sxs-lookup"><span data-stu-id="08da3-230">For now, we flag the mesh as needing an update.</span></span>

<span data-ttu-id="08da3-231">De SurfaceMesh. cpp:</span><span class="sxs-lookup"><span data-stu-id="08da3-231">From SurfaceMesh.cpp:</span></span>

```cpp
void SurfaceMesh::UpdateSurface(SpatialSurfaceMesh^ surfaceMesh)
{
    m_surfaceMesh = surfaceMesh;
    m_updateNeeded = true;
}
```

<span data-ttu-id="08da3-232">Na próxima vez que a malha for solicitada a desenhar, ela verificará o sinalizador primeiro.</span><span class="sxs-lookup"><span data-stu-id="08da3-232">Next time the mesh is asked to draw itself, it will check the flag first.</span></span> <span data-ttu-id="08da3-233">Se uma atualização for necessária, os buffers de vértice e de índice serão atualizados na GPU.</span><span class="sxs-lookup"><span data-stu-id="08da3-233">If an update is needed, the vertex and index buffers will be updated on the GPU.</span></span>

```cpp
void SurfaceMesh::CreateDeviceDependentResources(ID3D11Device* device)
{
    m_indexCount = m_surfaceMesh->TriangleIndices->ElementCount;
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }
```

<span data-ttu-id="08da3-234">Primeiro, adquirimos os buffers de dados brutos:</span><span class="sxs-lookup"><span data-stu-id="08da3-234">First, we acquire the raw data buffers:</span></span>

```cpp
Windows::Storage::Streams::IBuffer^ positions = m_surfaceMesh->VertexPositions->Data;
    Windows::Storage::Streams::IBuffer^ normals   = m_surfaceMesh->VertexNormals->Data;
    Windows::Storage::Streams::IBuffer^ indices   = m_surfaceMesh->TriangleIndices->Data;
```

<span data-ttu-id="08da3-235">Em seguida, criamos buffers de dispositivo Direct3D com os dados de malha fornecidos pelo HoloLens:</span><span class="sxs-lookup"><span data-stu-id="08da3-235">Then, we create Direct3D device buffers with the mesh data provided by the HoloLens:</span></span>

```cpp
CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, positions, m_vertexPositions.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_VERTEX_BUFFER, normals,   m_vertexNormals.GetAddressOf());
    CreateDirectXBuffer(device, D3D11_BIND_INDEX_BUFFER,  indices,   m_triangleIndices.GetAddressOf());

    // Create a constant buffer to control mesh position.
    CD3D11_BUFFER_DESC constantBufferDesc(sizeof(SurfaceTransforms), D3D11_BIND_CONSTANT_BUFFER);
    DX::ThrowIfFailed(
        device->CreateBuffer(
            &constantBufferDesc,
            nullptr,
            &m_modelTransformBuffer
            )
        );

    m_loadingComplete = true;
}
```

<span data-ttu-id="08da3-236">**Observação:** Para a função auxiliar CreateDirectXBuffer usada no trecho anterior, consulte o exemplo de código de mapeamento de superfície: SurfaceMesh. cpp, GetDataFromIBuffer. h.</span><span class="sxs-lookup"><span data-stu-id="08da3-236">**NOTE:** For the CreateDirectXBuffer helper function used in the previous snippet, see the Surface Mapping code sample: SurfaceMesh.cpp, GetDataFromIBuffer.h.</span></span> <span data-ttu-id="08da3-237">Agora a criação do recurso do dispositivo está concluída e a malha é considerada como carregada e pronta para atualização e renderização.</span><span class="sxs-lookup"><span data-stu-id="08da3-237">Now the device resource creation is complete, and the mesh is considered to be loaded and ready for update and render.</span></span>

### <a name="update-and-render-surface-meshes"></a><span data-ttu-id="08da3-238">Atualizar e renderizar malhas de superfície</span><span class="sxs-lookup"><span data-stu-id="08da3-238">Update and render surface meshes</span></span>

<span data-ttu-id="08da3-239">Nossa classe SurfaceMesh tem uma função de atualização especializada.</span><span class="sxs-lookup"><span data-stu-id="08da3-239">Our SurfaceMesh class has a specialized update function.</span></span> <span data-ttu-id="08da3-240">Cada [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) tem sua própria transformação, e nosso exemplo usa o sistema de coordenadas atual para nosso **SpatialStationaryReferenceFrame** para adquirir a transformação.</span><span class="sxs-lookup"><span data-stu-id="08da3-240">Each [SpatialSurfaceMesh](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.surfaces.spatialsurfacemesh.aspx) has its own transform, and our sample uses the current coordinate system for our **SpatialStationaryReferenceFrame** to acquire the transform.</span></span> <span data-ttu-id="08da3-241">Em seguida, ele atualiza o buffer de constante do modelo na GPU.</span><span class="sxs-lookup"><span data-stu-id="08da3-241">Then it updates the model constant buffer on the GPU.</span></span>

```cpp
void SurfaceMesh::UpdateTransform(
    ID3D11DeviceContext* context,
    SpatialCoordinateSystem^ baseCoordinateSystem
    )
{
    if (m_indexCount < 3)
    {
        // Not enough indices to draw a triangle.
        return;
    }

    XMMATRIX transform = XMMatrixIdentity();

    auto tryTransform = m_surfaceMesh->CoordinateSystem->TryGetTransformTo(baseCoordinateSystem);
    if (tryTransform != nullptr)
    {
        transform = XMLoadFloat4x4(&tryTransform->Value);
    }

    XMMATRIX scaleTransform = XMMatrixScalingFromVector(XMLoadFloat3(&m_surfaceMesh->VertexPositionScale));

    XMStoreFloat4x4(
        &m_constantBufferData.vertexWorldTransform,
        XMMatrixTranspose(
            scaleTransform * transform
            )
        );

    // Normals don't need to be translated.
    XMMATRIX normalTransform = transform;
    normalTransform.r[3] = XMVectorSet(0.f, 0.f, 0.f, XMVectorGetW(normalTransform.r[3]));
    XMStoreFloat4x4(
        &m_constantBufferData.normalWorldTransform,
        XMMatrixTranspose(
            normalTransform
        )
        );

    if (!m_loadingComplete)
    {
        return;
    }

    context->UpdateSubresource(
        m_modelTransformBuffer.Get(),
        0,
        NULL,
        &m_constantBufferData,
        0,
        0
        );
}
```

<span data-ttu-id="08da3-242">Quando é hora de renderizar malhas de superfície, fazemos um trabalho de preparação antes de renderizar a coleção.</span><span class="sxs-lookup"><span data-stu-id="08da3-242">When it's time to render surface meshes, we do some prep work before rendering the collection.</span></span> <span data-ttu-id="08da3-243">Configuramos o pipeline do sombreador para a configuração de renderização atual e configuramos o estágio do assembler de entrada.</span><span class="sxs-lookup"><span data-stu-id="08da3-243">We set up the shader pipeline for the current rendering configuration, and we set up the input assembler stage.</span></span> <span data-ttu-id="08da3-244">Observe que a classe auxiliar da câmera Holographic **CameraResources. cpp** já configurou o buffer constante de exibição/projeção agora.</span><span class="sxs-lookup"><span data-stu-id="08da3-244">Note that the holographic camera helper class **CameraResources.cpp** already has set up the view/projection constant buffer by now.</span></span>

<span data-ttu-id="08da3-245">De **RealtimeSurfaceMeshRenderer:: render** :</span><span class="sxs-lookup"><span data-stu-id="08da3-245">From **RealtimeSurfaceMeshRenderer::Render** :</span></span>

```cpp
auto context = m_deviceResources->GetD3DDeviceContext();

context->IASetPrimitiveTopology(D3D11_PRIMITIVE_TOPOLOGY_TRIANGLELIST);
context->IASetInputLayout(m_inputLayout.Get());

// Attach our vertex shader.
context->VSSetShader(
    m_vertexShader.Get(),
    nullptr,
    0
    );

// The constant buffer is per-mesh, and will be set as such.

if (depthOnly)
{
    // Explicitly detach the later shader stages.
    context->GSSetShader(nullptr, nullptr, 0);
    context->PSSetShader(nullptr, nullptr, 0);
}
else
{
    if (!m_usingVprtShaders)
    {
        // Attach the passthrough geometry shader.
        context->GSSetShader(
            m_geometryShader.Get(),
            nullptr,
            0
            );
    }

    // Attach our pixel shader.
    context->PSSetShader(
        m_pixelShader.Get(),
        nullptr,
        0
        );
}
```

<span data-ttu-id="08da3-246">Quando isso for feito, vamos fazer um loop em nossas malhas e dizer a cada uma delas para se desenhar.</span><span class="sxs-lookup"><span data-stu-id="08da3-246">Once this is done, we loop on our meshes and tell each one to draw itself.</span></span> <span data-ttu-id="08da3-247">**Observação:** Este código de exemplo não é otimizado para usar qualquer tipo de remoção de frustum, mas você deve incluir esse recurso em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08da3-247">**NOTE:** This sample code is not optimized to use any sort of frustum culling, but you should include this feature in your app.</span></span>

```cpp
std::lock_guard<std::mutex> guard(m_meshCollectionLock);

auto device = m_deviceResources->GetD3DDevice();

// Draw the meshes.
for (auto& pair : m_meshCollection)
{
    auto& id = pair.first;
    auto& surfaceMesh = pair.second;

    surfaceMesh.Draw(device, context, m_usingVprtShaders, isStereo);
}
```

<span data-ttu-id="08da3-248">As malhas individuais são responsáveis pela configuração do vértice e do buffer de índice, Stride e buffer constante de transformação de modelo.</span><span class="sxs-lookup"><span data-stu-id="08da3-248">The individual meshes are responsible for setting up the vertex and index buffer, stride, and model transform constant buffer.</span></span> <span data-ttu-id="08da3-249">Assim como no cubo de rotação no modelo de aplicativo Holographic do Windows, renderizamos para buffers estereoscópico usando instanciação.</span><span class="sxs-lookup"><span data-stu-id="08da3-249">As with the spinning cube in the Windows Holographic app template, we render to stereoscopic buffers using instancing.</span></span>

<span data-ttu-id="08da3-250">De **SurfaceMesh::D bruto** :</span><span class="sxs-lookup"><span data-stu-id="08da3-250">From **SurfaceMesh::Draw** :</span></span>

```cpp
// The vertices are provided in {vertex, normal} format

const auto& vertexStride = m_surfaceMesh->VertexPositions->Stride;
const auto& normalStride = m_surfaceMesh->VertexNormals->Stride;

UINT strides [] = { vertexStride, normalStride };
UINT offsets [] = { 0, 0 };
ID3D11Buffer* buffers [] = { m_vertexPositions.Get(), m_vertexNormals.Get() };

context->IASetVertexBuffers(
    0,
    ARRAYSIZE(buffers),
    buffers,
    strides,
    offsets
    );

const auto& indexFormat = static_cast<DXGI_FORMAT>(m_surfaceMesh->TriangleIndices->Format);

context->IASetIndexBuffer(
    m_triangleIndices.Get(),
    indexFormat,
    0
    );

context->VSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

if (!usingVprtShaders)
{
    context->GSSetConstantBuffers(
        0,
        1,
        m_modelTransformBuffer.GetAddressOf()
        );
}

context->PSSetConstantBuffers(
    0,
    1,
    m_modelTransformBuffer.GetAddressOf()
    );

context->DrawIndexedInstanced(
    m_indexCount,       // Index count per instance.
    isStereo ? 2 : 1,   // Instance count.
    0,                  // Start index location.
    0,                  // Base vertex location.
    0                   // Start instance location.
    );
```

### <a name="rendering-choices-with-surface-mapping"></a><span data-ttu-id="08da3-251">Opções de renderização com mapeamento de superfície</span><span class="sxs-lookup"><span data-stu-id="08da3-251">Rendering choices with Surface Mapping</span></span>

<span data-ttu-id="08da3-252">O exemplo de código de mapeamento de superfície oferece código para renderização oclusão de dados de malha de superfície e para renderização na tela de dados de malha de superfície.</span><span class="sxs-lookup"><span data-stu-id="08da3-252">The Surface Mapping code sample offers code for occlusion-only rendering of surface mesh data, and for on-screen rendering of surface mesh data.</span></span> <span data-ttu-id="08da3-253">Qual caminho você escolhe-ou ambos-depende do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="08da3-253">Which path you choose - or both - depends on your application.</span></span> <span data-ttu-id="08da3-254">Vamos percorrer as duas configurações deste documento.</span><span class="sxs-lookup"><span data-stu-id="08da3-254">We'll walk through both configurations in this document.</span></span>

<span data-ttu-id="08da3-255">**Renderizando buffers oclusão para efeito Holographic**</span><span class="sxs-lookup"><span data-stu-id="08da3-255">**Rendering occlusion buffers for holographic effect**</span></span>

<span data-ttu-id="08da3-256">Comece limpando a exibição de destino de renderização para a câmera virtual atual.</span><span class="sxs-lookup"><span data-stu-id="08da3-256">Start by clearing the render target view for the current virtual camera.</span></span>

<span data-ttu-id="08da3-257">De AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="08da3-257">From AppMain.cpp:</span></span>

```cpp
context->ClearRenderTargetView(pCameraResources->GetBackBufferRenderTargetView(), DirectX::Colors::Transparent);
```

<span data-ttu-id="08da3-258">Essa é uma passagem de "pré-processamento".</span><span class="sxs-lookup"><span data-stu-id="08da3-258">This is a "pre-rendering" pass.</span></span> <span data-ttu-id="08da3-259">Aqui, criamos um buffer oclusão solicitando que o processador de malha processe apenas a profundidade.</span><span class="sxs-lookup"><span data-stu-id="08da3-259">Here, we create an occlusion buffer by asking the mesh renderer to render only depth.</span></span> <span data-ttu-id="08da3-260">Nessa configuração, não anexamos uma exibição de destino de renderização e o processador de malha define o estágio do sombreador de pixel como **nullptr** para que a GPU não se preocupe em desenhar pixels.</span><span class="sxs-lookup"><span data-stu-id="08da3-260">In this configuration, we don't attach a render target view, and the mesh renderer sets the pixel shader stage to **nullptr** so that the GPU doesn't bother to draw pixels.</span></span> <span data-ttu-id="08da3-261">A geometria será rasterizada para o buffer de profundidade e o pipeline de gráficos será interrompido.</span><span class="sxs-lookup"><span data-stu-id="08da3-261">The geometry will be rasterized to the depth buffer, and the graphics pipeline will stop there.</span></span>

```cpp
// Pre-pass rendering: Create occlusion buffer from Surface Mapping data.
context->ClearDepthStencilView(pCameraResources->GetSurfaceDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to null, and set the depth target occlusion buffer.
// We will use this same buffer as a shader resource when drawing holograms.
context->OMSetRenderTargets(0, nullptr, pCameraResources->GetSurfaceOcclusionDepthStencilView());

// The first pass is a depth-only pass that generates an occlusion buffer we can use to know which
// hologram pixels are hidden behind surfaces in the environment.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), true);
```

<span data-ttu-id="08da3-262">Podemos desenhar hologramas com um teste de profundidade extra em relação ao buffer oclusão de mapeamento de superfície.</span><span class="sxs-lookup"><span data-stu-id="08da3-262">We can draw holograms with an extra depth test against the Surface Mapping occlusion buffer.</span></span> <span data-ttu-id="08da3-263">Neste exemplo de código, renderizaremos pixels no cubo em uma cor diferente se estiverem atrás de uma superfície.</span><span class="sxs-lookup"><span data-stu-id="08da3-263">In this code sample, we render pixels on the cube a different color if they are behind a surface.</span></span>

<span data-ttu-id="08da3-264">De AppMain. cpp:</span><span class="sxs-lookup"><span data-stu-id="08da3-264">From AppMain.cpp:</span></span>

```cpp
// Hologram rendering pass: Draw holographic content.
context->ClearDepthStencilView(pCameraResources->GetHologramDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target, and set the depth target drawing buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetHologramDepthStencilView());

// Render the scene objects.
// In this example, we draw a special effect that uses the occlusion buffer we generated in the
// Pre-Pass step to render holograms using X-Ray Vision when they are behind physical objects.
m_xrayCubeRenderer->Render(
    pCameraResources->IsRenderingStereoscopic(),
    pCameraResources->GetSurfaceOcclusionShaderResourceView(),
    pCameraResources->GetHologramOcclusionShaderResourceView(),
    pCameraResources->GetDepthTextureSamplerState()
    );
```

<span data-ttu-id="08da3-265">Com base no código de SpecialEffectPixelShader. HLSL:</span><span class="sxs-lookup"><span data-stu-id="08da3-265">Based on code from SpecialEffectPixelShader.hlsl:</span></span>

```cpp
// Draw boundaries
min16int surfaceSum = GatherDepthLess(envDepthTex, uniSamp, input.pos.xy, pixelDepth, input.idx.x);

if (surfaceSum <= -maxSum)
{
    // The pixel and its neighbors are behind the surface.
    // Return the occluded 'X-ray' color.
    return min16float4(0.67f, 0.f, 0.f, 1.0f);
}
else if (surfaceSum < maxSum)
{
    // The pixel and its neighbors are a mix of in front of and behind the surface.
    // Return the silhouette edge color.
    return min16float4(1.f, 1.f, 1.f, 1.0f);
}
else
{
    // The pixel and its neighbors are all in front of the surface.
    // Return the color of the hologram.
    return min16float4(input.color, 1.0f);
}
```

<span data-ttu-id="08da3-266">**Observação:** Para nossa rotina **GatherDepthLess** , consulte o exemplo de código de mapeamento de superfície: SpecialEffectPixelShader. HLSL.</span><span class="sxs-lookup"><span data-stu-id="08da3-266">**Note:** For our **GatherDepthLess** routine, see the Surface Mapping code sample: SpecialEffectPixelShader.hlsl.</span></span>

<span data-ttu-id="08da3-267">**Renderizando dados de malha da superfície para a exibição**</span><span class="sxs-lookup"><span data-stu-id="08da3-267">**Rendering surface mesh data to the display**</span></span>

<span data-ttu-id="08da3-268">Também podemos simplesmente desenhar as malhas de superfície para os buffers de vídeo estéreo.</span><span class="sxs-lookup"><span data-stu-id="08da3-268">We can also just draw the surface meshes to the stereo display buffers.</span></span> <span data-ttu-id="08da3-269">Optamos por desenhar faces completas com iluminação, mas você está livre para desenhar wireframe, processar malhas antes de renderizar, aplicar um mapa de textura e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="08da3-269">We chose to draw full faces with lighting, but you're free to draw wireframe, process meshes before rendering, apply a texture map, and so on.</span></span>

<span data-ttu-id="08da3-270">Aqui, nosso exemplo de código diz ao renderizador de malha para desenhar a coleção.</span><span class="sxs-lookup"><span data-stu-id="08da3-270">Here, our code sample tells the mesh renderer to draw the collection.</span></span> <span data-ttu-id="08da3-271">Desta vez, não especificamos uma passagem somente de profundidade, portanto, ele anexará um sombreador de pixel e concluirá o pipeline de renderização usando os destinos que especificamos para a câmera virtual atual.</span><span class="sxs-lookup"><span data-stu-id="08da3-271">This time we don't specify a depth-only pass, so it will attach a pixel shader and complete the rendering pipeline using the targets that we specified for the current virtual camera.</span></span>

```cpp
// Spatial Mapping mesh rendering pass: Draw Spatial Mapping mesh over the world.
context->ClearDepthStencilView(pCameraResources->GetSurfaceOcclusionDepthStencilView(), D3D11_CLEAR_DEPTH | D3D11_CLEAR_STENCIL, 1.0f, 0);

// Set the render target to the current holographic camera's back buffer, and set the depth buffer.
ID3D11RenderTargetView *const targets[1] = { pCameraResources->GetBackBufferRenderTargetView() };
context->OMSetRenderTargets(1, targets, pCameraResources->GetSurfaceDepthStencilView());

// This drawing pass renders the surface meshes to the stereoscopic display. The user will be
// able to see them while wearing the device.
m_meshCollection->Render(pCameraResources->IsRenderingStereoscopic(), false);
```

## <a name="see-also"></a><span data-ttu-id="08da3-272">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08da3-272">See also</span></span>
* [<span data-ttu-id="08da3-273">Como criar um projeto holográfico do DirectX</span><span class="sxs-lookup"><span data-stu-id="08da3-273">Creating a holographic DirectX project</span></span>](creating-a-holographic-directx-project.md)
* [<span data-ttu-id="08da3-274">API Windows. percepção. espacial</span><span class="sxs-lookup"><span data-stu-id="08da3-274">Windows.Perception.Spatial API</span></span>](https://msdn.microsoft.com/library/windows/apps/windows.perception.spatial.aspx)
