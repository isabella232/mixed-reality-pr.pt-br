---
title: Como criar um player personalizado de comunicação remota holográfica
description: Crie um aplicativo de comunicação remota Hologaphic personalizado para exibir o conteúdo renderizado em um computador remoto para o seu HoloLens 2.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicação remota, Holographic de comunicação remota, NuGet, manifesto de aplicativo, contexto do Player, aplicativo remoto, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: b6a0d65b8ec1f07f7ebaae17b9921d48105474a4
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581247"
---
# <a name="writing-a-custom-holographic-remoting-player-app"></a><span data-ttu-id="512fa-104">Como escrever um aplicativo personalizado do Holographic Remoting Player</span><span class="sxs-lookup"><span data-stu-id="512fa-104">Writing a custom Holographic Remoting player app</span></span>

>[!IMPORTANT]
><span data-ttu-id="512fa-105">Este documento descreve a criação de um aplicativo de player personalizado para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="512fa-105">This document describes the creation of a custom player application for HoloLens 2.</span></span> <span data-ttu-id="512fa-106">Os players personalizados escritos para o HoloLens 2 não são compatíveis com os aplicativos remotos escritos para o HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="512fa-106">Custom players written for HoloLens 2 are not compatible with remote applications written for HoloLens 1.</span></span> <span data-ttu-id="512fa-107">Isso implica que ambos os aplicativos devem usar o pacote NuGet versão **2. x**. x.</span><span class="sxs-lookup"><span data-stu-id="512fa-107">This implies that both applications must use NuGet package version **2.x.x**.</span></span>

<span data-ttu-id="512fa-108">Ao criar um aplicativo de Player remoto do Holographic personalizado, você pode criar um aplicativo personalizado capaz de exibir [exibições de imersão](../../design/app-views.md) em um computador remoto no seu HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="512fa-108">By creating a custom Holographic Remoting player app, you can create a custom application capable of displaying [immersive views](../../design/app-views.md) from on a remote machine on your HoloLens 2.</span></span> <span data-ttu-id="512fa-109">Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span><span class="sxs-lookup"><span data-stu-id="512fa-109">All code on this page and working projects can be found in the [Holographic Remoting samples github repository](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).</span></span>

<span data-ttu-id="512fa-110">Um player de comunicação remota Holographic permite que seu aplicativo exiba conteúdo Holographic [renderizado](rendering.md) em um computador desktop ou um dispositivo UWP como o Xbox One com acesso a mais recursos do sistema.</span><span class="sxs-lookup"><span data-stu-id="512fa-110">A Holographic Remoting player lets your app display holographic content [rendered](rendering.md) on a desktop PC or UWP device like the Xbox One with access to more system resources.</span></span> <span data-ttu-id="512fa-111">Um aplicativo de player de comunicação remota Holographic transmite dados de entrada para um aplicativo remoto de comunicação remota Holographic e recebe um modo de exibição de imersão como fluxo de áudio e vídeo.</span><span class="sxs-lookup"><span data-stu-id="512fa-111">A Holographic Remoting player app streams input data to a Holographic Remoting remote application and receives back an immersive view as video and audio stream.</span></span> <span data-ttu-id="512fa-112">A conexão é feita usando Wi-Fi padrão.</span><span class="sxs-lookup"><span data-stu-id="512fa-112">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="512fa-113">Para criar um aplicativo de Player, use um pacote NuGet para adicionar a comunicação remota do Holographic ao seu aplicativo UWP.</span><span class="sxs-lookup"><span data-stu-id="512fa-113">To create a player app, use a NuGet package to add Holographic Remoting to your UWP app.</span></span> <span data-ttu-id="512fa-114">Em seguida, escreva o código para manipular a conexão e exibir uma exibição de imersão.</span><span class="sxs-lookup"><span data-stu-id="512fa-114">Then write code to handle the connection and to display an immersive view.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="512fa-115">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="512fa-115">Prerequisites</span></span>

<span data-ttu-id="512fa-116">Um bom ponto de partida é um aplicativo UWP de trabalho baseado em DirectX que já tem como alvo a API de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="512fa-116">A good starting point is a working DirectX based UWP app that already targets the Windows Mixed Reality API.</span></span> <span data-ttu-id="512fa-117">Para obter detalhes, consulte [visão geral do desenvolvimento do DirectX](../native/directx-development-overview.md).</span><span class="sxs-lookup"><span data-stu-id="512fa-117">For details see [DirectX development overview](../native/directx-development-overview.md).</span></span> <span data-ttu-id="512fa-118">Se você não tiver um aplicativo existente e quiser começar do zero, o [modelo de projeto do C++ Holographic](../native/creating-a-holographic-directx-project.md) será um bom ponto de partida.</span><span class="sxs-lookup"><span data-stu-id="512fa-118">If you don't have an existing app and want to start from scratch the [C++ holographic project template](../native/creating-a-holographic-directx-project.md) is a good starting point.</span></span>

>[!IMPORTANT]
><span data-ttu-id="512fa-119">Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](//windows/win32/com/multithreaded-apartments)multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="512fa-119">Any app using Holographic Remoting should be authored to use a [multi-threaded apartment](//windows/win32/com/multithreaded-apartments).</span></span> <span data-ttu-id="512fa-120">O uso de um [apartamento de thread único](//windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução.</span><span class="sxs-lookup"><span data-stu-id="512fa-120">The use of a [single-threaded apartment](//windows/win32/com/single-threaded-apartments) is supported but will lead to sub-optimal performance and possibly stuttering during playback.</span></span> <span data-ttu-id="512fa-121">Ao usar C++/WinRT [WinRT:: init_apartment](//windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.</span><span class="sxs-lookup"><span data-stu-id="512fa-121">When using C++/WinRT [winrt::init_apartment](//windows/uwp/cpp-and-winrt-apis/get-started) a multi-threaded apartment is the default.</span></span>

## <a name="get-the-holographic-remoting-nuget-package"></a><span data-ttu-id="512fa-122">Obter o pacote NuGet de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="512fa-122">Get the Holographic Remoting NuGet package</span></span>

<span data-ttu-id="512fa-123">As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="512fa-123">The following steps are required to add the NuGet package to a project in Visual Studio.</span></span>
1. <span data-ttu-id="512fa-124">Abra o projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="512fa-124">Open the project in Visual Studio.</span></span>
2. <span data-ttu-id="512fa-125">Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="512fa-125">Right-click the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="512fa-126">No painel que aparece, selecione **procurar** e, em seguida, pesquise "comunicação remota do Holographic".</span><span class="sxs-lookup"><span data-stu-id="512fa-126">In the panel that appears, select **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="512fa-127">Selecione **Microsoft. Holographic. Remoting**, certifique-se de selecionar a versão **2. x. x** mais recente e selecione **instalar**.</span><span class="sxs-lookup"><span data-stu-id="512fa-127">Select **Microsoft.Holographic.Remoting**, ensure to pick the latest **2.x.x** version and select **Install**.</span></span>
5. <span data-ttu-id="512fa-128">Se a caixa de diálogo **Visualizar** for exibida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="512fa-128">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="512fa-129">Selecione **aceito quando o** diálogo do contrato de licença for exibido.</span><span class="sxs-lookup"><span data-stu-id="512fa-129">Select **I Accept** when the license agreement dialog appears.</span></span>

>[!IMPORTANT]
><a name="idl"></a><span data-ttu-id="512fa-130">O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API exposta pela comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="512fa-130">The ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` inside the NuGet package contains detailed documentation for the API exposed by Holographic Remoting.</span></span>

## <a name="modify-the-packageappxmanifest-of-the-application"></a><span data-ttu-id="512fa-131">Modificar o Package. appxmanifest do aplicativo</span><span class="sxs-lookup"><span data-stu-id="512fa-131">Modify the Package.appxmanifest of the application</span></span>

<span data-ttu-id="512fa-132">Para tornar o aplicativo ciente do Microsoft.Holographic.AppRemoting.dll adicionado pelo pacote NuGet, as etapas a seguir precisam ser executadas no projeto:</span><span class="sxs-lookup"><span data-stu-id="512fa-132">To make the application aware of the Microsoft.Holographic.AppRemoting.dll added by the NuGet package, the following steps need to be taken on the project:</span></span>

1. <span data-ttu-id="512fa-133">No Gerenciador de Soluções clique com o botão direito do mouse no arquivo **Package. appxmanifest** e selecione **abrir com...**</span><span class="sxs-lookup"><span data-stu-id="512fa-133">In the Solution Explorer right-click on the **Package.appxmanifest** file and select **Open With...**</span></span>
2. <span data-ttu-id="512fa-134">Selecione **Editor de XML (texto)** e selecione **OK**</span><span class="sxs-lookup"><span data-stu-id="512fa-134">Select **XML (Text) Editor** and select **OK**</span></span>
3. <span data-ttu-id="512fa-135">Adicione as seguintes linhas ao arquivo e salve</span><span class="sxs-lookup"><span data-stu-id="512fa-135">Add the following lines to the file and save</span></span>
```xml
  </Capabilities>

  <!--Add lines below -->
  <Extensions>
    <Extension Category="windows.activatableClass.inProcessServer">
      <InProcessServer>
        <Path>Microsoft.Holographic.AppRemoting.dll</Path>
        <ActivatableClass ActivatableClassId="Microsoft.Holographic.AppRemoting.PlayerContext" ThreadingModel="both" />
      </InProcessServer>
    </Extension>
  </Extensions>
  <!--Add lines above -->

</Package>
```
## <a name="create-the-player-context"></a><span data-ttu-id="512fa-136">Criar o contexto do Player</span><span class="sxs-lookup"><span data-stu-id="512fa-136">Create the player context</span></span>

<span data-ttu-id="512fa-137">Como primeira etapa, o aplicativo deve criar um contexto de Player.</span><span class="sxs-lookup"><span data-stu-id="512fa-137">As a first step the application should create a player context.</span></span>

```cpp
// class declaration:

#include <winrt/Microsoft.Holographic.AppRemoting.h>

...

private:
// PlayerContext used to connect with a Holographic Remoting remote app and display remotely rendered frames
winrt::Microsoft::Holographic::AppRemoting::PlayerContext m_playerContext = nullptr;
```


```cpp
// class implementation:

// Create the player context
// IMPORTANT: This must be done before creating the HolographicSpace (or any other call to the Holographic API).
m_playerContext = winrt::Microsoft::Holographic::AppRemoting::PlayerContext::Create();

```

>[!WARNING]
><span data-ttu-id="512fa-138">O Holographic Remoting funciona substituindo o tempo de execução do Windows Mixed Reality que faz parte do Windows com um tempo de execução específico de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="512fa-138">Holographic Remoting works by replacing the Windows Mixed Reality runtime which is part of Windows with a remoting specific runtime.</span></span> <span data-ttu-id="512fa-139">Isso é feito durante a criação do contexto do Player.</span><span class="sxs-lookup"><span data-stu-id="512fa-139">This is done during the creation of the player context.</span></span> <span data-ttu-id="512fa-140">Por esse motivo, qualquer chamada em qualquer API de realidade mista do Windows antes de criar o contexto do player pode resultar em um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="512fa-140">For that reason any call on any Windows Mixed Reality API before creating the player context can result in unexpected behavior.</span></span> <span data-ttu-id="512fa-141">A abordagem recomendada é criar o contexto do Player o mais cedo possível antes da interação com qualquer API de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="512fa-141">The recommended approach is to create the player context as early as possible before interaction with any Mixed Reality API.</span></span> <span data-ttu-id="512fa-142">Nunca misture objetos criados ou recuperados por meio de qualquer API de realidade mista do Windows antes da chamada para ```PlayerContext::Create``` com objetos criados ou recuperados posteriormente.</span><span class="sxs-lookup"><span data-stu-id="512fa-142">Never mix objects created or retrieved through any Windows Mixed Reality API before the call to ```PlayerContext::Create``` with objects created or retrieved afterwards.</span></span>

<span data-ttu-id="512fa-143">Em seguida, o HolographicSpace pode ser criado chamando [HolographicSpace. CreateForCoreWindow](//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span><span class="sxs-lookup"><span data-stu-id="512fa-143">Next the HolographicSpace can be created, by calling [HolographicSpace.CreateForCoreWindow](//uwp/api/windows.graphics.holographic.holographicspace.createforcorewindow).</span></span>

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(window);
```

## <a name="connect-to-the-remote-app"></a><span data-ttu-id="512fa-144">Conectar-se ao aplicativo remoto</span><span class="sxs-lookup"><span data-stu-id="512fa-144">Connect to the remote app</span></span>

<span data-ttu-id="512fa-145">Depois que o aplicativo de Player estiver pronto para o processamento de conteúdo, pode ser estabelecida uma conexão com o aplicativo remoto.</span><span class="sxs-lookup"><span data-stu-id="512fa-145">Once the player app is ready for rendering content a connection to the remote app can be established.</span></span>

<span data-ttu-id="512fa-146">A conexão pode ser estabelecida de uma das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="512fa-146">The connection can be established in one of the following ways:</span></span>
1) <span data-ttu-id="512fa-147">O aplicativo de Player em execução no HoloLens 2 se conecta ao aplicativo remoto.</span><span class="sxs-lookup"><span data-stu-id="512fa-147">The player app running on HoloLens 2 connects to the remote app.</span></span>
2) <span data-ttu-id="512fa-148">O aplicativo remoto se conecta ao aplicativo de Player em execução no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="512fa-148">The remote app connects to the player app running on HoloLens 2.</span></span>

<span data-ttu-id="512fa-149">Para se conectar do aplicativo Player ao aplicativo remoto, chame o ```Connect``` método no contexto do Player especificando o nome do host e a porta.</span><span class="sxs-lookup"><span data-stu-id="512fa-149">To connect from the player app to the remote app call the ```Connect``` method on the player context specifying the hostname and port.</span></span> <span data-ttu-id="512fa-150">A porta padrão é **8265**.</span><span class="sxs-lookup"><span data-stu-id="512fa-150">The default port is **8265**.</span></span>

```cpp
try
{
    m_playerContext.Connect(m_hostname, m_port);
}
catch(winrt::hresult_error& e)
{
    // Failed to connect. Get an error details via e.code() and e.message()
}
```

>[!IMPORTANT]
><span data-ttu-id="512fa-151">Assim como acontece com qualquer API do C++/WinRT, você ```Connect``` pode lançar um WinRT:: hresult_error que precisa ser manipulado.</span><span class="sxs-lookup"><span data-stu-id="512fa-151">As with any C++/WinRT API ```Connect``` might throw an winrt::hresult_error which needs to be handled.</span></span>

<span data-ttu-id="512fa-152">A escuta de conexões de entrada no aplicativo de player pode ser feita chamando o ```Listen``` método.</span><span class="sxs-lookup"><span data-stu-id="512fa-152">Listening for incoming connections on the player app can be done by calling the ```Listen``` method.</span></span> <span data-ttu-id="512fa-153">A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada.</span><span class="sxs-lookup"><span data-stu-id="512fa-153">Both the handshake port and transport port can be specified during this call.</span></span> <span data-ttu-id="512fa-154">A porta de handshake é usada para o handshake inicial.</span><span class="sxs-lookup"><span data-stu-id="512fa-154">The handshake port is used for the initial handshake.</span></span> <span data-ttu-id="512fa-155">Os dados são enviados pela porta de transporte.</span><span class="sxs-lookup"><span data-stu-id="512fa-155">The data is then sent over the transport port.</span></span> <span data-ttu-id="512fa-156">Por padrão, o número da porta **8265** e **8266** são usados.</span><span class="sxs-lookup"><span data-stu-id="512fa-156">By default port number **8265** and **8266** are used.</span></span>

```cpp
try
{
    m_playerContext.Listen(L"0.0.0.0", m_port, m_port + 1);
}
catch(winrt::hresult_error& e)
{
    // Failed to listen. Get an error details via e.code() and e.message()
}
```


## <a name="handling-connection-related-events"></a><span data-ttu-id="512fa-157">Manipulando eventos relacionados à conexão</span><span class="sxs-lookup"><span data-stu-id="512fa-157">Handling connection-related events</span></span>

<span data-ttu-id="512fa-158">O ```PlayerContext``` expõe três eventos para monitorar o estado da conexão</span><span class="sxs-lookup"><span data-stu-id="512fa-158">The ```PlayerContext``` exposes three events to monitor the state of the connection</span></span>
1) <span data-ttu-id="512fa-159">Onconnected: disparado quando uma conexão com o aplicativo remoto foi estabelecida com êxito.</span><span class="sxs-lookup"><span data-stu-id="512fa-159">OnConnected: Triggered when a connection to the remote app has been successfully established.</span></span>
```cpp
m_onConnectedEventToken = m_playerContext.OnConnected([]() 
{
    // Handle connection successfully established
});
```
2) <span data-ttu-id="512fa-160">OnDisconnect: disparado se uma conexão estabelecida for encerrada ou não foi possível estabelecer uma conexão.</span><span class="sxs-lookup"><span data-stu-id="512fa-160">OnDisconnected: Triggered if an established connection is terminated or a connection couldn't be established.</span></span>
```cpp
m_onDisconnectedEventToken = m_playerContext.OnDisconnected([](ConnectionFailureReason failureReason)
{
    switch (failureReason)
    {
        // Handle connection failed or terminated.
        // See ConnectionFailureReason for possible reasons.
    }
}
```
>[!NOTE]
><span data-ttu-id="512fa-161">Os ```ConnectionFailureReason``` valores possíveis são documentados no ```Microsoft.Holographic.AppRemoting.idl``` [arquivo](#idl).</span><span class="sxs-lookup"><span data-stu-id="512fa-161">Possible ```ConnectionFailureReason``` values are documented in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

3) <span data-ttu-id="512fa-162">Desescutando: quando a escuta de conexões de entrada é iniciada.</span><span class="sxs-lookup"><span data-stu-id="512fa-162">OnListening: When listening for incoming connections starts.</span></span>
```cpp
m_onListeningEventToken = m_playerContext.OnListening([]()
{
    // Handle start listening for incoming connections
});
```

<span data-ttu-id="512fa-163">Além disso, o estado da conexão pode ser consultado usando a ```ConnectionState``` propriedade no contexto do Player.</span><span class="sxs-lookup"><span data-stu-id="512fa-163">Additionally the connection state can be queried using the ```ConnectionState``` property on the player context.</span></span>
```cpp
winrt::Microsoft::Holographic::AppRemoting::ConnectionState state = m_playerContext.ConnectionState();
```

## <a name="display-the-remotely-rendered-frame"></a><span data-ttu-id="512fa-164">Exibir o quadro processado remotamente</span><span class="sxs-lookup"><span data-stu-id="512fa-164">Display the remotely rendered frame</span></span>

<span data-ttu-id="512fa-165">Para exibir o conteúdo renderizado remotamente, chame ```PlayerContext::BlitRemoteFrame``` ao renderizar um [HolographicFrame](//uwp/api/windows.graphics.holographic.holographicframe).</span><span class="sxs-lookup"><span data-stu-id="512fa-165">To display the remotely rendered content, call ```PlayerContext::BlitRemoteFrame``` while rendering a [HolographicFrame](//uwp/api/windows.graphics.holographic.holographicframe).</span></span> 

<span data-ttu-id="512fa-166">```BlitRemoteFrame``` requer que o buffer de fundo para o HolographicFrame atual seja associado como destino de renderização.</span><span class="sxs-lookup"><span data-stu-id="512fa-166">```BlitRemoteFrame``` requires that the back buffer for the current HolographicFrame is bound as render target.</span></span> <span data-ttu-id="512fa-167">O buffer de fundo pode ser recebido do [HolographicCameraRenderingParameters](//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) por meio da propriedade [Direct3D11BackBuffer](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) .</span><span class="sxs-lookup"><span data-stu-id="512fa-167">The back buffer can be received from the [HolographicCameraRenderingParameters](//uwp/api/windows.graphics.holographic.holographicframe.getrenderingparameters) via the [Direct3D11BackBuffer](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.direct3d11backbuffer) property.</span></span>

<span data-ttu-id="512fa-168">Quando chamado, ```BlitRemoteFrame``` o copia o último quadro recebido do aplicativo remoto para o BackBuffer do HolographicFrame.</span><span class="sxs-lookup"><span data-stu-id="512fa-168">When called, ```BlitRemoteFrame``` copies the latest received frame from the remote application into the BackBuffer of the HolographicFrame.</span></span> <span data-ttu-id="512fa-169">Além disso, o conjunto de pontos de foco é definido, se o aplicativo remoto tiver especificado um ponto de foco durante a renderização do quadro remoto.</span><span class="sxs-lookup"><span data-stu-id="512fa-169">Additionally the focus point set is set, if the remote application has specified a focus point during the rendering of the remote frame.</span></span>

```cpp
// Blit the remote frame into the backbuffer for the HolographicFrame.
winrt::Microsoft::Holographic::AppRemoting::BlitResult result = m_playerContext.BlitRemoteFrame();
```

>[!NOTE]
><span data-ttu-id="512fa-170">```PlayerContext::BlitRemoteFrame``` Substitui potencialmente o ponto de foco do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="512fa-170">```PlayerContext::BlitRemoteFrame``` potentially overwrites the focus point for the current frame.</span></span> 
>- <span data-ttu-id="512fa-171">Para especificar um ponto de foco de fallback, chame [HolographicCameraRenderingParameters:: SetFocusPoint](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) antes de ```PlayerContext::BlitRemoteFrame``` .</span><span class="sxs-lookup"><span data-stu-id="512fa-171">To specify a fallback focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint) before ```PlayerContext::BlitRemoteFrame```.</span></span> 
>- <span data-ttu-id="512fa-172">Para substituir o ponto de foco remoto, chame [HolographicCameraRenderingParameters:: SetFocusPoint](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  após ```PlayerContext::BlitRemoteFrame``` .</span><span class="sxs-lookup"><span data-stu-id="512fa-172">To overwrite the remote focus point, call [HolographicCameraRenderingParameters::SetFocusPoint](//uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.setfocuspoint)  after ```PlayerContext::BlitRemoteFrame```.</span></span>

<span data-ttu-id="512fa-173">Em caso de sucesso, ```BlitRemoteFrame``` retorna ```BlitResult::Success_Color``` .</span><span class="sxs-lookup"><span data-stu-id="512fa-173">On success, ```BlitRemoteFrame``` returns ```BlitResult::Success_Color```.</span></span> <span data-ttu-id="512fa-174">Caso contrário, ele retornará o motivo da falha:</span><span class="sxs-lookup"><span data-stu-id="512fa-174">Otherwise it returns the failure reason:</span></span>
- <span data-ttu-id="512fa-175">```BlitResult::Failed_NoRemoteFrameAvailable```: Falhou porque nenhum quadro remoto está disponível.</span><span class="sxs-lookup"><span data-stu-id="512fa-175">```BlitResult::Failed_NoRemoteFrameAvailable```: Failed because no remote frame is available.</span></span>
- <span data-ttu-id="512fa-176">```BlitResult::Failed_NoCamera```: Falhou porque nenhuma câmera presente.</span><span class="sxs-lookup"><span data-stu-id="512fa-176">```BlitResult::Failed_NoCamera```: Failed because no camera present.</span></span>
- <span data-ttu-id="512fa-177">```BlitResult::Failed_RemoteFrameTooOld```: Falhou porque a estrutura remota é muito antiga (consulte a propriedade PlayerContext:: BlitRemoteFrameTimeout).</span><span class="sxs-lookup"><span data-stu-id="512fa-177">```BlitResult::Failed_RemoteFrameTooOld```: Failed because remote frame is too old (see PlayerContext::BlitRemoteFrameTimeout property).</span></span>

>[!IMPORTANT]
> <span data-ttu-id="512fa-178">A partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0) , é possível que um jogador personalizado use a Reprojeção de profundidade por meio da comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="512fa-178">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) it is possible with a custom player to use depth reprojection via Holographic Remoting.</span></span>

<span data-ttu-id="512fa-179">```BlitResult``` também pode retornar ```BlitResult::Success_Color_Depth``` sob as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="512fa-179">```BlitResult``` can also return ```BlitResult::Success_Color_Depth``` under the following conditions:</span></span>

- <span data-ttu-id="512fa-180">O aplicativo remoto confirmou um buffer de profundidade por meio de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span><span class="sxs-lookup"><span data-stu-id="512fa-180">The remote app has committed a depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).</span></span>
- <span data-ttu-id="512fa-181">O aplicativo de player personalizado um buffer de profundidade válido antes de chamar ```BlitRemoteFrame``` .</span><span class="sxs-lookup"><span data-stu-id="512fa-181">The custom player app has bound a valid depth buffer before calling ```BlitRemoteFrame```.</span></span>

<span data-ttu-id="512fa-182">Se essas condições forem atendidas ```BlitRemoteFrame``` , blit a profundidade remota no buffer de profundidade local atualmente associado.</span><span class="sxs-lookup"><span data-stu-id="512fa-182">If these conditions are met ```BlitRemoteFrame``` will blit the remote depth into the currently bound local depth buffer.</span></span> <span data-ttu-id="512fa-183">Em seguida, você pode renderizar conteúdo local adicional, que terá a interseção de profundidade com o conteúdo renderizado remotamente.</span><span class="sxs-lookup"><span data-stu-id="512fa-183">You can then render additional local content, which will have depth intersection with the remote rendered content.</span></span> <span data-ttu-id="512fa-184">Além disso, você pode confirmar o buffer de profundidade local por meio de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) em seu player personalizado para ter uma Reprojeção de profundidade para conteúdo renderizado remoto e local.</span><span class="sxs-lookup"><span data-stu-id="512fa-184">Additionally you can commit the local depth buffer via [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_) in your custom player to have depth reprojection for remote and local rendered content.</span></span> <span data-ttu-id="512fa-185">Consulte [Reprojeção de profundidade](hologram-stability.md#reprojection) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="512fa-185">See [Depth Reprojection](hologram-stability.md#reprojection) for details.</span></span>

### <a name="projection-transform-mode"></a><span data-ttu-id="512fa-186">Modo de transformação de projeção</span><span class="sxs-lookup"><span data-stu-id="512fa-186">Projection Transform Mode</span></span>

<span data-ttu-id="512fa-187">Um problema, que se superfícies ao usar a Reprojeção de profundidade por meio da comunicação remota do Holographic é que o conteúdo remoto pode ser renderizado com uma transformação de projeção diferente do conteúdo local processado diretamente pelo seu aplicativo de player personalizado.</span><span class="sxs-lookup"><span data-stu-id="512fa-187">One problem, which surfaces when using depth reprojection via Holographic Remoting is that the remote content can be rendered with a different projection transform than local content directly rendered by your custom player app.</span></span> <span data-ttu-id="512fa-188">Um caso de uso comum é especificar valores diferentes para o plano próximo e longe (via [HolographicCamera:: SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) e [HolographicCamera:: SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) no lado do Player e no lado remoto.</span><span class="sxs-lookup"><span data-stu-id="512fa-188">A common use-case is to specify different values for near and far plane (via [HolographicCamera::SetNearPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setnearplanedistance) and [HolographicCamera::SetFarPlaneDistance](/uwp/api/windows.graphics.holographic.holographiccamera.setfarplanedistance)) on the player side and the remote side.</span></span> <span data-ttu-id="512fa-189">Nesse caso, não fica claro se a transformação de projeção no lado do jogador deve refletir as distâncias do plano Near/distante remotas ou os locais.</span><span class="sxs-lookup"><span data-stu-id="512fa-189">In this case, it's not clear if the projection transform on the player side should reflect the remote near/far plane distances or the local ones.</span></span>

<span data-ttu-id="512fa-190">A partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0) , você pode controlar o modo de transformação projeção via ```PlayerContext::ProjectionTransformConfig``` .</span><span class="sxs-lookup"><span data-stu-id="512fa-190">Starting with version [2.1.0](holographic-remoting-version-history.md#v2.1.0) you can control the projection transform mode via ```PlayerContext::ProjectionTransformConfig```.</span></span> <span data-ttu-id="512fa-191">Os valores com suporte são:</span><span class="sxs-lookup"><span data-stu-id="512fa-191">Supported values are:</span></span>

- <span data-ttu-id="512fa-192">```Local``` - [HolographicCameraPose::P rojectiontransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) retorna uma transformação de projeção, que reflete as distâncias do plano próximo/longe definidas pelo seu aplicativo de player personalizado no HolographicCamera.</span><span class="sxs-lookup"><span data-stu-id="512fa-192">```Local``` - [HolographicCameraPose::ProjectionTransform](/uwp/api/windows.graphics.holographic.holographiccamerapose.projectiontransform) returns a projection transform, which reflects the near/far plane distances set by your custom player app on the HolographicCamera.</span></span>
- <span data-ttu-id="512fa-193">```Remote``` -A transformação de projeção reflete as distâncias do plano próximo/longe especificadas pelo aplicativo remoto.</span><span class="sxs-lookup"><span data-stu-id="512fa-193">```Remote``` - Projection transform reflects the near/far plane distances specified by the remote app.</span></span>
- <span data-ttu-id="512fa-194">```Merged``` -As distâncias do plano próximo/longe do seu aplicativo remoto e do seu aplicativo de player personalizado são mescladas.</span><span class="sxs-lookup"><span data-stu-id="512fa-194">```Merged``` - Near/Far plane distances from your remote app and your custom player app are merged.</span></span> <span data-ttu-id="512fa-195">Por padrão, isso é feito por meio do mínimo de distâncias do plano próximo e do máximo de distâncias do plano distante.</span><span class="sxs-lookup"><span data-stu-id="512fa-195">By default this is done by taking the minimum of the near plane distances and the maximum of the far plane distances.</span></span> <span data-ttu-id="512fa-196">Caso o lado remoto ou local sejam invertidos, digamos que < perto, as distâncias remotas do plano próximo/longe são invertidas.</span><span class="sxs-lookup"><span data-stu-id="512fa-196">In case either the remote or local side are inverted, say far < near, the remote near/far plane distances are flipped.</span></span>

## <a name="optional-set-blitremoteframetimeout"></a><span data-ttu-id="512fa-197">Opcional: definir BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span><span class="sxs-lookup"><span data-stu-id="512fa-197">Optional: Set BlitRemoteFrameTimeout <a name="BlitRemoteFrameTimeout"></a></span></span>
>[!IMPORTANT]
> <span data-ttu-id="512fa-198">```PlayerContext::BlitRemoteFrameTimeout``` tem suporte a partir da versão [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span><span class="sxs-lookup"><span data-stu-id="512fa-198">```PlayerContext::BlitRemoteFrameTimeout``` is supported starting with version [2.0.9](holographic-remoting-version-history.md#v2.0.9).</span></span> 

<span data-ttu-id="512fa-199">A ```PlayerContext::BlitRemoteFrameTimeout``` propriedade especifica a quantidade de tempo que um quadro remoto será reutilizado se nenhum quadro remoto for recebido.</span><span class="sxs-lookup"><span data-stu-id="512fa-199">The ```PlayerContext::BlitRemoteFrameTimeout``` property specifies the amount of time a remote frame is reused if no new remote frame is received.</span></span> 

<span data-ttu-id="512fa-200">Um caso de uso comum é habilitar o tempo limite de BlitRemoteFrame para exibir uma tela em branco se nenhum novo quadro for recebido por um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="512fa-200">A common use-case is to enable the BlitRemoteFrame timeout to display a blank screen if no new frames are received for a certain amount of time.</span></span> <span data-ttu-id="512fa-201">Quando habilitado, o tipo de retorno do ```BlitRemoteFrame``` método também pode ser usado para alternar para um conteúdo de fallback processado localmente.</span><span class="sxs-lookup"><span data-stu-id="512fa-201">When enabled the return type of the ```BlitRemoteFrame``` method can also be used to switch to a locally rendered fallback content.</span></span> 

<span data-ttu-id="512fa-202">Para habilitar o tempo limite, defina o valor da propriedade como uma duração igual ou maior que 100 ms.</span><span class="sxs-lookup"><span data-stu-id="512fa-202">To enable the timeout, set the property value to a duration equal or greater than 100 ms.</span></span> <span data-ttu-id="512fa-203">Para desabilitar o tempo limite, defina a propriedade como duração zero.</span><span class="sxs-lookup"><span data-stu-id="512fa-203">To disable the timeout, set the property to zero duration.</span></span> <span data-ttu-id="512fa-204">Se o tempo limite for habilitado e nenhum quadro remoto for recebido para a duração definida, o BlitRemoteFrame falhará e retornará ```Failed_RemoteFrameTooOld``` até que um novo quadro remoto seja recebido.</span><span class="sxs-lookup"><span data-stu-id="512fa-204">If the timeout is enabled and no remote frame is received for the set duration, BlitRemoteFrame will fail and return ```Failed_RemoteFrameTooOld``` until a new remote frame is received.</span></span>

```cpp
using namespace std::chrono_literals;

// Set the BlitRemoteFrame timeout to 0.5s
m_playerContext.BlitRemoteFrameTimeout(500ms);
```

## <a name="optional-get-statistics-about-the-last-remote-frame"></a><span data-ttu-id="512fa-205">Opcional: obter estatísticas sobre o último quadro remoto</span><span class="sxs-lookup"><span data-stu-id="512fa-205">Optional: Get statistics about the last remote frame</span></span>

<span data-ttu-id="512fa-206">Para diagnosticar problemas de desempenho ou de rede, as estatísticas sobre o último quadro remoto podem ser recuperadas por meio da ```PlayerContext::LastFrameStatistics``` propriedade.</span><span class="sxs-lookup"><span data-stu-id="512fa-206">To diagnose performance or network issues, statistics about the last remote frame can be retrieved via the ```PlayerContext::LastFrameStatistics``` property.</span></span> <span data-ttu-id="512fa-207">As estatísticas são atualizadas durante a chamada para [HolographicFrame::P resentusingcurrentprediction](//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span><span class="sxs-lookup"><span data-stu-id="512fa-207">Statistics are updated during the call to [HolographicFrame::PresentUsingCurrentPrediction](//uwp/api/windows.graphics.holographic.holographicframe.presentusingcurrentprediction).</span></span>

```cpp
// Get statistics for the last presented frame.
winrt::Microsoft::Holographic::AppRemoting::PlayerFrameStatistics statistics = m_playerContext.LastFrameStatistics();
```

<span data-ttu-id="512fa-208">Para obter mais informações, consulte a ```PlayerFrameStatistics``` documentação no ```Microsoft.Holographic.AppRemoting.idl``` [arquivo](#idl).</span><span class="sxs-lookup"><span data-stu-id="512fa-208">For more information, see the ```PlayerFrameStatistics``` documentation in the ```Microsoft.Holographic.AppRemoting.idl``` [file](#idl).</span></span>

## <a name="optional-custom-data-channels"></a><span data-ttu-id="512fa-209">Opcional: canais de dados personalizados</span><span class="sxs-lookup"><span data-stu-id="512fa-209">Optional: Custom data channels</span></span>

<span data-ttu-id="512fa-210">Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida.</span><span class="sxs-lookup"><span data-stu-id="512fa-210">Custom data channels can be used to send user data over the already established remoting connection.</span></span> <span data-ttu-id="512fa-211">Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="512fa-211">See [custom data channels](holographic-remoting-custom-data-channels.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="512fa-212">Consulte Também</span><span class="sxs-lookup"><span data-stu-id="512fa-212">See Also</span></span>
* [<span data-ttu-id="512fa-213">Escrevendo um aplicativo remoto de comunicação remota do Holographic usando as APIs de realidade mista do Windows</span><span class="sxs-lookup"><span data-stu-id="512fa-213">Writing a Holographic Remoting remote app using Windows Mixed Reality APIs</span></span>](holographic-remoting-create-remote-wmr.md)
* [<span data-ttu-id="512fa-214">Escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR</span><span class="sxs-lookup"><span data-stu-id="512fa-214">Writing a Holographic Remoting remote app using OpenXR APIs</span></span>](holographic-remoting-create-remote-openxr.md)
* [<span data-ttu-id="512fa-215">Canais de dados personalizados de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="512fa-215">Custom Holographic Remoting data channels</span></span>](holographic-remoting-custom-data-channels.md)
* [<span data-ttu-id="512fa-216">Como estabelecer uma conexão segura com o Holographic Remoting</span><span class="sxs-lookup"><span data-stu-id="512fa-216">Establishing a secure connection with Holographic Remoting</span></span>](holographic-remoting-secure-connection.md)
* [<span data-ttu-id="512fa-217">Solução de problemas e limitações de comunicação remota do Holographic</span><span class="sxs-lookup"><span data-stu-id="512fa-217">Holographic Remoting troubleshooting and limitations</span></span>](holographic-remoting-troubleshooting.md)
* [<span data-ttu-id="512fa-218">Termos de licença de software de comunicação remota holográfica</span><span class="sxs-lookup"><span data-stu-id="512fa-218">Holographic Remoting software license terms</span></span>](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [<span data-ttu-id="512fa-219">Política de Privacidade da Microsoft</span><span class="sxs-lookup"><span data-stu-id="512fa-219">Microsoft Privacy Statement</span></span>](https://go.microsoft.com/fwlink/?LinkId=521839)