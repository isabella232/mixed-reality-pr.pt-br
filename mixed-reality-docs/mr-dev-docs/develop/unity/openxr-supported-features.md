---
title: Recursos com suporte do plug-in OpenXR no Unity
description: Descubra os recursos que o OpenXR dá suporte para desenvolvimento de realidade misturada no Unity.
author: hferrone
ms.author: alexturn
ms.date: 01/11/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução
ms.openlocfilehash: 0501abe5a417c17283347455ccea8ec6f49a6a45
ms.sourcegitcommit: 4647712788a91a2b26d4b01e62285c2942bb0bd2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102230737"
---
# <a name="mixed-reality-openxr-supported-features-in-unity"></a><span data-ttu-id="0383d-104">Recursos com suporte da realidade misturada OpenXR no Unity</span><span class="sxs-lookup"><span data-stu-id="0383d-104">Mixed Reality OpenXR supported features in Unity</span></span>

<span data-ttu-id="0383d-105">O pacote de **plug-in OpenXR da realidade mista** é uma extensão do **plug-in OpenXR** do Unity e dá suporte a um conjunto de recursos para headsets do HoloLens 2 e do Windows Mixed Reality.</span><span class="sxs-lookup"><span data-stu-id="0383d-105">The **Mixed Reality OpenXR Plugin** package is an extension of Unity's **OpenXR Plugin** and supports a suite of features for HoloLens 2 and Windows Mixed Reality headsets.</span></span> <span data-ttu-id="0383d-106">Antes de continuar, certifique-se de ter instalado o **Unity 2020,2** ou posterior, **OpenXR plugin versão 0.1.3** ou posterior e seu projeto de Unity está [configurado para OpenXR](openxr-getting-started.md).</span><span class="sxs-lookup"><span data-stu-id="0383d-106">Before continuing, make sure that you've installed **Unity 2020.2** or later, **OpenXR Plugin version 0.1.3** or later, and your Unity project is [configured for OpenXR](openxr-getting-started.md).</span></span>

## <a name="whats-supported"></a><span data-ttu-id="0383d-107">O que tem suporte</span><span class="sxs-lookup"><span data-stu-id="0383d-107">What's supported</span></span>

<span data-ttu-id="0383d-108">Atualmente, há suporte para os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="0383d-108">The following features are currently supported:</span></span>

* <span data-ttu-id="0383d-109">Dá suporte a aplicativos UWP para o HoloLens 2 e otimizar para o modelo de aplicativo do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0383d-109">Supports UWP applications for HoloLens 2, and optimize for HoloLens 2 application model.</span></span>
* <span data-ttu-id="0383d-110">Dá suporte a aplicativos Win32 VR para o headset de realidade mista do Windows com perfis de controlador mais recentes e comunicação remota de aplicativo Holographic.</span><span class="sxs-lookup"><span data-stu-id="0383d-110">Supports Win32 VR applications for Windows Mixed Reality headset with latest controller profiles and holographic app remoting.</span></span>
* <span data-ttu-id="0383d-111">Controle de escala mundial usando âncoras e espaço não associado.</span><span class="sxs-lookup"><span data-stu-id="0383d-111">World scale tracking using Anchors and Unbounded space.</span></span>
* <span data-ttu-id="0383d-112">[API de armazenamento de ancoragem para persistir âncoras](#anchors-and-anchor-persistence) no armazenamento local do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0383d-112">[Anchor storage API to persist anchors](#anchors-and-anchor-persistence) to HoloLens 2 local storage.</span></span>
* <span data-ttu-id="0383d-113">[Controlador de movimento e interações de mão](#motion-controller-and-hand-interactions), incluindo o novo controlador do HP reverberate G2.</span><span class="sxs-lookup"><span data-stu-id="0383d-113">[Motion controller and hand interactions](#motion-controller-and-hand-interactions), including the new HP Reverb G2 controller.</span></span>
* <span data-ttu-id="0383d-114">Controle de mão articulado usando 26 junções e entradas de raio conjuntas.</span><span class="sxs-lookup"><span data-stu-id="0383d-114">Articulated hand tracking using 26 joints and joint radius inputs.</span></span>
* <span data-ttu-id="0383d-115">Observe a interação olhar no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0383d-115">Eye gaze interaction on HoloLens 2.</span></span>
* <span data-ttu-id="0383d-116">Localizando a câmera de foto/vídeo (PV) no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0383d-116">Locating photo/video (PV) camera on HoloLens 2.</span></span>
* <span data-ttu-id="0383d-117">A realidade misturada é a captura usando o processamento de 3ª vista por meio da câmera VP.</span><span class="sxs-lookup"><span data-stu-id="0383d-117">Mixed Reality Capture using 3rd eye rendering through PV camera.</span></span>
* <span data-ttu-id="0383d-118">Dá suporte à ["reprodução" para o HoloLens 2 com o aplicativo de comunicação remota do Holographic](#holographic-remoting-in-unity-editor-play-mode), permitindo que os desenvolvedores depurem scripts sem compilar e implantar no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0383d-118">Supports ["Play" to HoloLens 2 with the Holographic Remoting app](#holographic-remoting-in-unity-editor-play-mode), allowing developers to debug scripts without building and deploying to the device.</span></span>
* <span data-ttu-id="0383d-119">Compatível com o MRTK Unity 2.5.3 e mais recente por meio do [suporte do provedor MRTK OpenXR](openxr-getting-started.md#using-mrtk-with-openxr-support).</span><span class="sxs-lookup"><span data-stu-id="0383d-119">Compatible with MRTK Unity 2.5.3 and newer through [MRTK OpenXR provider support](openxr-getting-started.md#using-mrtk-with-openxr-support).</span></span>
* <span data-ttu-id="0383d-120">Compatível com o Unity [ARFoundation 4,0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) ou posterior.</span><span class="sxs-lookup"><span data-stu-id="0383d-120">Compatible with Unity [ARFoundation 4.0](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/index.html) or later.</span></span>
* <span data-ttu-id="0383d-121">(Adicionado em 0.1.3) Dá suporte à [comunicação remota do aplicativo de desktop Holographic](#holographic-remoting-in-desktop-app) de um aplicativo autônomo do Windows e compilado.</span><span class="sxs-lookup"><span data-stu-id="0383d-121">(Added in 0.1.3) Supports [desktop app Holographic Remoting](#holographic-remoting-in-desktop-app) from a built and deployed Windows Standalone app.</span></span>
* <span data-ttu-id="0383d-122">(Adicionado em 0.1.4) Dá suporte ao [controle de código QR](#qr-codes) no HoloLens2 por meio de SpatialGraphNode</span><span class="sxs-lookup"><span data-stu-id="0383d-122">(Added in 0.1.4) Supports [QR code tracking](#qr-codes) on HoloLens2 through SpatialGraphNode</span></span>

## <a name="holographic-remoting-setup"></a><span data-ttu-id="0383d-123">Configuração de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="0383d-123">Holographic Remoting setup</span></span>

1. <span data-ttu-id="0383d-124">Primeiro, você precisa [instalar o aplicativo de player de comunicação remota do Holographic](https://www.microsoft.com/store/productId/9NBLGGH4SV40) do Microsoft Store no seu HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="0383d-124">First, you need to [install the Holographic Remoting Player app](https://www.microsoft.com/store/productId/9NBLGGH4SV40) from the Microsoft Store on your HoloLens 2</span></span>
2. <span data-ttu-id="0383d-125">Execute o aplicativo de player de comunicação remota do Holographic no HoloLens 2 e você verá o número de versão e o endereço IP para se conectar</span><span class="sxs-lookup"><span data-stu-id="0383d-125">Run the Holographic Remoting Player app on HoloLens 2 and you'll see the version number and IP address to connect to</span></span>
    * <span data-ttu-id="0383d-126">Você precisará do v 2.4 ou posterior para trabalhar com o plug-in OpenXR</span><span class="sxs-lookup"><span data-stu-id="0383d-126">You'll need v2.4 or later to work with the OpenXR plugin</span></span>

    ![Captura de tela do player de comunicação remota do Holographic em execução no HoloLens](images/openxr-features-img-01.png)

## <a name="holographic-remoting-in-unity-editor-play-mode"></a><span data-ttu-id="0383d-128">Holographic comunicação remota no modo de reprodução do editor do Unity</span><span class="sxs-lookup"><span data-stu-id="0383d-128">Holographic Remoting in Unity Editor play mode</span></span>

<span data-ttu-id="0383d-129">Criar um projeto de Unity do UWP no projeto do Visual Studio e, em seguida, compactá-lo e implantá-lo em um dispositivo HoloLens 2 pode levar algum tempo.</span><span class="sxs-lookup"><span data-stu-id="0383d-129">Building a UWP Unity project in Visual Studio project and then packaging and deploying it to a HoloLens 2 device can take some time.</span></span> <span data-ttu-id="0383d-130">Uma solução é habilitar o recurso de comunicação remota do editor do Holographic, que permite que você depure seu script C# usando o modo "Play" diretamente em um dispositivo de HoloLens 2 na rede.</span><span class="sxs-lookup"><span data-stu-id="0383d-130">One solution is to enable the Holographic Editor Remoting feature, which lets you debug your C# script using “Play” mode directly to a HoloLens 2 device over your network.</span></span> <span data-ttu-id="0383d-131">Esse cenário evita a sobrecarga de criar e implantar um pacote UWP para um dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="0383d-131">This scenario avoids the overhead of building and deploying a UWP package to remote device.</span></span>

1. <span data-ttu-id="0383d-132">Siga as etapas na [instalação do Holographic Remoting](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="0383d-132">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="0383d-133">Abra **configurações do projeto de > de edição**, navegue até **Gerenciamento de plug-in de XR** e marque a caixa conjunto de recursos do **Windows Mixed Realm** :</span><span class="sxs-lookup"><span data-stu-id="0383d-133">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box:</span></span>

    ![Captura de tela do painel configurações do projeto aberta no editor do Unity com o gerenciamento de plug-in do XR realçado](images/openxr-features-img-02.png)

3. <span data-ttu-id="0383d-135">Expanda a seção **recursos** em **OpenXR** e selecione **Mostrar tudo**</span><span class="sxs-lookup"><span data-stu-id="0383d-135">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="0383d-136">Marque a caixa de seleção **comunicação remota do editor de Holographic** e insira o endereço IP obtido do aplicativo de comunicação remota do Holographic:</span><span class="sxs-lookup"><span data-stu-id="0383d-136">Check the **Holographic Editor Remoting** checkbox and input the IP address you get from the Holographic Remoting app:</span></span>

    ![Captura de tela do painel de configurações do projeto aberto no editor do Unity com recursos realçados](images/openxr-features-img-03.png)

<span data-ttu-id="0383d-138">Agora você pode clicar no botão "reproduzir" para reproduzir seu aplicativo do Unity no aplicativo de comunicação remota do Holographic em seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0383d-138">Now you can click the “Play” button to play your Unity app into the Holographic Remoting app on your HoloLens.</span></span> <span data-ttu-id="0383d-139">Você também pode [anexar o Visual Studio ao Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) para depurar scripts C# no modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="0383d-139">You can also [attach Visual Studio to Unity](/visualstudio/gamedev/unity/get-started/using-visual-studio-tools-for-unity?pivots=windows) to debug C# scripts in the play mode.</span></span>

> [!NOTE]
> <span data-ttu-id="0383d-140">A partir da versão 0.1.0, o tempo de execução de comunicação remota do Holographic não dá suporte a âncoras, e as funcionalidades de ARAnchorManager não funcionarão por meio de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="0383d-140">As of version 0.1.0, the Holographic Remoting runtime doesn’t support Anchors, and ARAnchorManager functionalities will not work through remoting.</span></span>  <span data-ttu-id="0383d-141">Esse recurso estará disponível em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="0383d-141">This feature is coming in future releases.</span></span>

## <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="0383d-142">Comunicação remota do Holographic no aplicativo de desktop</span><span class="sxs-lookup"><span data-stu-id="0383d-142">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="0383d-143">O suporte remoto do aplicativo Windows autônomo foi adicionado na versão do pacote 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="0383d-143">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="0383d-144">A partir da versão 0.1.3, esse recurso não oferece suporte a compilações UWP.</span><span class="sxs-lookup"><span data-stu-id="0383d-144">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="0383d-145">Siga as etapas na [instalação do Holographic Remoting](#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="0383d-145">Follow the steps in [Holographic Remoting setup](#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="0383d-146">Abra **as configurações do projeto de > de edição**, navegue até o **Gerenciamento de plug-in do XR** e marque a caixa conjunto de recursos da realidade do **Windows Mixed** .</span><span class="sxs-lookup"><span data-stu-id="0383d-146">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="0383d-147">Além disso, desmarque **inicializar XR na inicialização**:</span><span class="sxs-lookup"><span data-stu-id="0383d-147">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Captura de tela do painel de configurações do projeto aberta no editor do Unity com Initialize XR na inicialização desmarcada](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="0383d-149">Expanda a seção **recursos** em **OpenXR** e selecione **Mostrar tudo**</span><span class="sxs-lookup"><span data-stu-id="0383d-149">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="0383d-150">Marque a caixa de seleção de **comunicação remota do aplicativo Holographic** :</span><span class="sxs-lookup"><span data-stu-id="0383d-150">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Captura de tela do painel de configurações do projeto aberto no editor do Unity com a comunicação remota do aplicativo habilitada](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="0383d-152">Em seguida, escreva algum código para definir a configuração de comunicação remota e disparar a inicialização de XR.</span><span class="sxs-lookup"><span data-stu-id="0383d-152">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="0383d-153">O aplicativo de exemplo distribuído com o [plug-in OpenXR de realidade misturada](openxr-getting-started.md#hololens-2-samples) contém AppRemoting.cs, que mostra um cenário de exemplo para se conectar a um endereço IP específico em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0383d-153">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="0383d-154">A implantação do aplicativo de exemplo em um computador local neste ponto exibirá um campo de entrada de endereço IP com um botão conectar.</span><span class="sxs-lookup"><span data-stu-id="0383d-154">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="0383d-155">Digitar um endereço IP e clicar em conectar irá inicializar o XR e tentar se conectar ao dispositivo de destino:</span><span class="sxs-lookup"><span data-stu-id="0383d-155">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Captura de tela do aplicativo de exemplo exibindo exemplo de IU de comunicação remota](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="0383d-157">Para gravar o código de conexão personalizado, chame `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` com um preenchimento `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="0383d-157">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="0383d-158">O aplicativo de exemplo expõe isso no Inspetor e mostra como preencher o endereço IP a partir de um campo de texto.</span><span class="sxs-lookup"><span data-stu-id="0383d-158">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="0383d-159">Chamar `Connect` irá definir a configuração e inicializar automaticamente a XR, que é o motivo pelo qual ela deve ser chamada como uma corrotina:</span><span class="sxs-lookup"><span data-stu-id="0383d-159">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="0383d-160">Durante a execução, você pode obter o estado de conexão atual com a `AppRemoting.TryGetConnectionState` API e, opcionalmente, desconectar e desinicializar a XR usando `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="0383d-160">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="0383d-161">Isso pode ser usado para desconectar e reconectar-se a um dispositivo diferente na mesma sessão de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0383d-161">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="0383d-162">O aplicativo de exemplo fornece um cubo tappable que desconectará a sessão de comunicação remota, se tocado.</span><span class="sxs-lookup"><span data-stu-id="0383d-162">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="0383d-163">Migração de APIs anteriores</span><span class="sxs-lookup"><span data-stu-id="0383d-163">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="0383d-164">UnityEngine. XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="0383d-164">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="0383d-165">Do código de exemplo nos [documentos do Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="0383d-165">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="0383d-166">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="0383d-166">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="0383d-167">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="0383d-167">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="0383d-168">[N/A: ocorre automaticamente ao chamar `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="0383d-168">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="0383d-169">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="0383d-169">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="0383d-170">XR. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="0383d-170">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="0383d-171">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="0383d-171">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="0383d-172">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="0383d-172">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="0383d-173">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="0383d-173">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="0383d-174">Transmitido `AppRemoting.Connect` via `RemotingConfiguration` struct</span><span class="sxs-lookup"><span data-stu-id="0383d-174">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`

## <a name="anchors-and-anchor-persistence"></a><span data-ttu-id="0383d-175">Âncoras e persistência de ancoragem</span><span class="sxs-lookup"><span data-stu-id="0383d-175">Anchors and Anchor Persistence</span></span>

<span data-ttu-id="0383d-176">O plug-in Mixed Reality OpenXR fornece a funcionalidade de ancoragem básica por meio de uma implementação de ARFoundation **ARAnchorManager** do Unity.</span><span class="sxs-lookup"><span data-stu-id="0383d-176">The Mixed Reality OpenXR Plugin supplies basic anchor functionality through an implementation of Unity’s ARFoundation **ARAnchorManager**.</span></span> <span data-ttu-id="0383d-177">Para aprender as noções básicas sobre **ARAnchor** s no ARFoundation, visite o [manual do ARFoundation para o gerente de ancoragem ar](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span><span class="sxs-lookup"><span data-stu-id="0383d-177">To learn the basics on **ARAnchor** s in ARFoundation, visit the [ARFoundation Manual for AR Anchor Manager](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@4.1/manual/anchor-manager.html).</span></span> <span data-ttu-id="0383d-178">A partir da versão 0.1.0, esse plug-in dá suporte a toda a funcionalidade ARAnchorManager, exceto a criação de âncoras anexadas a um plano, que está chegando em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="0383d-178">As of version 0.1.0, this plugin supports all ARAnchorManager functionality except creating anchors attached to a plane, which is coming in a future release.</span></span>

### <a name="anchor-persistence-and-the-xranchorstore"></a><span data-ttu-id="0383d-179">Persistência de ancoragem e XRAnchorStore</span><span class="sxs-lookup"><span data-stu-id="0383d-179">Anchor Persistence and the XRAnchorStore</span></span>

<span data-ttu-id="0383d-180">Uma API adicional chamada **XRAnchorStore** permite que as âncoras sejam persistidas entre as sessões.</span><span class="sxs-lookup"><span data-stu-id="0383d-180">An additional API called the **XRAnchorStore** enables anchors to be persisted between sessions.</span></span> <span data-ttu-id="0383d-181">O XRAnchorStore é uma representação das âncoras salvas em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0383d-181">The XRAnchorStore is a representation of the saved anchors on your device.</span></span> <span data-ttu-id="0383d-182">As âncoras podem persistir de **ARAnchors** na cena do Unity, carregadas do armazenamento para o New **ARAnchors** ou excluídas do armazenamento.</span><span class="sxs-lookup"><span data-stu-id="0383d-182">Anchors can be persisted from **ARAnchors** in the Unity scene, loaded from storage into new **ARAnchors**, or deleted from storage.</span></span>

> [!NOTE]
> <span data-ttu-id="0383d-183">Essas âncoras devem ser salvas e carregadas no mesmo dispositivo.</span><span class="sxs-lookup"><span data-stu-id="0383d-183">These anchors are to be saved and loaded on the same device.</span></span> <span data-ttu-id="0383d-184">O armazenamento de âncora entre dispositivos terá suporte por meio de âncoras espaciais do Azure em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="0383d-184">Cross-device anchor storage will be supported through Azure Spatial Anchors in a future release.</span></span>

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

<span data-ttu-id="0383d-185">Para carregar o XRAnchorStore, o plug-in fornece um método de extensão no XRAnchorSubsystem, o subsistema de um ARAnchorManager:</span><span class="sxs-lookup"><span data-stu-id="0383d-185">To load the XRAnchorStore, the plugin provides an extension method on the XRAnchorSubsystem, the subsystem of an ARAnchorManager:</span></span>

``` cs
public static Task<XRAnchorStore> LoadAnchorStoreAsync(this XRAnchorSubsystem anchorSubsystem)
```

<span data-ttu-id="0383d-186">Para usar esse método de extensão, acesse-o de um subsistema de ARAnchorManager da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0383d-186">To use this extension method, access it from an ARAnchorManager's subsystem as follows:</span></span>

``` cs
ARAnchorManager arAnchorManager = GetComponent<ARAnchorManager>();
XRAnchorStore anchorStore = await arAnchorManager.subsystem.LoadAnchorStoreAsync();
```

<span data-ttu-id="0383d-187">Para ver um exemplo completo de persistência/descontinuação de âncoras, confira o exemplo âncoras-> ancoras Games e o script AnchorsSample.cs na [cena de exemplo do plugin OpenXR de realidade misturada](openxr-getting-started.md#hololens-2-samples):</span><span class="sxs-lookup"><span data-stu-id="0383d-187">To see a full example of persisting / unpersisting anchors, check out the Anchors -> Anchors Sample GameObject and AnchorsSample.cs script in the [Mixed Reality OpenXR Plugin Sample Scene](openxr-getting-started.md#hololens-2-samples):</span></span>

![Captura de tela do painel hierarquia aberta no editor do Unity com o exemplo âncoras realçado](images/openxr-features-img-04.png)

![Captura de tela do painel Inspetor aberto no editor do Unity com o script de exemplo âncoras realçado](images/openxr-features-img-05.png)

## <a name="motion-controller-and-hand-interactions"></a><span data-ttu-id="0383d-190">Controlador de movimento e interações de mão</span><span class="sxs-lookup"><span data-stu-id="0383d-190">Motion controller and hand interactions</span></span>

<span data-ttu-id="0383d-191">Para aprender as noções básicas sobre interações de realidade misturada no Unity, visite o [manual do Unity para entrada do Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span><span class="sxs-lookup"><span data-stu-id="0383d-191">To learn the basics about mixed reality interactions in Unity, visit the [Unity Manual for Unity XR Input](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html).</span></span> <span data-ttu-id="0383d-192">Esta documentação do Unity aborda os mapeamentos de entradas específicas do controlador para **InputFeatureUsage** s mais generalizadas, como as entradas de XR disponíveis podem ser identificadas e categorizadas, como ler dados dessas entradas e muito mais.</span><span class="sxs-lookup"><span data-stu-id="0383d-192">This Unity documentation covers the mappings from controller-specific inputs to more generalizable **InputFeatureUsage** s, how available XR inputs can be identified and categorized, how to read data from these inputs, and more.</span></span>

<span data-ttu-id="0383d-193">O plug-in Mixed Reality OpenXR fornece perfis de interação de entrada adicionais, mapeados para os **InputFeatureUsage** padrão, conforme detalhado abaixo:</span><span class="sxs-lookup"><span data-stu-id="0383d-193">The Mixed Reality OpenXR Plugin provides additional input interaction profiles, mapped to standard **InputFeatureUsage** s as detailed below:</span></span>

| <span data-ttu-id="0383d-194">InputFeatureUsage</span><span class="sxs-lookup"><span data-stu-id="0383d-194">InputFeatureUsage</span></span> | <span data-ttu-id="0383d-195">Controlador do HP reverbo G2 (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="0383d-195">HP Reverb G2 Controller (OpenXR)</span></span> | <span data-ttu-id="0383d-196">Mão do HoloLens (OpenXR)</span><span class="sxs-lookup"><span data-stu-id="0383d-196">HoloLens Hand (OpenXR)</span></span> |
| ---- | ---- | ---- |
| <span data-ttu-id="0383d-197">primary2DAxis</span><span class="sxs-lookup"><span data-stu-id="0383d-197">primary2DAxis</span></span> | <span data-ttu-id="0383d-198">Botões</span><span class="sxs-lookup"><span data-stu-id="0383d-198">Joystick</span></span> | |
| <span data-ttu-id="0383d-199">primary2DAxisClick</span><span class="sxs-lookup"><span data-stu-id="0383d-199">primary2DAxisClick</span></span> | <span data-ttu-id="0383d-200">Joystick – clique em</span><span class="sxs-lookup"><span data-stu-id="0383d-200">Joystick - Click</span></span> | |
| <span data-ttu-id="0383d-201">gatilho</span><span class="sxs-lookup"><span data-stu-id="0383d-201">trigger</span></span> | <span data-ttu-id="0383d-202">Gatilho</span><span class="sxs-lookup"><span data-stu-id="0383d-202">Trigger</span></span>  | |
| <span data-ttu-id="0383d-203">Dimensiona</span><span class="sxs-lookup"><span data-stu-id="0383d-203">grip</span></span> | <span data-ttu-id="0383d-204">Dimensiona</span><span class="sxs-lookup"><span data-stu-id="0383d-204">Grip</span></span> | <span data-ttu-id="0383d-205">Toque ou aperte o ar</span><span class="sxs-lookup"><span data-stu-id="0383d-205">Air tap or squeeze</span></span> |
| <span data-ttu-id="0383d-206">primaryButton</span><span class="sxs-lookup"><span data-stu-id="0383d-206">primaryButton</span></span> | <span data-ttu-id="0383d-207">[X/A]-Pressione</span><span class="sxs-lookup"><span data-stu-id="0383d-207">[X/A] - Press</span></span> | <span data-ttu-id="0383d-208">Fechar e abrir dedos indicador e polegar</span><span class="sxs-lookup"><span data-stu-id="0383d-208">Air tap</span></span> |
| <span data-ttu-id="0383d-209">secondaryButton</span><span class="sxs-lookup"><span data-stu-id="0383d-209">secondaryButton</span></span> | <span data-ttu-id="0383d-210">[S/B]-Pressione</span><span class="sxs-lookup"><span data-stu-id="0383d-210">[Y/B] - Press</span></span> | |
| <span data-ttu-id="0383d-211">gripButton</span><span class="sxs-lookup"><span data-stu-id="0383d-211">gripButton</span></span> | <span data-ttu-id="0383d-212">Segure a tecla</span><span class="sxs-lookup"><span data-stu-id="0383d-212">Grip - Press</span></span> | |
| <span data-ttu-id="0383d-213">triggerButton</span><span class="sxs-lookup"><span data-stu-id="0383d-213">triggerButton</span></span> | <span data-ttu-id="0383d-214">Gatilho-Pressione</span><span class="sxs-lookup"><span data-stu-id="0383d-214">Trigger - Press</span></span> | |
| <span data-ttu-id="0383d-215">menuButton</span><span class="sxs-lookup"><span data-stu-id="0383d-215">menuButton</span></span> | <span data-ttu-id="0383d-216">Menu</span><span class="sxs-lookup"><span data-stu-id="0383d-216">Menu</span></span> | |

### <a name="aim-and-grip-poses"></a><span data-ttu-id="0383d-217">As poses AIM e segure</span><span class="sxs-lookup"><span data-stu-id="0383d-217">Aim and Grip Poses</span></span>

<span data-ttu-id="0383d-218">Você tem acesso a dois conjuntos de poses por meio de interações de entrada OpenXR:</span><span class="sxs-lookup"><span data-stu-id="0383d-218">You have access to two sets of poses through OpenXR input interactions:</span></span>

* <span data-ttu-id="0383d-219">A alça representa a renderização de objetos à mão</span><span class="sxs-lookup"><span data-stu-id="0383d-219">The grip poses for rendering objects in the hand</span></span>
* <span data-ttu-id="0383d-220">O objetivo se destaca no mundo.</span><span class="sxs-lookup"><span data-stu-id="0383d-220">The aim poses for pointing into the world.</span></span>

<span data-ttu-id="0383d-221">Mais informações sobre esse design e as diferenças entre as duas poses podem ser encontradas na [especificação OpenXR-subcaminhos de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span><span class="sxs-lookup"><span data-stu-id="0383d-221">More information on this design and the differences between the two poses can be found in the [OpenXR Specification - Input Subpaths](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).</span></span>

<span data-ttu-id="0383d-222">As poses fornecidas pelo InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** e **DeviceAngularVelocity** representam a pose de **alça** de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="0383d-222">Poses supplied by the InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity**, and **DeviceAngularVelocity** all represent the OpenXR **grip** pose.</span></span> <span data-ttu-id="0383d-223">Os InputFeatureUsages relacionados a pose são definidos no [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)do Unity.</span><span class="sxs-lookup"><span data-stu-id="0383d-223">InputFeatureUsages related to grip poses are defined in Unity’s [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html).</span></span>

<span data-ttu-id="0383d-224">As poses fornecidas pelo InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** e **PointerAngularVelocity** representam a pose de **AIM** de OpenXR.</span><span class="sxs-lookup"><span data-stu-id="0383d-224">Poses supplied by the InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity**, and **PointerAngularVelocity** all represent the OpenXR **aim** pose.</span></span> <span data-ttu-id="0383d-225">Esses InputFeatureUsages não são definidos em nenhum arquivo C# incluído, portanto, você precisará definir seu próprio InputFeatureUsages da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="0383d-225">These InputFeatureUsages aren't defined in any included C# files, so you'll need to define your own InputFeatureUsages as follows:</span></span>

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

### <a name="haptics"></a><span data-ttu-id="0383d-226">Haptics</span><span class="sxs-lookup"><span data-stu-id="0383d-226">Haptics</span></span>

<span data-ttu-id="0383d-227">Para obter informações sobre como usar o haptics no sistema de entrada XR da Unity, a documentação pode ser encontrada no [manual do Unity para o Unity XR Input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span><span class="sxs-lookup"><span data-stu-id="0383d-227">For information on using haptics in Unity’s XR Input system, documentation can be found at the [Unity Manual for Unity XR Input - Haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).</span></span>

## <a name="qr-codes"></a><span data-ttu-id="0383d-228">Códigos QR</span><span class="sxs-lookup"><span data-stu-id="0383d-228">QR codes</span></span>

<span data-ttu-id="0383d-229">O HoloLens 2 pode detectar códigos QR no ambiente em torno do headset, estabelecendo um sistema de coordenadas na localização do mundo real de cada código.</span><span class="sxs-lookup"><span data-stu-id="0383d-229">HoloLens 2 can detect QR codes in the environment around the headset, establishing a coordinate system at each code's real-world location.</span></span> <span data-ttu-id="0383d-230">Você pode encontrar mais detalhes em nossa documentação de [controle de código QR](../platform-capabilities-and-apis/qr-code-tracking.md) .</span><span class="sxs-lookup"><span data-stu-id="0383d-230">You can find more details in our [QR code tracking](../platform-capabilities-and-apis/qr-code-tracking.md) documentation.</span></span>  <span data-ttu-id="0383d-231">Ao usar o plug-in OpenXR, pegue o [ `SpatialGraphNodeId` da API QR](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) e use a `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API para localizar o código QR.</span><span class="sxs-lookup"><span data-stu-id="0383d-231">When using the OpenXR plugin, grab the [`SpatialGraphNodeId` from the QR API](../platform-capabilities-and-apis/qr-code-tracking.md#qr-api-reference) and use the `Microsoft.MixedReality.OpenXR.SpatialGraphNode` API to locate the QR code.</span></span>

<span data-ttu-id="0383d-232">Para referência, temos um [projeto de exemplo de acompanhamento QR no GitHub](https://github.com/yl-msft/QRTracking) com mais uma explicação de uso detalhada para a [ `SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span><span class="sxs-lookup"><span data-stu-id="0383d-232">For reference, we have a [QR tracking sample project on GitHub](https://github.com/yl-msft/QRTracking) with more a detailed usage explanation for the [`SpatialGraphNode` API](https://github.com/yl-msft/QRTracking/blob/main/SampleQRCodes/Assets/Scripts/SpatialGraphNodeTracker.cs).</span></span>

## <a name="whats-coming-soon"></a><span data-ttu-id="0383d-233">O que virá em breve</span><span class="sxs-lookup"><span data-stu-id="0383d-233">What's coming soon</span></span>

<span data-ttu-id="0383d-234">Os seguintes problemas e recursos ausentes são conhecidos com o plug-in OpenXR da realidade misturada **versão 0.1.0**.</span><span class="sxs-lookup"><span data-stu-id="0383d-234">The following issues and missing features are known with Mixed Reality OpenXR plugin **version 0.1.0**.</span></span> <span data-ttu-id="0383d-235">Estamos trabalhando nessas soluções e lançaremos correções e novos recursos em versões futuras.</span><span class="sxs-lookup"><span data-stu-id="0383d-235">We're working on these and will release fixes and new features in upcoming releases.</span></span>

* <span data-ttu-id="0383d-236">**ARPlaneSubsystem** ainda não é compatível.</span><span class="sxs-lookup"><span data-stu-id="0383d-236">**ARPlaneSubsystem** is not supported yet.</span></span> <span data-ttu-id="0383d-237">**ARPlaneManager**, **ARRaycastManager** e API relacionada, como **ARAnchorManager. AttachAnchor** , também não têm suporte no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0383d-237">**ARPlaneManager**, **ARRaycastManager**, and related API like **ARAnchorManager.AttachAnchor** are also not supported on HoloLens 2.</span></span>
* <span data-ttu-id="0383d-238">A **persistência de ancoragem** não é suportada pela comunicação remota do Holographic ainda, mas está chegando em breve.</span><span class="sxs-lookup"><span data-stu-id="0383d-238">**Anchor persistence** isn't supported by Holographic Remoting yet, but it's coming in the near future.</span></span>
* <span data-ttu-id="0383d-239">O rastreamento de **malha à mão** e o **XRMeshSubsystem** ainda não têm suporte.</span><span class="sxs-lookup"><span data-stu-id="0383d-239">**Hand Mesh** tracking and **XRMeshSubsystem** aren't supported yet.</span></span>
* <span data-ttu-id="0383d-240">O suporte a **âncoras espaciais do Azure** estará disponível em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="0383d-240">**Azure Spatial Anchors** support is coming in a future release.</span></span>
* <span data-ttu-id="0383d-241">**ARM64** é a única plataforma com suporte para aplicativos do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="0383d-241">**ARM64** is the only supported platform for HoloLens 2 apps.</span></span> <span data-ttu-id="0383d-242">A plataforma **ARM** estará disponível em uma versão futura.</span><span class="sxs-lookup"><span data-stu-id="0383d-242">The **ARM** platform is coming in a future release.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="0383d-243">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="0383d-243">Troubleshooting</span></span>

<span data-ttu-id="0383d-244">Quando você suspende e retoma um aplicativo do Unity no HoloLens 2, o aplicativo não pode retomar corretamente, o que leva a 4 pontos girando na exibição do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0383d-244">When you suspend and resume a Unity app on HoloLens 2, the app can't correctly resume, which leads to 4 spinning dots in the HoloLens view.</span></span>

* <span data-ttu-id="0383d-245">Defina o **modo de envio de profundidade** como **nenhum** nas configurações do projeto OpenXR como uma solução alternativa</span><span class="sxs-lookup"><span data-stu-id="0383d-245">Set **Depth submission Mode** to **None** in the OpenXR project settings as a workaround</span></span>
