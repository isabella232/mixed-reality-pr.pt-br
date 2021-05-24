---
title: Comunicação remota holográfica em um aplicativo da área de trabalho
description: Descubra como usar a Remota Holográfica em um aplicativo da área de trabalho com OpenXR.
author: hferrone
ms.author: alexturn
ms.date: 03/16/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, Kit de Ferramentas de Realidade Misturada, realidade aumentada, realidade virtual, headsets de realidade misturada, learn, tutorial, introdução, comunicação remota holográfica, área de trabalho
ms.openlocfilehash: 18557af1f08ea05715b92b5072460871bb05a329
ms.sourcegitcommit: b195b82f7e83e2ac4f5d8937d169e9dcb865d46d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/24/2021
ms.locfileid: "110333401"
---
# <a name="holographic-remoting-in-desktop-app"></a><span data-ttu-id="b4b3d-104">Comunicação remota holográfica em um aplicativo da área de trabalho</span><span class="sxs-lookup"><span data-stu-id="b4b3d-104">Holographic Remoting in desktop app</span></span>

> [!NOTE]
> <span data-ttu-id="b4b3d-105">O suporte à remoção de aplicativos autônomos do Windows foi adicionado na versão do pacote 0.1.3.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-105">Windows Standalone app remoting support was added in the 0.1.3 package release.</span></span>
> <span data-ttu-id="b4b3d-106">A partir da versão 0.1.3, esse recurso não dá suporte a builds UWP.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-106">As of version 0.1.3, this feature doesn’t support UWP builds.</span></span>

1. <span data-ttu-id="b4b3d-107">Siga as etapas em [Configuração de Remoção Holográfica](unity-play-mode.md#holographic-remoting-setup)</span><span class="sxs-lookup"><span data-stu-id="b4b3d-107">Follow the steps in [Holographic Remoting setup](unity-play-mode.md#holographic-remoting-setup)</span></span>
2. <span data-ttu-id="b4b3d-108">Abra **Editar -> Configurações do** Projeto, navegue até Gerenciamento de **plug-in XR** e marque **a caixa Windows Mixed Reality conjunto de recursos.**</span><span class="sxs-lookup"><span data-stu-id="b4b3d-108">Open **Edit -> Project Settings**, navigate to **XR plug-in Management**, and check the **Windows Mixed Reality feature set** box.</span></span> <span data-ttu-id="b4b3d-109">Além disso, **desmarque Inicializar XR na Inicialização:**</span><span class="sxs-lookup"><span data-stu-id="b4b3d-109">Also, uncheck **Initialize XR on Startup**:</span></span>

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com Inicializar XR na Inicialização desmarcada](images/openxr-features-img-02-app.png)

3. <span data-ttu-id="b4b3d-111">Expanda **a seção** Recursos em **OpenXR** e selecione **Mostrar Tudo**</span><span class="sxs-lookup"><span data-stu-id="b4b3d-111">Expand the **Features** section under **OpenXR** and select **Show All**</span></span>
4. <span data-ttu-id="b4b3d-112">Marque a **caixa de seleção Holographic App Remoting:**</span><span class="sxs-lookup"><span data-stu-id="b4b3d-112">Check the **Holographic App Remoting** checkbox:</span></span>

    ![Captura de tela do painel de configurações do projeto aberto no Editor do Unity com a opção de remoção de aplicativo habilitada](images/openxr-features-img-03-app.png)

5. <span data-ttu-id="b4b3d-114">Em seguida, escreva um código para definir a configuração de remoting e disparar a inicialização de XR.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-114">Next, write some code to set the remoting configuration and trigger XR initialization.</span></span> <span data-ttu-id="b4b3d-115">O aplicativo de exemplo distribuído com o [Plug-in OpenXR](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) de Realidade Misturada contém AppRemoting.cs, que mostra um cenário de exemplo para se conectar a um endereço IP específico em runtime.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-115">The sample app distributed with the [Mixed Reality OpenXR Plugin](openxr-getting-started.md#unity-sample-projects-for-openxr-and-hololens-2) contains AppRemoting.cs, which shows an example scenario for connecting to a specific IP address at runtime.</span></span> <span data-ttu-id="b4b3d-116">Implantar o aplicativo de exemplo em um computador local neste ponto exibirá um campo de entrada de endereço IP com um botão conectar.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-116">Deploying the sample app to a local machine at this point will display an IP address input field with a connect button.</span></span> <span data-ttu-id="b4b3d-117">Digitar um endereço IP e clicar em Conectar inicializa o XR e tentar se conectar ao dispositivo de destino:</span><span class="sxs-lookup"><span data-stu-id="b4b3d-117">Typing an IP address and clicking Connect will initialize XR and attempt to connect to the target device:</span></span>

    ![Captura de tela do aplicativo de exemplo exibindo a interface do usuário de exemplo de remoting do aplicativo](images/openxr-sample-app-remoting.png)

6. <span data-ttu-id="b4b3d-119">Para escrever código de conexão personalizado, `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` chame com um `RemotingConfiguration` preenchido.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-119">To write custom connection code, call `Microsoft.MixedReality.OpenXR.Remoting.AppRemoting.Connect` with a filled-in `RemotingConfiguration`.</span></span> <span data-ttu-id="b4b3d-120">O aplicativo de exemplo expõe isso no inspetor e mostra como preencher o endereço IP de um campo de texto.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-120">The sample app exposes this in the inspector and shows how to fill in the IP address from a text field.</span></span> <span data-ttu-id="b4b3d-121">Chamar `Connect` definirá a configuração e inicializa automaticamente o XR, por isso ele deve ser chamado como uma coroutina:</span><span class="sxs-lookup"><span data-stu-id="b4b3d-121">Calling `Connect` will set the configuration and automatically initialize XR, which is why it must be called as a coroutine:</span></span>

    ``` cs
    StartCoroutine(Remoting.AppRemoting.Connect(remotingConfiguration));
    ```

7. <span data-ttu-id="b4b3d-122">Durante a execução, você pode obter o estado de conexão atual com a API e, opcionalmente, desconectar `AppRemoting.TryGetConnectionState` e des inicializar XR usando `AppRemoting.Disconnect()` .</span><span class="sxs-lookup"><span data-stu-id="b4b3d-122">While running, you can obtain the current connection state with the `AppRemoting.TryGetConnectionState` API, and optionally disconnect and de-initialize XR using `AppRemoting.Disconnect()`.</span></span> <span data-ttu-id="b4b3d-123">Isso pode ser usado para desconectar e reconectar-se a um dispositivo diferente na mesma sessão de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-123">This could be used to disconnect and reconnect to a different device within the same app session.</span></span> <span data-ttu-id="b4b3d-124">O aplicativo de exemplo fornece um cubo tappable que desconectará a sessão de comunicação remota, se tocado.</span><span class="sxs-lookup"><span data-stu-id="b4b3d-124">The sample app provides a tappable cube which will disconnect the remoting session if tapped.</span></span>

### <a name="migration-from-previous-apis"></a><span data-ttu-id="b4b3d-125">Migração de APIs anteriores</span><span class="sxs-lookup"><span data-stu-id="b4b3d-125">Migration from previous APIs</span></span>

#### <a name="unityenginexrwsaholographicremoting"></a><span data-ttu-id="b4b3d-126">UnityEngine. XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="b4b3d-126">UnityEngine.XR.WSA.HolographicRemoting</span></span>

<span data-ttu-id="b4b3d-127">Do código de exemplo nos [documentos do Unity](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span><span class="sxs-lookup"><span data-stu-id="b4b3d-127">From the sample code on [Unity's docs](https://docs.unity3d.com/2018.4/Documentation/ScriptReference/XR.WSA.HolographicRemoting.html):</span></span>

| <span data-ttu-id="b4b3d-128">XR. WSA. HolographicRemoting</span><span class="sxs-lookup"><span data-stu-id="b4b3d-128">XR.WSA.HolographicRemoting</span></span> | <span data-ttu-id="b4b3d-129">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="b4b3d-129">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `HolographicRemoting.Connect(String)` | `AppRemoting.Connect(RemotingConfiguration)` |
| `HolographicRemoting.ConnectionState` | `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| `StartCoroutine(LoadDevice("WindowsMR"))`| <span data-ttu-id="b4b3d-130">[N/A: ocorre automaticamente ao chamar `AppRemoting.Connect` ]</span><span class="sxs-lookup"><span data-stu-id="b4b3d-130">[N/A: Automatically happens when calling `AppRemoting.Connect`]</span></span>  |

#### <a name="unityenginexrwindowsmrwindowsmrremoting"></a><span data-ttu-id="b4b3d-131">UnityEngine. XR. WindowsMR. WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="b4b3d-131">UnityEngine.XR.WindowsMR.WindowsMRRemoting</span></span>

| <span data-ttu-id="b4b3d-132">XR. WindowsMR.WindowsMRRemoting</span><span class="sxs-lookup"><span data-stu-id="b4b3d-132">XR.WindowsMR.WindowsMRRemoting</span></span> | <span data-ttu-id="b4b3d-133">OpenXR. Remoting. AppRemoting</span><span class="sxs-lookup"><span data-stu-id="b4b3d-133">OpenXR.Remoting.AppRemoting</span></span> |
| ---- | ---- |
| `WindowsMRRemoting.Connect()` | `AppRemoting.Connect(RemotingConfiguration)` |
| `WindowsMRRemoting.Disconnect()` | `AppRemoting.Disconnect()` |
| <span data-ttu-id="b4b3d-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` e `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span><span class="sxs-lookup"><span data-stu-id="b4b3d-134">`WindowsMRRemoting.TryGetConnectionState(out ConnectionState)` and `WindowsMRRemoting.TryGetConnectionFailureReason(out ConnectionFailureReason)`</span></span>| `AppRemoting.TryGetConnectionState(out ConnectionState, out DisconnectReason)`|
| <span data-ttu-id="b4b3d-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span><span class="sxs-lookup"><span data-stu-id="b4b3d-135">`WindowsMRRemoting.isAudioEnabled`, `WindowsMRRemoting.maxBitRateKbps`, `WindowsMRRemoting.remoteMachineName`</span></span> | <span data-ttu-id="b4b3d-136">Transmitido `AppRemoting.Connect` via `RemotingConfiguration` struct</span><span class="sxs-lookup"><span data-stu-id="b4b3d-136">Passed into `AppRemoting.Connect` via the `RemotingConfiguration` struct</span></span> |
| `WindowsMRRemoting.isConnected` | `AppRemoting.TryGetConnectionState(out ConnectionState state, out _) && state == ConnectionState.Connected`