---
title: Comunicação remota do Holographic no aplicativo de desktop
description: Descubra como usar a comunicação remota do Holographic em um aplicativo de área de trabalho com OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, Unity, hololens, hololens 2, realidade misturada, MRTK, kit de ferramentas de realidade mista, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução, Holographic comunicação remota, área de trabalho
ms.openlocfilehash: f3cf43d59b74b0f47e701acc1d7312544867b0df
ms.sourcegitcommit: d5e4eb94c87b86a7774a639f11cd9e35a7050107
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103624312"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="4e1bd-104">Comunicação remota do Holographic no aplicativo de desktop</span><span class="sxs-lookup"><span data-stu-id="4e1bd-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="4e1bd-105">O suporte remoto do aplicativo Windows autônomo foi adicionado na versão do pacote 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="4e1bd-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="4e1bd-106">A partir da versão 0.1.3, esse recurso não oferece suporte a compilações UWP.</span><span class="sxs-lookup"><span data-stu-id="4e1bd-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="4e1bd-107">Siga as etapas na [instalação do Holographic Remoting](openxr-supported-features.md#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="4e1bd-107">Follow the steps in [Holographic Remoting setup](openxr-supported-features.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="4e1bd-108">Abra **as configurações do projeto de > de edição**, navegue até o **Gerenciamento de plug-in do XR** e marque a caixa conjunto de recursos da realidade do **Windows Mixed** .</span><span class="sxs-lookup"><span data-stu-id="4e1bd-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="4e1bd-109">Além disso, desmarque **inicializar XR na inicialização**:</span><span class="sxs-lookup"><span data-stu-id="4e1bd-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Captura de tela do painel de configurações do projeto aberta no editor do Unity com Initialize XR na inicialização desmarcada](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="4e1bd-111">Expanda a seção **recursos** em **OpenXR** e selecione **Mostrar tudo**</span><span class="sxs-lookup"><span data-stu-id="4e1bd-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="4e1bd-112">Marque a caixa de seleção de **comunicação remota do aplicativo Holographic** :</span><span class="sxs-lookup"><span data-stu-id="4e1bd-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Captura de tela do painel de configurações do projeto aberto no editor do Unity com a comunicação remota do aplicativo habilitada](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="4e1bd-114">Em seguida, escreva algum código para definir a configuração de comunicação remota e disparar a inicialização de XR.</span><span class="sxs-lookup"><span data-stu-id="4e1bd-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="4e1bd-115">O aplicativo de exemplo distribuído com o [plug-in OpenXR de realidade misturada](openxr-getting-started.md#hololens-2-samples) contém AppRemoting.cs, que mostra um cenário de exemplo para se conectar a um endereço IP específico em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4e1bd-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#hololens-2-samples) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="4e1bd-116">A implantação do aplicativo de exemplo em um computador local neste ponto exibirá um campo de entrada de endereço IP com um botão conectar.</span><span class="sxs-lookup"><span data-stu-id="4e1bd-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="4e1bd-117">Digitar um endereço IP e clicar em conectar irá inicializar o XR e tentar se conectar ao dispositivo de destino:</span><span class="sxs-lookup"><span data-stu-id="4e1bd-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Captura de tela do aplicativo de exemplo exibindo exemplo de IU de comunicação remota](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="4e1bd-119">Para gravar o código de conexão personalizado, chame `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` com um preenchimento `RemotingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="4e1bd-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="4e1bd-120">O aplicativo de exemplo expõe isso no Inspetor e mostra como preencher o endereço IP a partir de um campo de texto.</span><span class="sxs-lookup"><span data-stu-id="4e1bd-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="4e1bd-121">Chamar `Connect` irá definir a configuração e inicializar automaticamente a XR, que é o motivo pelo qual ela deve ser chamada como uma corrotina:</span><span class="sxs-lookup"><span data-stu-id="4e1bd-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="4e1bd-122">Durante a execução, você pode obter o estado de conexão atual com a `AppRemoting.TryGetConnectionState` API e, opcionalmente, desconectar e desinicializar a XR usando `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="4e1bd-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="4e1bd-123">Isso pode ser usado para desconectar e reconectar-se a um dispositivo diferente na mesma sessão de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4e1bd-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="4e1bd-124">O aplicativo de exemplo fornece um cubo tappable que desconectará a sessão de comunicação remota, se tocado.</span><span class="sxs-lookup"><span data-stu-id="4e1bd-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="4e1bd-125">Migração de APIs anteriores</span><span class="sxs-lookup"><span data-stu-id="4e1bd-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="4e1bd-126">UnityEngine. XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="4e1bd-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="4e1bd-127">Do código de exemplo nos [documentos do Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="4e1bd-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="4e1bd-128">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="4e1bd-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="4e1bd-129">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="4e1bd-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="4e1bd-130">[N/A: ocorre automaticamente ao chamar `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="4e1bd-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="4e1bd-131">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="4e1bd-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="4e1bd-132">XR. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="4e1bd-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="4e1bd-133">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="4e1bd-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="4e1bd-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="4e1bd-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="4e1bd-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="4e1bd-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="4e1bd-136">Transmitido `AppRemoting.Connect` via `RemotingConfiguration` struct</span><span class="sxs-lookup"><span data-stu-id="4e1bd-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`