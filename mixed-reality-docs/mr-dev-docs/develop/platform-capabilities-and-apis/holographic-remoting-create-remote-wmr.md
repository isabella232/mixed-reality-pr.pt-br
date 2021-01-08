---
title: Escrevendo um aplicativo remoto de comunicação remota do Holographic (WMR)
description: Saiba como transmitir conteúdo remoto renderizado em um computador remoto para o HoloLens 2 com aplicativos de comunicação remota Holographic com HolographicSpace.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, comunicação remota Holographic, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, NuGet
ms.openlocfilehash: b78d1c93c8b2890ba8d904c289c8d61a14380824
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006496"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a><span data-ttu-id="c96dd-104">Escrevendo um aplicativo remoto de comunicação remota do Holographic usando a API do HolographicSpace</span><span class="sxs-lookup"><span data-stu-id="c96dd-104">Writing a Holographic Remoting remote app using the HolographicSpace API</span></span>

>[!IMPORTANT]
><span data-ttu-id="c96dd-105">Este documento descreve a criação de um aplicativo remoto para o HoloLens 2 usando a [API HolographicSpace](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="c96dd-105">This document describes the creation of a remote application for HoloLens 2 using the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="c96dd-106">Os aplicativos remotos para o **HoloLens (1º gen)** devem usar o pacote NuGet versão **1. x**. x.</span><span class="sxs-lookup"><span data-stu-id="c96dd-106">Remote applications for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="c96dd-107">Isso significa que os aplicativos remotos escritos para o HoloLens 2 não são compatíveis com o HoloLens 1 e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="c96dd-107">This implies that remote applications written for HoloLens 2 are not compatible with HoloLens 1 and vice versa.</span></span> <span data-ttu-id="c96dd-108">A documentação do HoloLens 1 pode ser encontrada [aqui](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="c96dd-108">The documentation for HoloLens 1 can be found [here](add-holographic-remoting.md).</span></span>

<span data-ttu-id="c96dd-109">Os aplicativos de comunicação remota Holographic podem transmitir conteúdo renderizado remotamente para o HoloLens 2 e os headsets de imersão de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="c96dd-109">Holographic Remoting apps can stream remotely rendered content to HoloLens 2 and Windows Mixed Reality immersive headsets.</span></span> <span data-ttu-id="c96dd-110">Você também pode acessar mais recursos do sistema e integrar [exibições de imersão](../../design/app-views.md) remotas ao software de PC desktop existente.</span><span class="sxs-lookup"><span data-stu-id="c96dd-110">You can also access more system resources and integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="c96dd-111">Um aplicativo remoto recebe um fluxo de dados de entrada do HoloLens 2, renderiza o conteúdo em uma exibição de imersão virtual e transmite os quadros de conteúdo de volta para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c96dd-111">A remote app receives an input data stream from HoloLens 2, renders content in a virtual immersive view, and streams content frames back to HoloLens 2.</span></span> <span data-ttu-id="c96dd-112">A conexão é feita usando Wi-Fi padrão.</span><span class="sxs-lookup"><span data-stu-id="c96dd-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="c96dd-113">A comunicação remota do Holographic é adicionada a um aplicativo de desktop ou UWP por meio de um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="c96dd-113">Holographic Remoting is added to a desktop or UWP app via a NuGet packet.</span></span> <span data-ttu-id="c96dd-114">É necessário um código adicional que manipula a conexão e é renderizado em uma exibição de imersão.</span><span class="sxs-lookup"><span data-stu-id="c96dd-114">Additional code is required which handles the connection and renders in an immersive view.</span></span> <span data-ttu-id="c96dd-115">Uma conexão de comunicação remota típica terá um mínimo de 50 ms de latência.</span><span class="sxs-lookup"><span data-stu-id="c96dd-115">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="c96dd-116">O aplicativo de player pode relatar a latência em tempo real.</span><span class="sxs-lookup"><span data-stu-id="c96dd-116">The player app can report the latency in real time.</span></span>

<span data-ttu-id="c96dd-117">Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="c96dd-117">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c96dd-118">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="c96dd-118">Prerequisites</span></span>

<span data-ttu-id="c96dd-119">Um bom ponto de partida é um aplicativo de área de trabalho baseado em DirectX em funcionamento ou UWP, que tem como alvo a [API HolographicSpace](../native/getting-a-holographicspace.md).</span><span class="sxs-lookup"><span data-stu-id="c96dd-119">A good starting point is a working DirectX based Desktop or UWP app, which targets the [HolographicSpace API](../native/getting-a-holographicspace.md).</span></span> <span data-ttu-id="c96dd-120">Para obter detalhes, consulte [visão geral do desenvolvimento do DirectX](../native/directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c96dd-120">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="c96dd-121">O [modelo de projeto C++ Holographic](../native/creating-a-holographic-directx-project.md) é um bom ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="c96dd-121">The [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c96dd-122">Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="c96dd-122">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="c96dd-123">O uso de um [apartamento de thread único](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="c96dd-123">The use of a [single-threaded apartment](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="c96dd-124">Ao usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.</span><span class="sxs-lookup"><span data-stu-id="c96dd-124">When using C++/WinRT [winrt::init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>



## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="c96dd-125">Obter o pacote NuGet de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="c96dd-125">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="c96dd-126">As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c96dd-126">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="c96dd-127">Abra o projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c96dd-127">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="c96dd-128">Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="c96dd-128">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="c96dd-129">No painel que aparece, selecione **procurar** e, em seguida, pesquise "comunicação remota do Holographic".</span><span class="sxs-lookup"><span data-stu-id="c96dd-129">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="c96dd-130">Selecione **Microsoft. Holographic. Remoting**, certifique-se de selecionar a versão **2. x. x** mais recente e selecione **instalar**.</span><span class="sxs-lookup"><span data-stu-id="c96dd-130">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="c96dd-131">Se a caixa de diálogo **Visualizar** for exibida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="c96dd-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="c96dd-132">Selecione **aceito** quando a caixa de diálogo do contrato de licença for exibida.</span><span class="sxs-lookup"><span data-stu-id="c96dd-132">Select **I Accept** when the license agreement dialog pops up.</span></span>

>[!NOTE]
><span data-ttu-id="c96dd-133">A versão **1. x. x** do pacote NuGet ainda está disponível para desenvolvedores que desejam direcionar para o HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="c96dd-133">Version **1.x.x** of the NuGet package is still available for developers who want to target HoloLens 1.</span></span> <span data-ttu-id="c96dd-134">Para obter detalhes, consulte [Add Holographic Remoting (HoloLens (1º gen))](add-holographic-remoting.md).</span><span class="sxs-lookup"><span data-stu-id="c96dd-134">For details see [Add Holographic Remoting (HoloLens (1st gen))](add-holographic-remoting.md).</span></span>

## <a name="create-the-remote-context"></a><span data-ttu-id="c96dd-135">Criar o contexto remoto</span><span class="sxs-lookup"><span data-stu-id="c96dd-135">Create the remote context</span></span>

<span data-ttu-id="c96dd-136">Como primeira etapa, o aplicativo deve criar um contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="c96dd-136">As a first step the application should create a remote context.</span></span>

```cpp
// class declaration
#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
    // RemoteContext used to connect with a Holographic Remoting player and display rendered frames
    winrt::Microsoft::Holographic::AppRemoting::RemoteContext m_remoteContext = nullptr;
```


```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

```

>[!WARNING]
><span data-ttu-id="c96dd-137">O Holographic Remoting funciona substituindo o tempo de execução do Windows Mixed Reality que faz parte do Windows com um tempo de execução específico de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="c96dd-137">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="c96dd-138">Isso é feito durante a criação do contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="c96dd-138">This is done during the creation of the remote context.</span></span> <span data-ttu-id="c96dd-139">Por esse motivo, qualquer chamada em qualquer API de realidade mista do Windows antes de criar o contexto remoto pode resultar em um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="c96dd-139">For that reason any call on any Windows Mixed Reality API before creating the remote context can result in unexpected behavior.</span></span> <span data-ttu-id="c96dd-140">A abordagem recomendada é criar o contexto remoto o mais cedo possível antes da interação com qualquer API de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="c96dd-140">The recommended approach is to create the remote context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="c96dd-141">Nunca misture objetos criados ou recuperados por meio de qualquer API de realidade mista do Windows antes da chamada para CreateRemoteContext com objetos criados ou recuperados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="c96dd-141">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to CreateRemoteContext with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="c96dd-142">Em seguida, o espaço Holographic precisa ser criado.</span><span class="sxs-lookup"><span data-stu-id="c96dd-142">Next the holographic space needs to be created.</span></span> <span data-ttu-id="c96dd-143">Não é necessário especificar um CoreWindow.</span><span class="sxs-lookup"><span data-stu-id="c96dd-143">Specifying a CoreWindow isn't required.</span></span> <span data-ttu-id="c96dd-144">Os aplicativos da área de trabalho que não têm um CoreWindow podem apenas passar um ```nullptr``` .</span><span class="sxs-lookup"><span data-stu-id="c96dd-144">Desktop apps that don't have a CoreWindow can just pass a ```nullptr```.</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a><span data-ttu-id="c96dd-145">Conectar-se ao dispositivo</span><span class="sxs-lookup"><span data-stu-id="c96dd-145">Connect to the device</span></span>

<span data-ttu-id="c96dd-146">Quando o aplicativo remoto estiver pronto para renderizar o conteúdo, pode ser estabelecida uma conexão com o dispositivo do Player.</span><span class="sxs-lookup"><span data-stu-id="c96dd-146">When the remote app is ready for rendering content a connection to the player device can be established.</span></span>

<span data-ttu-id="c96dd-147">A conexão pode ser feita de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="c96dd-147">Connection can be done in one of two ways.</span></span>
1) <span data-ttu-id="c96dd-148">O aplicativo remoto se conecta ao Player em execução no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c96dd-148">The remote app connects to the player running on the device.</span></span>
2) <span data-ttu-id="c96dd-149">O Player em execução no dispositivo se conecta ao aplicativo remoto.</span><span class="sxs-lookup"><span data-stu-id="c96dd-149">The player running on the device connects to the remote app.</span></span>

<span data-ttu-id="c96dd-150">Para estabelecer uma conexão do aplicativo remoto com o dispositivo do Player, chame o ```Connect``` método no contexto remoto especificando o nome do host e a porta.</span><span class="sxs-lookup"><span data-stu-id="c96dd-150">To establish a connection from the remote app to the player device call the ```Connect``` method on the remote context specifying the hostname and port.</span></span> <span data-ttu-id="c96dd-151">A porta usada pelo Holographic Remoting Player é **8265**.</span><span class="sxs-lookup"><span data-stu-id="c96dd-151">The port used by the Holographic Remoting Player is **8265**.</span></span>

```cpp
try
{
    m_remoteContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Connect failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="c96dd-152">Assim como acontece com qualquer API do C++/WinRT, você ```Connect``` pode lançar um WinRT:: hresult_error que precisa ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="c96dd-152">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

>[!TIP]
><span data-ttu-id="c96dd-153">Para evitar o uso da projeção de linguagem [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) , o arquivo ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` localizado no pacote NuGet de comunicação remota do Holographic pode ser incluído.</span><span class="sxs-lookup"><span data-stu-id="c96dd-153">To avoid using [C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/) language projection the file ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` located inside the Holographic Remoting NuGet package can be included.</span></span> <span data-ttu-id="c96dd-154">Ele contém declarações das interfaces COM subjacentes.</span><span class="sxs-lookup"><span data-stu-id="c96dd-154">It contains declarations of the underlying COM interfaces.</span></span> <span data-ttu-id="c96dd-155">No entanto, o uso de C++/WinRT é recomendado.</span><span class="sxs-lookup"><span data-stu-id="c96dd-155">The use of C++/WinRT is recommended though.</span></span>

<span data-ttu-id="c96dd-156">A escuta de conexões de entrada no aplicativo remoto pode ser feita chamando o ```Listen``` método.</span><span class="sxs-lookup"><span data-stu-id="c96dd-156">Listening for incoming connections on the remote app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="c96dd-157">A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada.</span><span class="sxs-lookup"><span data-stu-id="c96dd-157">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="c96dd-158">A porta de handshake é usada para o handshake inicial.</span><span class="sxs-lookup"><span data-stu-id="c96dd-158">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="c96dd-159">Os dados são enviados pela porta de transporte.</span><span class="sxs-lookup"><span data-stu-id="c96dd-159">The data is then sent over the transport port.</span></span> <span data-ttu-id="c96dd-160">Por padrão, **8265** e **8266** são usados.</span><span class="sxs-lookup"><span data-stu-id="c96dd-160">By default **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_remoteContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    DebugLog(L"Listen failed with hr = 0x%08X", e.code());
}
```

>[!IMPORTANT]
><span data-ttu-id="c96dd-161">O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API exposta pela comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="c96dd-161">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="handling-remoting-specific-events"></a><span data-ttu-id="c96dd-162">Manipulando eventos específicos de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="c96dd-162">Handling Remoting specific events</span></span>

<span data-ttu-id="c96dd-163">O contexto remoto expõe três eventos, que são importantes para monitorar o estado de uma conexão.</span><span class="sxs-lookup"><span data-stu-id="c96dd-163">The remote context exposes three events, which are important to monitor the state of a connection.</span></span>
1) <span data-ttu-id="c96dd-164">Onconnected: disparado quando uma conexão com o dispositivo tiver sido estabelecida com êxito.</span><span class="sxs-lookup"><span data-stu-id="c96dd-164">OnConnected: Triggered when a connection to the device has been successfully established.</span></span>
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) <span data-ttu-id="c96dd-165">OnDisconnect: disparado se uma conexão estabelecida estiver fechada ou não foi possível estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="c96dd-165">OnDisconnected: Triggered if an established connection is closed or a connection couldn't be established.</span></span>
```cpp
m_onDisconnectedEventRevoker =
    m_remoteContext.OnDisconnected(winrt::auto_revoke, [this, remoteContextWeakRef](ConnectionFailureReason failureReason) {
        if (auto remoteContext = remoteContextWeakRef.get())
        {
            DebugLog(L"Disconnected with reason %d", failureReason);
            // Update UI

            // Reconnect if this is a transient failure.
            if (failureReason == ConnectionFailureReason::HandshakeUnreachable ||
                failureReason == ConnectionFailureReason::TransportUnreachable ||
                failureReason == ConnectionFailureReason::ConnectionLost)
            {
                DebugLog(L"Reconnecting...");

                ConnectOrListen();
            }
            // Failure reason None indicates a normal disconnect.
            else if (failureReason != ConnectionFailureReason::None)
            {
                DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
            }
        }
    });
```
3) <span data-ttu-id="c96dd-166">Desescutando: quando a escuta de conexões de entrada é iniciada.</span><span class="sxs-lookup"><span data-stu-id="c96dd-166">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

<span data-ttu-id="c96dd-167">Além disso, o estado da conexão pode ser consultado usando a ```ConnectionState``` propriedade no contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="c96dd-167">Additionally the connection state can be queried using the ```ConnectionState``` property on the remote context.</span></span>
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a><span data-ttu-id="c96dd-168">Manipulando eventos de fala</span><span class="sxs-lookup"><span data-stu-id="c96dd-168">Handling speech events</span></span>

<span data-ttu-id="c96dd-169">Usando a interface de fala remota, é possível registrar gatilhos de fala com o HoloLens 2 e tê-los remotos no aplicativo remoto.</span><span class="sxs-lookup"><span data-stu-id="c96dd-169">Using the remote speech interface it's possible to register speech triggers with HoloLens 2 and have them remoted to the remote application.</span></span>

<span data-ttu-id="c96dd-170">Esse membro adicional é necessário para acompanhar o estado da fala remota.</span><span class="sxs-lookup"><span data-stu-id="c96dd-170">This additional member is required to track the state of the remote speech.</span></span>

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

<span data-ttu-id="c96dd-171">Primeiro, a interface de fala remota precisa ser recuperada.</span><span class="sxs-lookup"><span data-stu-id="c96dd-171">First the remote speech interface needs to be retrieved.</span></span>

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

<span data-ttu-id="c96dd-172">Usando um método auxiliar assíncrono, você pode inicializar a fala remota.</span><span class="sxs-lookup"><span data-stu-id="c96dd-172">Using an asynchronous helper method you can then initialize the remote speech.</span></span> <span data-ttu-id="c96dd-173">Isso deve ser feito de forma assíncrona, pois a inicialização pode levar um tempo considerável.</span><span class="sxs-lookup"><span data-stu-id="c96dd-173">This should be done asynchronously as initializing might take a considerable amount of time.</span></span> <span data-ttu-id="c96dd-174">[Operações de simultaneidade e assíncronas com c++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explica como criar funções assíncronas com c++/WinRT.</span><span class="sxs-lookup"><span data-stu-id="c96dd-174">[Concurrency and asynchronous operations with C++/WinRT](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/concurrency) explains how to author asynchronous functions with C++/WinRT.</span></span>

```cpp
winrt::Windows::Foundation::IAsyncOperation<winrt::Windows::Storage::StorageFile> LoadGrammarFileAsync()
{
    const wchar_t* speechGrammarFile = L"SpeechGrammar.xml";
    auto rootFolder = winrt::Windows::ApplicationModel::Package::Current().InstalledLocation();
    return rootFolder.GetFileAsync(speechGrammarFile);
}

winrt::fire_and_forget InitializeSpeechAsync(
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech remoteSpeech,
    winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker& onRecognizedSpeechRevoker,
    std::weak_ptr<SampleRemoteMain> sampleRemoteMainWeak)
{
    onRecognizedSpeechRevoker = remoteSpeech.OnRecognizedSpeech(
        winrt::auto_revoke, [sampleRemoteMainWeak](const winrt::Microsoft::Holographic::AppRemoting::RecognizedSpeech& recognizedSpeech) {
            if (auto sampleRemoteMain = sampleRemoteMainWeak.lock())
            {
                sampleRemoteMain->OnRecognizedSpeech(recognizedSpeech.RecognizedText);
            }
        });

    auto grammarFile = co_await LoadGrammarFileAsync();

    std::vector<winrt::hstring> dictionary;
    dictionary.push_back(L"Red");
    dictionary.push_back(L"Blue");
    dictionary.push_back(L"Green");
    dictionary.push_back(L"Default");
    dictionary.push_back(L"Aquamarine");

    remoteSpeech.ApplyParameters(L"", grammarFile, dictionary);
}
```

<span data-ttu-id="c96dd-175">Há duas maneiras de especificar frases a serem reconhecidas.</span><span class="sxs-lookup"><span data-stu-id="c96dd-175">There are two ways of specifying phrases to be recognized.</span></span>
1) <span data-ttu-id="c96dd-176">Especificação dentro de um arquivo XML de gramática de fala.</span><span class="sxs-lookup"><span data-stu-id="c96dd-176">Specification inside a speech grammar xml file.</span></span> <span data-ttu-id="c96dd-177">Consulte [como criar uma gramática XML básica](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="c96dd-177">See [How to create a basic XML Grammar](https://docs.microsoft.com//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) for details.</span></span>
2) <span data-ttu-id="c96dd-178">Especifique ao passá-los dentro do vetor do dicionário para ```ApplyParameters``` .</span><span class="sxs-lookup"><span data-stu-id="c96dd-178">Specify by passing them inside the dictionary vector to ```ApplyParameters```.</span></span>

<span data-ttu-id="c96dd-179">Dentro do retorno de chamada OnRecognizedSpeech, os eventos de fala podem ser processados:</span><span class="sxs-lookup"><span data-stu-id="c96dd-179">Inside the OnRecognizedSpeech callback, the speech events can then be processed:</span></span>

```cpp
void SampleRemoteMain::OnRecognizedSpeech(const winrt::hstring& recognizedText)
{
    bool changedColor = false;
    DirectX::XMFLOAT4 color = {1, 1, 1, 1};

    if (recognizedText == L"Red")
    {
        color = {1, 0, 0, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Blue")
    {
        color = {0, 0, 1, 1};
        changedColor = true;
    }
    else if (recognizedText == L"Green")
    {
        ...
    }

    ...
}
```

## <a name="preview-streamed-content-locally"></a><span data-ttu-id="c96dd-180">Visualizar conteúdo transmitido localmente</span><span class="sxs-lookup"><span data-stu-id="c96dd-180">Preview streamed content locally</span></span>

<span data-ttu-id="c96dd-181">Para exibir o mesmo conteúdo no aplicativo remoto que é enviado para o dispositivo, o ```OnSendFrame``` evento do contexto remoto pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="c96dd-181">To display the same content in the remote app that is sent to the device the ```OnSendFrame``` event of the remote context can be used.</span></span> <span data-ttu-id="c96dd-182">O ```OnSendFrame``` evento é disparado toda vez que a biblioteca de comunicação remota do Holographic envia o quadro atual para o dispositivo remoto.</span><span class="sxs-lookup"><span data-stu-id="c96dd-182">The ```OnSendFrame``` event is triggered every time the Holographic Remoting library sends the current frame to the remote device.</span></span> <span data-ttu-id="c96dd-183">Esse é o momento ideal para pegar o conteúdo e também blit-lo na janela Desktop ou UWP.</span><span class="sxs-lookup"><span data-stu-id="c96dd-183">This is the ideal time to take the content and also blit it into the desktop or UWP window.</span></span>

```cpp
#include <windows.graphics.directx.direct3d11.interop.h>

...

m_onSendFrameEventRevoker = m_remoteContext.OnSendFrame(
    winrt::auto_revoke, [this](const winrt::Windows::Graphics::DirectX::Direct3D11::IDirect3DSurface& texture) {
        winrt::com_ptr<ID3D11Texture2D> texturePtr;
        {
            winrt::com_ptr<ID3D11Resource> resource;
            winrt::com_ptr<::IInspectable> inspectable = texture.as<::IInspectable>();
            winrt::com_ptr<Windows::Graphics::DirectX::Direct3D11::IDirect3DDxgiInterfaceAccess> dxgiInterfaceAccess;
            winrt::check_hresult(inspectable->QueryInterface(__uuidof(dxgiInterfaceAccess), dxgiInterfaceAccess.put_void()));
            winrt::check_hresult(dxgiInterfaceAccess->GetInterface(__uuidof(resource), resource.put_void()));
            resource.as(texturePtr);
        }

        // Copy / blit texturePtr into the back buffer here.
    });
```

## <a name="depth-reprojection"></a><span data-ttu-id="c96dd-184">Reprojeção de profundidade</span><span class="sxs-lookup"><span data-stu-id="c96dd-184">Depth Reprojection</span></span>

<span data-ttu-id="c96dd-185">A partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0), a comunicação remota Holographic dá suporte à [Reprojeção de profundidade](hologram-stability.md#reprojection).</span><span class="sxs-lookup"><span data-stu-id="c96dd-185">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0), Holographic Remoting supports [Depth Reprojection](hologram-stability.md#reprojection).</span></span> <span data-ttu-id="c96dd-186">Isso exige que o buffer de cores e o buffer de profundidade sejam transmitidos do aplicativo remoto para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c96dd-186">This requires both the color buffer and depth buffer to be streamed from the Remote application to the HoloLens 2.</span></span> <span data-ttu-id="c96dd-187">Por padrão, o streaming de buffer de profundidade é habilitado e configurado para usar metade da resolução do buffer de cores.</span><span class="sxs-lookup"><span data-stu-id="c96dd-187">By default depth buffer streaming is enabled and configured to use half the resolution of the color buffer.</span></span> <span data-ttu-id="c96dd-188">Isso pode ser alterado da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c96dd-188">This can be changed as follows:</span></span>

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

<span data-ttu-id="c96dd-189">Observe que, se os valores padrão não devem ser usados, ```ConfigureDepthVideoStream``` deve ser chamado antes de estabelecer uma conexão com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="c96dd-189">Note, if default values should not be used ```ConfigureDepthVideoStream``` must be called before establishing a connection to the HoloLens 2.</span></span> <span data-ttu-id="c96dd-190">O melhor local é logo após a criação do contexto remoto.</span><span class="sxs-lookup"><span data-stu-id="c96dd-190">The best place is right after you have created the remote context.</span></span> <span data-ttu-id="c96dd-191">Os valores possíveis para DepthBufferStreamResolution são:</span><span class="sxs-lookup"><span data-stu-id="c96dd-191">Possible values for DepthBufferStreamResolution are:</span></span>

* <span data-ttu-id="c96dd-192">Full_Resolution</span><span class="sxs-lookup"><span data-stu-id="c96dd-192">Full_Resolution</span></span>
* <span data-ttu-id="c96dd-193">Half_Resolution</span><span class="sxs-lookup"><span data-stu-id="c96dd-193">Half_Resolution</span></span>
* <span data-ttu-id="c96dd-194">Quarter_Resolution</span><span class="sxs-lookup"><span data-stu-id="c96dd-194">Quarter_Resolution</span></span>
* <span data-ttu-id="c96dd-195">Disabled (adicionado com a versão [2.1.3](holographic-remoting-version-history.md#v2.1.3) e, se usado, nenhum fluxo de vídeo de profundidade adicional é criado)</span><span class="sxs-lookup"><span data-stu-id="c96dd-195">Disabled (added with version [2.1.3](holographic-remoting-version-history.md#v2.1.3) and if used no additional depth video stream is created)</span></span>

<span data-ttu-id="c96dd-196">Tenha em mente que o uso de um buffer de profundidade de resolução completa também afeta os requisitos de largura de banda e precisa ser considerado no valor máximo de largura de banda fornecido para o ```CreateRemoteContext``` .</span><span class="sxs-lookup"><span data-stu-id="c96dd-196">Keep in mind that using a full resolution depth buffer also affects bandwidth requirements and needs to be accounted for in the maximum bandwidth value you provide to ```CreateRemoteContext```.</span></span>

<span data-ttu-id="c96dd-197">Ao lado de configurar a resolução, você também precisa confirmar um buffer de profundidade por meio de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="c96dd-197">Beside configuring the resolution, you also have to commit a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](https://docs.microsoft.com/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>

```cpp

void SampleRemoteMain::Render(HolographicFrame holographicFrame)
{
    ...

    m_deviceResources->UseHolographicCameraResources([this, holographicFrame](auto& cameraResourceMap) {
        
        ...

        for (auto cameraPose : prediction.CameraPoses())
        {
            DXHelper::CameraResources* pCameraResources = cameraResourceMap[cameraPose.HolographicCamera().Id()].get();

            ...

            m_deviceResources->UseD3DDeviceContext([&](ID3D11DeviceContext3* context) {
                
                ...

                // Commit depth buffer if available and enabled.
                if (m_canCommitDirect3D11DepthBuffer && m_commitDirect3D11DepthBuffer)
                {
                    auto interopSurface = pCameraResources->GetDepthStencilTextureInteropObject();
                    HolographicCameraRenderingParameters renderingParameters = holographicFrame.GetRenderingParameters(cameraPose);
                    renderingParameters.CommitDirect3D11DepthBuffer(interopSurface);
                }
            });
        }
    });
}

```

<span data-ttu-id="c96dd-198">Para verificar se a Reprojeção de profundidade está trabalhando corretamente no HoloLens 2, você pode habilitar um visualizador de profundidade por meio do portal do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c96dd-198">To verify if depth reprojection is correctly working on HoloLens 2, you can enable a depth visualizer via the Device Portal.</span></span> <span data-ttu-id="c96dd-199">Consulte [verificação de profundidade está definido corretamente](hologram-stability.md#verifying-depth-is-set-correctly) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="c96dd-199">See [Verifying Depth is Set Correctly](hologram-stability.md#verifying-depth-is-set-correctly) for details.</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="c96dd-200">Opcional: canais de dados personalizados</span><span class="sxs-lookup"><span data-stu-id="c96dd-200">Optional: Custom data channels</span></span>

<span data-ttu-id="c96dd-201">Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida.</span><span class="sxs-lookup"><span data-stu-id="c96dd-201">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="c96dd-202">Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c96dd-202">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="c96dd-203">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="c96dd-203">See Also</span></span>
* [<span data-ttu-id="c96dd-204">Como escrever um aplicativo personalizado do Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="c96dd-204">Writing a custom Holographic Remoting player app</span></span>](holographic-remoting-create-player.md)
* [<span data-ttu-id="c96dd-205">Canais de dados personalizados de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="c96dd-205">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="c96dd-206">Como estabelecer uma conexão segura com o Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="c96dd-206">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="c96dd-207">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="c96dd-207">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="c96dd-208">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="c96dd-208">Holographic Remoting software license terms</span></span>](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="c96dd-209">Política de Privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="c96dd-209">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)
