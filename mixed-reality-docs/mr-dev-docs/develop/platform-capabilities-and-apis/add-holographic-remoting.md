---
title: Adicionar comunicação remota do Holographic
description: Saiba como instalar, configurar e usar a comunicação remota do Holographic para renderizar hologramas em um dispositivo HoloLens pela rede.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Realidade mista do Windows, hologramas, comunicação remota Holographic, renderização remota, renderização de rede, HoloLens, hologramas remotos, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual
ms.openlocfilehash: 68c1dd43dac4830da061d4900ce768692057e781
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006666"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a><span data-ttu-id="6528a-104">Adicionar comunicação remota Holographic (HoloLens (primeira gen))</span><span class="sxs-lookup"><span data-stu-id="6528a-104">Add Holographic Remoting (HoloLens (first gen))</span></span>

>[!IMPORTANT]
> <span data-ttu-id="6528a-105">Este documento descreve a criação de um aplicativo host para o HoloLens 1.</span><span class="sxs-lookup"><span data-stu-id="6528a-105">This document describes the creation of a host application for HoloLens 1.</span></span> <span data-ttu-id="6528a-106">O aplicativo de host para o **HoloLens (1º gen)** deve usar o pacote NuGet versão **1. x**. x.</span><span class="sxs-lookup"><span data-stu-id="6528a-106">Host application for **HoloLens (1st gen)** must use NuGet package version **1.x.x**.</span></span> <span data-ttu-id="6528a-107">Isso implica que os aplicativos host escritos para o HoloLens 1 não são compatíveis com o HoloLens 2 e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="6528a-107">This implies that host applications written for HoloLens 1 are not compatible with HoloLens 2 and vice versa.</span></span>

## <a name="hololens-2"></a><span data-ttu-id="6528a-108">HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="6528a-108">HoloLens 2</span></span>

<span data-ttu-id="6528a-109">Os desenvolvedores de HoloLens que usam a comunicação remota do Holographic precisarão atualizar seus aplicativos para torná-los compatíveis com o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="6528a-109">HoloLens developers using Holographic Remoting will need to update their apps to make them compatible with HoloLens 2.</span></span> <span data-ttu-id="6528a-110">Isso requer uma nova versão do pacote NuGet de comunicação remota do Holographic.</span><span class="sxs-lookup"><span data-stu-id="6528a-110">This requires a new version of the Holographic Remoting NuGet package.</span></span> <span data-ttu-id="6528a-111">Certifique-se de usar a versão 2.0.0.0 ou superior do pacote do NuGet de comunicação remota do Holographic ao se conectar ao Player de comunicação remota do Holographic no HoloLens 2 ou a conexão falhará.</span><span class="sxs-lookup"><span data-stu-id="6528a-111">Be sure to use version 2.0.0.0 or above of the Holographic Remoting NuGet package when connecting to the Holographic Remoting Player on HoloLens 2 or the connection will fail.</span></span>

>[!NOTE]
> <span data-ttu-id="6528a-112">As diretrizes específicas para o HoloLens 2 podem ser encontradas [aqui](holographic-remoting-create-remote-wmr.md).</span><span class="sxs-lookup"><span data-stu-id="6528a-112">Guidance specific to HoloLens 2 can be found [here](holographic-remoting-create-remote-wmr.md).</span></span>


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a><span data-ttu-id="6528a-113">Adicionar a comunicação remota do Holographic ao seu aplicativo da área de trabalho ou UWP</span><span class="sxs-lookup"><span data-stu-id="6528a-113">Add holographic remoting to your desktop or UWP app</span></span>

<span data-ttu-id="6528a-114">Esta página descreve como adicionar o Holographic Remoting a um aplicativo desktop ou UWP.</span><span class="sxs-lookup"><span data-stu-id="6528a-114">This page describes how to add Holographic Remoting to a desktop or UWP app.</span></span>

<span data-ttu-id="6528a-115">A comunicação remota do Holographic permite que seu aplicativo direcione um HoloLens com conteúdo Holographic hospedado em um computador desktop ou em um dispositivo UWP, como o Xbox One.</span><span class="sxs-lookup"><span data-stu-id="6528a-115">Holographic remoting lets your app target a HoloLens with holographic content hosted on a desktop PC or on a UWP device such as the Xbox One.</span></span> <span data-ttu-id="6528a-116">Você também tem acesso a mais recursos do sistema, possibilitando a integração de [exibições de imersão](../../design/app-views.md) remotas ao software de PC desktop existente.</span><span class="sxs-lookup"><span data-stu-id="6528a-116">You also have access to more system resources, making it possible to integrate remote [immersive views](../../design/app-views.md) into existing desktop PC software.</span></span> <span data-ttu-id="6528a-117">Um aplicativo host de comunicação remota recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição de imersão virtual e transmite quadros de conteúdo de volta para o HoloLens.</span><span class="sxs-lookup"><span data-stu-id="6528a-117">A remoting host app receives an input data stream from a HoloLens, renders content in a virtual immersive view, and streams content frames back to HoloLens.</span></span> <span data-ttu-id="6528a-118">A conexão é feita usando Wi-Fi padrão.</span><span class="sxs-lookup"><span data-stu-id="6528a-118">The connection is made using standard Wi-Fi.</span></span> <span data-ttu-id="6528a-119">Para usar a comunicação remota, use um pacote NuGet para adicionar a comunicação remota do Holographic ao seu aplicativo da área de trabalho ou UWP e, em seguida, escreva o código para lidar com a conexão e renderize uma exibição imersiva.</span><span class="sxs-lookup"><span data-stu-id="6528a-119">To use remoting, use a NuGet package to add holographic remoting to your desktop or UWP app, then write code to handle the connection and render an immersive view.</span></span> <span data-ttu-id="6528a-120">As bibliotecas auxiliares são incluídas no exemplo de código que simplificam a tarefa de lidar com a conexão do dispositivo.</span><span class="sxs-lookup"><span data-stu-id="6528a-120">Helper libraries are included in the code sample that simplify the task of handling the device connection.</span></span>

<span data-ttu-id="6528a-121">Uma conexão de comunicação remota típica terá um mínimo de 50 ms de latência.</span><span class="sxs-lookup"><span data-stu-id="6528a-121">A typical remoting connection will have as low as 50 ms of latency.</span></span> <span data-ttu-id="6528a-122">O aplicativo de player pode relatar a latência em tempo real.</span><span class="sxs-lookup"><span data-stu-id="6528a-122">The player app can report the latency in real time.</span></span>

>[!NOTE]
><span data-ttu-id="6528a-123">Os trechos de código neste artigo demonstram atualmente o uso de C++/CX em vez de c++/WinRT compatível com C + +17, conforme usado no [modelo de projeto do C++ Holographic](../native/creating-a-holographic-directx-project.md).</span><span class="sxs-lookup"><span data-stu-id="6528a-123">The code snippets in this article currently demonstrate use of C++/CX rather than C++17-compliant C++/WinRT as used in the [C++ holographic project template](../native/creating-a-holographic-directx-project.md).</span></span>  <span data-ttu-id="6528a-124">Os conceitos são equivalentes a um projeto/WinRT do C++, embora você precise converter o código.</span><span class="sxs-lookup"><span data-stu-id="6528a-124">The concepts are equivalent for a C++/WinRT project, though you'll need to translate the code.</span></span>

### <a name="get-the-remoting-nuget-packages"></a><span data-ttu-id="6528a-125">Obter os pacotes de NuGet de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="6528a-125">Get the remoting NuGet packages</span></span>

<span data-ttu-id="6528a-126">Siga estas etapas para obter o pacote NuGet para a comunicação remota do Holographic e adicione uma referência do seu projeto:</span><span class="sxs-lookup"><span data-stu-id="6528a-126">Follow these steps to get the NuGet package for holographic remoting, and add a reference from your project:</span></span>
1. <span data-ttu-id="6528a-127">Vá para seu projeto no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6528a-127">Go to your project in Visual Studio.</span></span>
2. <span data-ttu-id="6528a-128">Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**</span><span class="sxs-lookup"><span data-stu-id="6528a-128">Right-click on the project node and select **Manage NuGet Packages...**</span></span>
3. <span data-ttu-id="6528a-129">No painel que aparece, selecct **procurar** e, em seguida, pesquise "Holographic Remoting".</span><span class="sxs-lookup"><span data-stu-id="6528a-129">In the panel that appears, selecct **Browse** and then search for "Holographic Remoting".</span></span>
4. <span data-ttu-id="6528a-130">Selecione **Microsoft. Holographic. Remoting** e selecct **install**.</span><span class="sxs-lookup"><span data-stu-id="6528a-130">Select **Microsoft.Holographic.Remoting** and selecct **Install**.</span></span>
5. <span data-ttu-id="6528a-131">Se a caixa de diálogo **Visualizar** for exibida, selecione **OK**.</span><span class="sxs-lookup"><span data-stu-id="6528a-131">If the **Preview** dialog appears, select **OK**.</span></span>
6. <span data-ttu-id="6528a-132">Selecione **aceito quando o** diálogo do contrato de licença for exibido.</span><span class="sxs-lookup"><span data-stu-id="6528a-132">Select **I Accept** when the license agreement dialog appears.</span></span>

### <a name="create-the-holographicstreamerhelpers"></a><span data-ttu-id="6528a-133">Criar o HolographicStreamerHelpers</span><span class="sxs-lookup"><span data-stu-id="6528a-133">Create the HolographicStreamerHelpers</span></span>

<span data-ttu-id="6528a-134">Primeiro, precisamos adicionar uma instância de HolographicStreamerHelpers à classe que manipulará a comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="6528a-134">First, we need to add an instance of HolographicStreamerHelpers to the class that will handle remoting.</span></span>

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

<span data-ttu-id="6528a-135">Você também precisará acompanhar o estado da conexão.</span><span class="sxs-lookup"><span data-stu-id="6528a-135">You'll also need to track connection state.</span></span> <span data-ttu-id="6528a-136">Se você quiser renderizar a visualização, precisará ter uma textura para copiá-la para.</span><span class="sxs-lookup"><span data-stu-id="6528a-136">If you want to render the preview, you need to have a texture to copy it to.</span></span> <span data-ttu-id="6528a-137">Você também precisa de algumas coisas como um bloqueio de estado de conexão, alguma maneira de armazenar o endereço IP do HoloLens e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="6528a-137">You also need a few things like a connection state lock, some way of storing the IP address of HoloLens, and so on.</span></span>

```cpp
private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::SRWLock                   m_connectionStateLock;

       RemotingHostSample::AppView^                        m_appView;
       Platform::String^                                   m_ipAddress;
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;

       Microsoft::WRL::Wrappers::CriticalSection           m_deviceLock;
       Microsoft::WRL::ComPtr<IDXGISwapChain1>             m_swapChain;
       Microsoft::WRL::ComPtr<ID3D11Texture2D>             m_spTexture;
```

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a><span data-ttu-id="6528a-138">Inicializar o HolographicStreamerHelpers e conectar-se ao HoloLens</span><span class="sxs-lookup"><span data-stu-id="6528a-138">Initialize HolographicStreamerHelpers and connect to HoloLens</span></span>

<span data-ttu-id="6528a-139">Para se conectar a um dispositivo HoloLens, crie uma instância do HolographicStreamerHelpers e conecte-se ao endereço IP de destino.</span><span class="sxs-lookup"><span data-stu-id="6528a-139">To connect to a HoloLens device, create an instance of HolographicStreamerHelpers and connect to the target IP address.</span></span> <span data-ttu-id="6528a-140">Você precisará definir o tamanho do quadro de vídeo para corresponder à largura e altura de exibição do HoloLens, pois a biblioteca de comunicação remota Holographic espera que as resoluções do codificador e do decodificador correspondam exatamente.</span><span class="sxs-lookup"><span data-stu-id="6528a-140">You'll need to set the video frame size to match the HoloLens display width and height, because the Holographic Remoting library expects the encoder and decoder resolutions to match exactly.</span></span>

```cpp
m_streamerHelpers = ref new HolographicStreamerHelpers();
       m_streamerHelpers->CreateStreamer(m_d3dDevice);

       // We currently need to stream at 720p because that's the resolution of our remote display.
       // There is a check in the holographic streamer that makes sure the remote and local
       // resolutions match. The default streamer resolution is 1080p.
       m_streamerHelpers->SetVideoFrameSize(1280, 720);

       try
       {
           m_streamerHelpers->Connect(m_ipAddress->Data(), 8001);
       }
       catch (Platform::Exception^ ex)
       {
           DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
       }
```

<span data-ttu-id="6528a-141">A conexão do dispositivo é assíncrona.</span><span class="sxs-lookup"><span data-stu-id="6528a-141">The device connection is asynchronous.</span></span> <span data-ttu-id="6528a-142">Seu aplicativo precisa fornecer manipuladores de eventos para eventos de conexão, desconexão e quadros de envio.</span><span class="sxs-lookup"><span data-stu-id="6528a-142">Your app needs to provide event handlers for connect, disconnect, and frame send events.</span></span>

<span data-ttu-id="6528a-143">O evento onconnected pode atualizar a interface do usuário, iniciar a renderização e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="6528a-143">The OnConnected event can update the UI, start rendering, and so on.</span></span> <span data-ttu-id="6528a-144">Em nosso exemplo de código de área de trabalho, atualizamos o título da janela com uma mensagem "conectada".</span><span class="sxs-lookup"><span data-stu-id="6528a-144">In our desktop code sample, we update the window title with a "connected" message.</span></span>

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

<span data-ttu-id="6528a-145">O evento ondisconnectd pode lidar com a reconexão, as atualizações da interface do usuário e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="6528a-145">The OnDisconnected event can handle reconnection, UI updates, and so on.</span></span> <span data-ttu-id="6528a-146">Neste exemplo, reconectamos se houver uma falha transitória.</span><span class="sxs-lookup"><span data-stu-id="6528a-146">In this example, we reconnect if there's a transient failure.</span></span>

```cpp
Platform::WeakReference streamerHelpersWeakRef = Platform::WeakReference(m_streamerHelpers);
       m_streamerHelpers->OnDisconnected += ref new DisconnectedEvent(
           [this, streamerHelpersWeakRef](_In_ HolographicStreamerConnectionFailureReason failureReason)
           {
               DebugLog(L"Disconnected with reason %d", failureReason);
               UpdateWindowTitle();

               // Reconnect if this is a transient failure.
               if (failureReason == HolographicStreamerConnectionFailureReason::Unreachable ||
                   failureReason == HolographicStreamerConnectionFailureReason::ConnectionLost)
               {
                   DebugLog(L"Reconnecting...");

                   try
                   {
                       auto helpersResolved = streamerHelpersWeakRef.Resolve<HolographicStreamerHelpers>();
                       if (helpersResolved)
                       {
                           helpersResolved->Connect(m_ipAddress->Data(), 8001);
                       }
                       else
                       {
                           DebugLog(L"Failed to reconnect because a disconnect has already occurred.\n");
                       }
                   }
                   catch (Platform::Exception^ ex)
                   {
                       DebugLog(L"Connect failed with hr = 0x%08X", ex->HResult);
                   }
               }
               else
               {
                   DebugLog(L"Disconnected with unrecoverable error, not attempting to reconnect.");
               }
           });
```

<span data-ttu-id="6528a-147">Quando o componente de comunicação remota está pronto para enviar um quadro, seu aplicativo recebe uma oportunidade de fazer uma cópia dele no SendFrameEvent.</span><span class="sxs-lookup"><span data-stu-id="6528a-147">When the remoting component is ready to send a frame, your app is provided an opportunity to make a copy of it in the SendFrameEvent.</span></span> <span data-ttu-id="6528a-148">Aqui, copiamos o quadro em uma cadeia de permuta para que possamos exibi-lo em uma janela de visualização.</span><span class="sxs-lookup"><span data-stu-id="6528a-148">Here, we copy the frame to a swap chain so that we can display it in a preview window.</span></span>

```cpp
m_streamerHelpers->OnSendFrame += ref new SendFrameEvent(
           [this](_In_ const ComPtr<ID3D11Texture2D>& spTexture, _In_ FrameMetadata metadata)
           {
               if (m_showPreview)
               {
                   ComPtr<ID3D11Device1> spDevice = m_appView->GetDeviceResources()->GetD3DDevice();
                   ComPtr<ID3D11DeviceContext> spContext = m_appView->GetDeviceResources()->GetD3DDeviceContext();

                   ComPtr<ID3D11Texture2D> spBackBuffer;
                   ThrowIfFailed(m_swapChain->GetBuffer(0, IID_PPV_ARGS(&spBackBuffer)));

                   spContext->CopySubresourceRegion(
                       spBackBuffer.Get(), // dest
                       0,                  // dest subresource
                       0, 0, 0,            // dest x, y, z
                       spTexture.Get(),    // source
                       0,                  // source subresource
                       nullptr);           // source box, null means the entire resource

                   DXGI_PRESENT_PARAMETERS parameters = { 0 };
                   ThrowIfFailed(m_swapChain->Present1(1, 0, &parameters));
               }
           });
```

### <a name="render-holographic-content"></a><span data-ttu-id="6528a-149">Renderizar conteúdo Holographic</span><span class="sxs-lookup"><span data-stu-id="6528a-149">Render holographic content</span></span>

<span data-ttu-id="6528a-150">Para renderizar o conteúdo usando comunicação remota, você configura um IFrameworkView virtual em seu aplicativo de área de trabalho ou UWP e processa os quadros Holographic da comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="6528a-150">To render content using remoting, you set up a virtual IFrameworkView within your desktop or UWP app and process holographic frames from remoting.</span></span> <span data-ttu-id="6528a-151">Todas as APIs Holographic do Windows são usadas da mesma forma por essa exibição, mas elas são configuradas de forma ligeiramente diferente.</span><span class="sxs-lookup"><span data-stu-id="6528a-151">All of the Windows Holographic APIs are used the same way by this view, but it's set up slightly differently.</span></span>

<span data-ttu-id="6528a-152">Em vez de criá-los por conta própria, os componentes de espaço e fala do Holographic vêm de sua classe HolographicRemotingHelpers:</span><span class="sxs-lookup"><span data-stu-id="6528a-152">Instead of creating them yourself, the holographic space and speech components come from your HolographicRemotingHelpers class:</span></span>

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

<span data-ttu-id="6528a-153">Em vez de usar um loop de atualização em um método Run, você fornece atualizações em escala do loop principal de seu aplicativo de desktop ou UWP.</span><span class="sxs-lookup"><span data-stu-id="6528a-153">Instead of using an update loop in a Run method, you provide tick updates from the main loop of your desktop or UWP app.</span></span> <span data-ttu-id="6528a-154">Isso permite que seu aplicativo da área de trabalho ou UWP permaneça no controle do processamento de mensagens.</span><span class="sxs-lookup"><span data-stu-id="6528a-154">This allows your desktop or UWP app to remain in control of message processing.</span></span>

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

<span data-ttu-id="6528a-155">O método Tick () da exibição do aplicativo Holographic conclui uma iteração do loop Update, Draw e Present.</span><span class="sxs-lookup"><span data-stu-id="6528a-155">The holographic app view's Tick() method completes one iteration of the update, draw, present loop.</span></span>

```cpp
void AppView::Tick()
   {
       if (m_main)
       {
           // When running on Windows Holographic, we can use the holographic rendering system.
           HolographicFrame^ holographicFrame = m_main->Update();

           if (holographicFrame && m_main->Render(holographicFrame))
           {
               // The holographic frame has an API that presents the swap chain for each
               // holographic camera.
               m_deviceResources->Present(holographicFrame);
           }
       }
   }
```

<span data-ttu-id="6528a-156">A exibição de aplicativo Holographic de atualização, processamento e loop presente são exatamente iguais às que se encontram durante a execução no HoloLens, exceto pelo fato de que você tem acesso a uma quantidade muito maior de recursos do sistema no computador desktop.</span><span class="sxs-lookup"><span data-stu-id="6528a-156">The holographic app view update, render, and present loop are exactly the same as it is when running on HoloLens - except that you have access to a much greater amount of system resources on your desktop PC.</span></span> <span data-ttu-id="6528a-157">Você pode renderizar muitos triângulos, ter mais passagens de desenho, realizar mais física e usar processos x64 para carregar o conteúdo que exige mais de 2 GB de RAM.</span><span class="sxs-lookup"><span data-stu-id="6528a-157">You can render many more triangles, have more drawing passes, do more physics, and use x64 processes to load content that requires more than 2 GB of RAM.</span></span>

### <a name="disconnect-and-end-the-remote-session"></a><span data-ttu-id="6528a-158">Desconectar e encerrar a sessão remota</span><span class="sxs-lookup"><span data-stu-id="6528a-158">Disconnect and end the remote session</span></span>

<span data-ttu-id="6528a-159">Para desconectar-por exemplo, quando o usuário clica em um botão da interface do usuário para desconectar-chamada Disconnect () no HolographicStreamerHelpers e, em seguida, libera o objeto.</span><span class="sxs-lookup"><span data-stu-id="6528a-159">To disconnect - for example, when the user clicks a UI button to disconnect - call Disconnect() on the HolographicStreamerHelpers, and then release the object.</span></span>

```cpp
void DesktopWindow::DisconnectFromRemoteDevice()
   {
       // Disconnecting from the remote device can change the connection state.
       auto exclusiveLock = m_connectionStateLock.LockExclusive();

       if (m_streamerHelpers != nullptr)
       {
           m_streamerHelpers->Disconnect();

           // Reset state
           m_streamerHelpers = nullptr;
       }
   }
```

## <a name="get-the-remoting-player"></a><span data-ttu-id="6528a-160">Obter o reprodutor de comunicação remota</span><span class="sxs-lookup"><span data-stu-id="6528a-160">Get the remoting player</span></span>

<span data-ttu-id="6528a-161">O player de comunicação remota do Windows Holographic é oferecido na loja de aplicativos do Windows como um ponto de extremidade para aplicativos de host remotos se conectarem ao.</span><span class="sxs-lookup"><span data-stu-id="6528a-161">The Windows Holographic remoting player is offered in the Windows app store as an endpoint for remoting host apps to connect to.</span></span> <span data-ttu-id="6528a-162">Para obter o Windows Holographic Remoting Player, visite a Windows App Store do seu HoloLens, pesquise por comunicação remota e baixe o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6528a-162">To get the Windows Holographic remoting player, visit the Windows app store from your HoloLens, search for Remoting, and download the app.</span></span> <span data-ttu-id="6528a-163">O player de comunicação remota inclui um recurso para exibir estatísticas na tela, o que pode ser útil ao depurar aplicativos de host de comunicação remota.</span><span class="sxs-lookup"><span data-stu-id="6528a-163">The remoting player includes a feature to display statistics on-screen, which can be useful when debugging remoting host apps.</span></span>

## <a name="notes-and-resources"></a><span data-ttu-id="6528a-164">Notas e recursos</span><span class="sxs-lookup"><span data-stu-id="6528a-164">Notes and resources</span></span>

<span data-ttu-id="6528a-165">A exibição do aplicativo Holographic precisará de uma maneira de fornecer seu aplicativo com o dispositivo Direct3D, que deve ser usado para inicializar o espaço do Holographic.</span><span class="sxs-lookup"><span data-stu-id="6528a-165">The holographic app view will need a way to provide your app with the Direct3D device, which must be used to initialize the holographic space.</span></span> <span data-ttu-id="6528a-166">Seu aplicativo deve usar este dispositivo Direct3D para copiar e exibir o quadro de visualização.</span><span class="sxs-lookup"><span data-stu-id="6528a-166">Your app should use this Direct3D device to copy and display the preview frame.</span></span>

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

<span data-ttu-id="6528a-167">**Exemplo de código:** Um [exemplo de código remoto Holographic](https://github.com/Microsoft/HoloLensCompanionKit) completo está disponível, que inclui uma exibição de aplicativo Holographic compatível com projetos de host remoto e de comunicação remota para desktop Win32, UWP DirectX e UWP com XAML.</span><span class="sxs-lookup"><span data-stu-id="6528a-167">**Code sample:** A complete [Holographic Remoting code sample](https://github.com/Microsoft/HoloLensCompanionKit) is available, which includes a holographic application view that is compatible with remoting and remoting host projects for desktop Win32, UWP DirectX, and UWP with XAML.</span></span> 

<span data-ttu-id="6528a-168">**Observação de depuração:** A biblioteca de comunicação remota do Holographic pode gerar exceções de primeira chance.</span><span class="sxs-lookup"><span data-stu-id="6528a-168">**Debugging note:** The Holographic Remoting library can throw first-chance exceptions.</span></span> <span data-ttu-id="6528a-169">Essas exceções podem ser visíveis em sessões de depuração, dependendo das configurações de exceção do Visual Studio que estão ativas no momento.</span><span class="sxs-lookup"><span data-stu-id="6528a-169">These exceptions may be visible in debugging sessions, depending on the Visual Studio exception settings that are active at the time.</span></span> <span data-ttu-id="6528a-170">Essas exceções são detectadas internamente pela biblioteca de comunicação remota do Holographic e podem ser ignoradas.</span><span class="sxs-lookup"><span data-stu-id="6528a-170">These exceptions are caught internally by the Holographic Remoting library and can be ignored.</span></span>
