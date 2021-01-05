---
title: Recursos com suporte do plug-in OpenXR no Unity
description: Descubra os recursos que o OpenXR dá suporte para desenvolvimento de realidade misturada no Unity.
author: hferrone
ms.author: alexturn
ms.date: 12/15/2020
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 94ec7ae6c89dea8f953fea6f4c794ca51e044d87
ms.sourcegitcommit: 5784336a780486d05db6a627839efe47f08fac36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97880580"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="cbce7-104">Recursos com suporte da realidade misturada OpenXR no Unity</span><span class="sxs-lookup"><span data-stu-id="cbce7-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="cbce7-105">O pacote de **plug-in OpenXR da realidade mista** é uma extensão do **plug-in OpenXR** do Unity e dá suporte a um conjunto de recursos para headsets do HoloLens 2 e do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="cbce7-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="cbce7-106">Antes de continuar, certifique-se de ter instalado o **Unity 2020,2** ou posterior, **OpenXR plugin versão 0.1.1** ou posterior e seu projeto de Unity está [configurado para OpenXR](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="cbce7-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.1** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="cbce7-107">O que tem suporte</span><span class="sxs-lookup"><span data-stu-id="cbce7-107">What's supported</span></span>

<span data-ttu-id="cbce7-108">Atualmente, há suporte para os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="cbce7-108">The following features are currently supported:</span></span>

* <span data-ttu-id="cbce7-109">Dá suporte a aplicativos UWP para o HoloLens 2 e aplicativos Win32 VR para headsets de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="cbce7-109">Supports both UWP applications for HoloLens 2 and Win32 VR applications for Windows Mixed Reality headsets.</span></span>
* <span data-ttu-id="cbce7-110">Otimiza o pacote UWP e a interação CoreWindow para aplicativos do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cbce7-110">Optimizes UWP package and CoreWindow interaction for HoloLens 2 applications.</span></span>
* <span data-ttu-id="cbce7-111">Controle de escala mundial usando âncoras e espaço não associado.</span><span class="sxs-lookup"><span data-stu-id="cbce7-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="cbce7-112">[API de armazenamento de ancoragem para persistir âncoras](#anchors-and-anchor-persistence) no armazenamento local do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cbce7-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="cbce7-113">[Controlador de movimento e interações de mão](#motion-controller-and-hand-interactions), incluindo o novo controlador do HP reverberate G2.</span><span class="sxs-lookup"><span data-stu-id="cbce7-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="cbce7-114">Controle de mão articulado usando 26 junções e entradas de raio conjuntas.</span><span class="sxs-lookup"><span data-stu-id="cbce7-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="cbce7-115">Observe a interação olhar no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cbce7-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="cbce7-116">Localizando a câmera de foto/vídeo (PV) no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cbce7-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="cbce7-117">A realidade misturada é a captura usando o processamento de 3ª vista por meio da câmera VP.</span><span class="sxs-lookup"><span data-stu-id="cbce7-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="cbce7-118">Dá suporte à ["reprodução" para o HoloLens 2 com o aplicativo de comunicação remota do Holographic](#holographic-remoting-in-unity-editor-play-mode), permitindo que os desenvolvedores depurem scripts sem compilar e implantar no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cbce7-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="cbce7-119">Compatível com o MRTK Unity 2.5.2 e mais recente por meio do suporte do provedor MRTK OpenXR.</span><span class="sxs-lookup"><span data-stu-id="cbce7-119">Compatible with MRTK Unity 2.5.2 and newer through MRTK OpenXR provider support.</span></span> <span data-ttu-id="cbce7-120">[Consulte a documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) para começar.</span><span class="sxs-lookup"><span data-stu-id="cbce7-120">[See the MRTK documentation](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithMRTKAndXRSDK.html) to get started.</span></span>
* <span data-ttu-id="cbce7-121">Compatível com o Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) ou posterior</span><span class="sxs-lookup"><span data-stu-id="cbce7-121">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later</span></span>

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="cbce7-122">Holographic comunicação remota no modo de reprodução do editor do Unity</span><span class="sxs-lookup"><span data-stu-id="cbce7-122">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="cbce7-123">Criar um projeto de Unity do UWP no projeto do Visual Studio e, em seguida, compactá-lo e implantá-lo em um dispositivo HoloLens 2 pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="cbce7-123">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="cbce7-124">Uma solução é habilitar a comunicação remota do editor do Holographic, que permite que você depure seu script C# usando o modo "Play" diretamente em um dispositivo de HoloLens 2 em sua rede.</span><span class="sxs-lookup"><span data-stu-id="cbce7-124">One solution is to enable the Holographic Editor Remoting, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="cbce7-125">Esse cenário evita a sobrecarga de criar e implantar um pacote UWP para um dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="cbce7-125">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="cbce7-126">Primeiro, você precisa [instalar o aplicativo de player de comunicação remota do Holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do repositório no seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="cbce7-126">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from Store on your HoloLens 2</span></span>
2. <span data-ttu-id="cbce7-127">Execute o aplicativo de player de comunicação remota do Holographic no HoloLens 2 e você verá o número de versão e o endereço IP para se conectar</span><span class="sxs-lookup"><span data-stu-id="cbce7-127">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="cbce7-128">Você precisará do v 2.4 ou posterior para trabalhar com o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="cbce7-128">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Captura de tela do player de comunicação remota do Holographic em execução no HoloLens](images/openxr-features-img-01.png)

3. <span data-ttu-id="cbce7-130">Abra **configurações do projeto de > de edição**, navegue até **Gerenciamento de plug-in de XR** e marque a caixa conjunto de recursos do **Windows Mixed Realm** :</span><span class="sxs-lookup"><span data-stu-id="cbce7-130">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-features-img-02.png)

4. <span data-ttu-id="cbce7-132">Expanda a seção **recursos** em **OpenXR** e selecione **Mostrar tudo**</span><span class="sxs-lookup"><span data-stu-id="cbce7-132">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
5. <span data-ttu-id="cbce7-133">Marque a caixa de seleção **comunicação remota do editor de Holographic** e insira o endereço IP obtido do aplicativo de comunicação remota do Holographic:</span><span class="sxs-lookup"><span data-stu-id="cbce7-133">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Captura de tela do painel de configurações do projeto aberto no editor do Unity com recursos realçados](images/openxr-features-img-03.png)

<span data-ttu-id="cbce7-135">Agora você pode clicar no botão "reproduzir" para reproduzir seu aplicativo do Unity no aplicativo de comunicação remota do Holographic em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cbce7-135">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="cbce7-136">Você também pode [anexar o Visual Studio ao Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) para depurar scripts C# no modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="cbce7-136">You can also [attach Visual Studio to Unity](https://docs.microsoft.com/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="cbce7-137">A partir da versão 0.1.0, o tempo de execução de comunicação remota do Holographic não dá suporte a âncoras, e as funcionalidades de ARAnchorManager não funcionarão por meio de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="cbce7-137">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="cbce7-138">Esse recurso estará disponível em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="cbce7-138">This feature is coming in future releases.</span></span>

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="cbce7-139">Âncoras e persistência de ancoragem</span><span class="sxs-lookup"><span data-stu-id="cbce7-139">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="cbce7-140">O plug-in Mixed Reality OpenXR fornece a funcionalidade de ancoragem básica por meio de uma implementação de ARFoundation **ARAnchorManager** do Unity.</span><span class="sxs-lookup"><span data-stu-id="cbce7-140">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="cbce7-141">Para aprender as noções básicas sobre **ARAnchor** s no ARFoundation, visite o [manual do ARFoundation para o gerente de ancoragem ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="cbce7-141">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="cbce7-142">A partir da versão 0.1.0, esse plug-in dá suporte a toda a funcionalidade ARAnchorManager, exceto a criação de âncoras anexadas a um plano, que está chegando em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="cbce7-142">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="cbce7-143">Persistência de ancoragem e XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="cbce7-143">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="cbce7-144">Uma API adicional chamada **XRAnchorStore** permite que as âncoras sejam persistidas entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="cbce7-144">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="cbce7-145">O XRAnchorStore é uma representação das âncoras salvas em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cbce7-145">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="cbce7-146">As âncoras podem persistir de **ARAnchors** na cena do Unity, carregadas do armazenamento para o New **ARAnchors** ou excluídas do armazenamento.</span><span class="sxs-lookup"><span data-stu-id="cbce7-146">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="cbce7-147">Essas âncoras devem ser salvas e carregadas no mesmo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="cbce7-147">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="cbce7-148">O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="cbce7-148">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

``` cs
public class Microsoft.MixedReality.ARSubsystems.XRAnchorStore
{
    // A list of all persisted anchors, which can be loaded.
    public IReadOnlyList<string> PersistedAnchorNames { get; }

    // Clear all persisted anchors
    public void Clear();

    // Load a single persisted anchor by name. The ARAnchorManager will create this new anchor and report it in
    // the ARAnchorManager.anchorsChanged event. The TrackableId returned here is the same TrackableId the
    // ARAnchor will have when it is instantiated.
    public TrackableId LoadAnchor(string name);

    // Attempts to persist an existing ARAnchor with the given TrackableId to the local store. Returns true if
    // the storage is successful, false otherwise.
    public bool TryPersistAnchor(string name, TrackableId trackableId);

    // Removes a single persisted anchor from the anchor store. This will not affect any ARAnchors in the Unity
    // scene, only the anchors in storage.
    public void UnpersistAnchor(string name);
}
```

<span data-ttu-id="cbce7-149">Para carregar o XRAnchorStore, o plug-in fornece um método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="cbce7-149">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="cbce7-150">Para usar esse método de extensão, acesse-o de um subsistema de ARAnchorManager da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbce7-150">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="cbce7-151">Para ver um exemplo completo de persistência/descontinuação de âncoras, confira o exemplo âncoras-> ancoras Games e o script AnchorsSample.cs na [cena de exemplo do plugin OpenXR de realidade misturada](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="cbce7-151">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de tela do painel hierarquia aberta no editor do Unity com o exemplo âncoras realçado](images/openxr-features-img-04.png)

![Captura de tela do painel Inspetor aberto no editor do Unity com o script de exemplo âncoras realçado](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="cbce7-154">Controlador de movimento e interações de mão</span><span class="sxs-lookup"><span data-stu-id="cbce7-154">Motion controller and hand interactions</span></span>

<span data-ttu-id="cbce7-155">Para aprender as noções básicas sobre interações de realidade misturada no Unity, visite o [manual do Unity para entrada do Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="cbce7-155">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="cbce7-156">Esta documentação do Unity aborda os mapeamentos de entradas específicas do controlador para **InputFeatureUsage** s mais generalizadas, como as entradas de XR disponíveis podem ser identificadas e categorizadas, como ler dados dessas entradas e muito mais.</span><span class="sxs-lookup"><span data-stu-id="cbce7-156">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="cbce7-157">O plug-in Mixed Reality OpenXR fornece perfis de interação de entrada adicionais, mapeados para os **InputFeatureUsage** padrão, conforme detalhado abaixo:</span><span class="sxs-lookup"><span data-stu-id="cbce7-157">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="cbce7-158">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="cbce7-158">InputFeatureUsage</span></span> | <span data-ttu-id="cbce7-159">Controlador do HP reverbo G2 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="cbce7-159">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="cbce7-160">Mão do HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="cbce7-160">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="cbce7-161">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="cbce7-161">primary2DAxis</span></span> | <span data-ttu-id="cbce7-162">Botões</span><span class="sxs-lookup"><span data-stu-id="cbce7-162">Joystick</span></span> | |
| <span data-ttu-id="cbce7-163">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="cbce7-163">primary2DAxisClick</span></span> | <span data-ttu-id="cbce7-164">Joystick – clique em</span><span class="sxs-lookup"><span data-stu-id="cbce7-164">Joystick - Click</span></span> | |
| <span data-ttu-id="cbce7-165">gatilho</span><span class="sxs-lookup"><span data-stu-id="cbce7-165">trigger</span></span> | <span data-ttu-id="cbce7-166">Gatilho</span><span class="sxs-lookup"><span data-stu-id="cbce7-166">Trigger</span></span>  | |
| <span data-ttu-id="cbce7-167">Dimensiona</span><span class="sxs-lookup"><span data-stu-id="cbce7-167">grip</span></span> | <span data-ttu-id="cbce7-168">Dimensiona</span><span class="sxs-lookup"><span data-stu-id="cbce7-168">Grip</span></span> | <span data-ttu-id="cbce7-169">Toque ou aperte o ar</span><span class="sxs-lookup"><span data-stu-id="cbce7-169">Air tap or squeeze</span></span> |
| <span data-ttu-id="cbce7-170">primaryButton</span><span class="sxs-lookup"><span data-stu-id="cbce7-170">primaryButton</span></span> | <span data-ttu-id="cbce7-171">[X/A]-Pressione</span><span class="sxs-lookup"><span data-stu-id="cbce7-171">[X/A] - Press</span></span> | <span data-ttu-id="cbce7-172">Fechar e abrir dedos indicador e polegar</span><span class="sxs-lookup"><span data-stu-id="cbce7-172">Air tap</span></span> |
| <span data-ttu-id="cbce7-173">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="cbce7-173">secondaryButton</span></span> | <span data-ttu-id="cbce7-174">[S/B]-Pressione</span><span class="sxs-lookup"><span data-stu-id="cbce7-174">[Y/B] - Press</span></span> | |
| <span data-ttu-id="cbce7-175">gripButton</span><span class="sxs-lookup"><span data-stu-id="cbce7-175">gripButton</span></span> | <span data-ttu-id="cbce7-176">Segure a tecla</span><span class="sxs-lookup"><span data-stu-id="cbce7-176">Grip - Press</span></span> | |
| <span data-ttu-id="cbce7-177">triggerButton</span><span class="sxs-lookup"><span data-stu-id="cbce7-177">triggerButton</span></span> | <span data-ttu-id="cbce7-178">Gatilho-Pressione</span><span class="sxs-lookup"><span data-stu-id="cbce7-178">Trigger - Press</span></span> | |
| <span data-ttu-id="cbce7-179">menuButton</span><span class="sxs-lookup"><span data-stu-id="cbce7-179">menuButton</span></span> | <span data-ttu-id="cbce7-180">Menu</span><span class="sxs-lookup"><span data-stu-id="cbce7-180">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="cbce7-181">As poses AIM e segure</span><span class="sxs-lookup"><span data-stu-id="cbce7-181">Aim and Grip Poses</span></span>

<span data-ttu-id="cbce7-182">Você tem acesso a dois conjuntos de poses por meio de interações de entrada OpenXR:</span><span class="sxs-lookup"><span data-stu-id="cbce7-182">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="cbce7-183">A alça representa a renderização de objetos à mão</span><span class="sxs-lookup"><span data-stu-id="cbce7-183">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="cbce7-184">O objetivo se destaca no mundo.</span><span class="sxs-lookup"><span data-stu-id="cbce7-184">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="cbce7-185">Mais informações sobre esse design e as diferenças entre as duas poses podem ser encontradas na [especificação OpenXR-subcaminhos de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="cbce7-185">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="cbce7-186">As poses fornecidas pelo InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** e **DeviceAngularVelocity** representam a pose de **alça** de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="cbce7-186">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="cbce7-187">Os InputFeatureUsages relacionados a pose são definidos no [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)do Unity.</span><span class="sxs-lookup"><span data-stu-id="cbce7-187">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="cbce7-188">As poses fornecidas pelo InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** e **PointerAngularVelocity** representam a pose de **AIM** de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="cbce7-188">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="cbce7-189">Esses InputFeatureUsages não são definidos em nenhum arquivo C# incluído, portanto, você precisará definir seu próprio InputFeatureUsages da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="cbce7-189">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="cbce7-190">Haptics</span><span class="sxs-lookup"><span data-stu-id="cbce7-190">Haptics</span></span>

<span data-ttu-id="cbce7-191">Para obter informações sobre como usar o haptics no sistema de entrada XR da Unity, a documentação pode ser encontrada no [manual do Unity para o Unity XR Input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="cbce7-191">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="cbce7-192">O que virá em breve</span><span class="sxs-lookup"><span data-stu-id="cbce7-192">What's coming soon</span></span>

<span data-ttu-id="cbce7-193">Os seguintes problemas e recursos ausentes são conhecidos com o plug-in OpenXR da realidade misturada **versão 0.1.0**.</span><span class="sxs-lookup"><span data-stu-id="cbce7-193">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="cbce7-194">Estamos trabalhando nessas soluções e lançaremos correções e novos recursos em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="cbce7-194">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="cbce7-195">**ARPlaneSubsystem** ainda não é compatível.</span><span class="sxs-lookup"><span data-stu-id="cbce7-195">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="cbce7-196">**ARPlaneManager**, **ARRaycastManager** e API relacionada, como **ARAnchorManager. AttachAnchor** , também não têm suporte no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cbce7-196">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="cbce7-197">A **âncora** não é suportada pela comunicação remota do Holographic ainda, mas está chegando em breve.</span><span class="sxs-lookup"><span data-stu-id="cbce7-197">**Anchor** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="cbce7-198">O rastreamento de **malha à mão** , **códigos QR** e **XRMeshSubsystem** ainda não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="cbce7-198">**Hand Mesh** tracking, **QR Codes**, and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="cbce7-199">O suporte a **âncoras espaciais do Azure** estará disponível em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="cbce7-199">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="cbce7-200">**ARM64** é a única plataforma com suporte para aplicativos do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="cbce7-200">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="cbce7-201">A plataforma **ARM** estará disponível em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="cbce7-201">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="cbce7-202">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="cbce7-202">Troubleshooting</span></span>

<span data-ttu-id="cbce7-203">Quando você suspende e retoma um aplicativo do Unity no HoloLens 2, o aplicativo não pode retomar corretamente, o que leva a 4 pontos girando na exibição do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="cbce7-203">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>
* <span data-ttu-id="cbce7-204">Defina o **modo de envio de profundidade** como **nenhum** nas configurações do projeto OpenXR como uma solução alternativa</span><span class="sxs-lookup"><span data-stu-id="cbce7-204">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
