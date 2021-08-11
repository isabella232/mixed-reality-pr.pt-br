---
title: Adicionar a remoção holográfica
description: Saiba como instalar, configurar e usar a Comunicação Remográfica Holográfica para renderizar hologramas em um HoloLens dispositivo pela rede.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: Windows Mixed Reality, hologramas, comunicação remota holográfica, renderização remota, renderização de rede, HoloLens, hologramas remotos, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual
ms.openlocfilehash: ecfc49477e202b08303160e54ce986577a9d79eb387dc1edb1bc33c63644615f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115198852"
---
# <a name="add-holographic-remoting-hololens-first-gen"></a>Adicionar a remoção holográfica (HoloLens (primeira geração))

>[!IMPORTANT]
> Este documento descreve a criação de um aplicativo host para HoloLens 1. O aplicativo host **para HoloLens (1ª geração)** deve usar NuGet versão do pacote **1.x.x**. Isso implica que os aplicativos host escritos para HoloLens 1 não são compatíveis com HoloLens 2 e vice-versa.

## <a name="hololens-2"></a>HoloLens 2

HoloLens desenvolvedores que usam a Holographic Remoting precisarão atualizar seus aplicativos para torná-los compatíveis com HoloLens 2. Isso requer uma nova versão do pacote de NuGet Holographic Remoting. Certifique-se de usar a versão 2.0.0.0 ou superior do pacote do holographic remoting NuGet ao se conectar ao Holographic Remoting Player no HoloLens 2 ou a conexão falhará.

>[!NOTE]
> Diretrizes específicas HoloLens 2 podem ser encontradas [aqui.](holographic-remoting-create-remote-wmr.md)


## <a name="add-holographic-remoting-to-your-desktop-or-uwp-app"></a>Adicionar a remota holográfica ao aplicativo UWP ou área de trabalho

Esta página descreve como adicionar o Holographic Remoting a um aplicativo UWP ou desktop.

A remota holográfica permite que seu aplicativo seja destinado a um HoloLens com conteúdo holográfico hospedado em um computador desktop ou em um dispositivo UWP, como o Xbox One. Você também tem acesso a mais recursos do sistema, possibilitando a integração de exibições [imersivas remotas](../../design/app-views.md) ao software de computador desktop existente. Um aplicativo host de remoção recebe um fluxo de dados de entrada de um HoloLens, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo de volta para HoloLens. A conexão é feita usando o Wi-Fi padrão. Para usar a remotaização, use um pacote NuGet para adicionar a remotação holográfica à área de trabalho ou ao aplicativo UWP e, em seguida, escreva código para lidar com a conexão e renderizar uma exibição imersiva. As bibliotecas auxiliares são incluídas no exemplo de código que simplifica a tarefa de lidar com a conexão do dispositivo.

Uma conexão de remoting típica terá até 50 ms de latência. O aplicativo player pode relatar a latência em tempo real.

>[!NOTE]
>Atualmente, os snippets de código neste artigo demonstram o uso do C++/CX em vez do C++17 compatível com C++/WinRT, conforme usado no modelo de projeto [holográfico C++.](../native/creating-a-holographic-directx-project.md)  Os conceitos são equivalentes para um projeto C++/WinRT, embora você precise traduzir o código.

### <a name="get-the-remoting-nuget-packages"></a>Obter os pacotes de NuGet remoções

Siga estas etapas para obter o pacote NuGet para a remoção holográfica e adicionar uma referência de seu projeto:
1. Acesse seu projeto em Visual Studio.
2. Clique com o botão direito do mouse no nó do projeto e **selecione Gerenciar NuGet Pacotes...**
3. No painel exibido, **seleccione** Procurar e pesquise "Holographic Remoting".
4. Selecione **Microsoft.Holographic.Remoting** e selecione **Instalar**.
5. Se a **caixa de** diálogo Visualização for exibida, selecione **OK.**
6. Selecione **Aceito quando a** caixa de diálogo do contrato de licença for exibida.

### <a name="create-the-holographicstreamerhelpers"></a>Criar o HolographicStreamerHelpers

Primeiro, precisamos adicionar uma instância de HolographicStreamerHelpers à classe que manipulará a remoção.

```cpp
#include <HolographicStreamerHelpers.h>

   private:
       Microsoft::Holographic::HolographicStreamerHelpers^ m_streamerHelpers;
```

Você também precisará acompanhar o estado da conexão. Se você quiser renderizar a versão prévia, precisará ter uma textura para a cópia. Você também precisa de algumas coisas como um bloqueio de estado de conexão, alguma maneira de armazenar o endereço IP de HoloLens e assim por diante.

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

### <a name="initialize-holographicstreamerhelpers-and-connect-to-hololens"></a>Inicialize HolographicStreamerHelpers e conecte-se ao HoloLens

Para se conectar a um HoloLens, crie uma instância de HolographicStreamerHelpers e conecte-se ao endereço IP de destino. Você precisará definir o tamanho do quadro de vídeo para corresponder à largura e à altura HoloLens exibição, pois a biblioteca de remoção holográfica espera que as resoluções do codificador e do decodificador corresponderem exatamente.

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

A conexão do dispositivo é assíncrona. Seu aplicativo precisa fornecer manipuladores de eventos para conectar, desconectar e enquadrar eventos de envio.

O evento OnConnected pode atualizar a interface do usuário, iniciar a renderização e assim por diante. Em nosso exemplo de código da área de trabalho, atualizamos o título da janela com uma mensagem "conectada".

```cpp
m_streamerHelpers->OnConnected += ref new ConnectedEvent(
           [this]()
           {
               UpdateWindowTitle();
           });
```

O evento OnDisconnected pode lidar com a reconexão, as atualizações da interface do usuário e assim por diante. Neste exemplo, nos reconectamos se houver uma falha transitória.

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

Quando o componente de remoting está pronto para enviar um quadro, seu aplicativo tem a oportunidade de fazer uma cópia dele no SendFrameEvent. Aqui, copiamos o quadro para uma cadeia de permuta para que possamos exibi-lo em uma janela de visualização.

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

### <a name="render-holographic-content"></a>Renderizar conteúdo holográfico

Para renderizar conteúdo usando a remotaização, você configura um IFrameworkView virtual em sua área de trabalho ou aplicativo UWP e processa quadros holográficos da remota. Todas as Windows APIs holográficas são usadas da mesma maneira por essa exibição, mas ela é configurada de forma ligeiramente diferente.

Em vez de criar você mesmo, o espaço holográfico e os componentes de fala vêm da classe HolographicRemotingHelpers:

```cpp
m_appView->Initialize(m_streamerHelpers->HolographicSpace, m_streamerHelpers->RemoteSpeech);
```

Em vez de usar um loop de atualização em um método Run, você fornece atualizações de escala do loop principal do aplicativo UWP ou da área de trabalho. Isso permite que sua área de trabalho ou aplicativo UWP permaneça no controle do processamento de mensagens.

```cpp
void DesktopWindow::Tick()
   {
       auto lock = m_deviceLock.Lock();
       m_appView->Tick();

       // display preview, etc.
   }
```

O método Tick() da exibição de aplicativo holográfico conclui uma iteração do loop update, draw, present.

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

O loop de atualização, renderização e atualização da exibição de aplicativo holográfico é exatamente o mesmo que é quando executado no HoloLens , exceto pelo fato de que você tem acesso a uma quantidade muito maior de recursos do sistema em seu computador desktop. Você pode renderizar muito mais triângulos, ter mais passagens de desenho, fazer mais física e usar processos x64 para carregar conteúdo que exige mais de 2 GB de RAM.

### <a name="disconnect-and-end-the-remote-session"></a>Desconectar e encerrar a sessão remota

Para desconectar – por exemplo, quando o usuário clica em um botão de interface do usuário para desconectar – chame Disconnect() no HolographicStreamerHelpers e, em seguida, libere o objeto.

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

## <a name="get-the-remoting-player"></a>Obter o player de remoção

O Windows player de remoção holográfico é oferecido na Windows de aplicativos como um ponto de extremidade para a conexão de aplicativos host de remoção. Para obter o Windows de remoção holográfica, visite a Windows de aplicativos do seu HoloLens, pesquise Por Remoting e baixe o aplicativo. O player de remoção inclui um recurso para exibir estatísticas na tela, o que pode ser útil ao depurar aplicativos host de transmissão.

## <a name="notes-and-resources"></a>Observações e recursos

A exibição de aplicativo holográfico precisará de uma maneira de fornecer ao aplicativo o dispositivo Direct3D, que deve ser usado para inicializar o espaço holográfico. Seu aplicativo deve usar esse dispositivo Direct3D para copiar e exibir o quadro de visualização.

```cpp
internal:
       const std::shared_ptr<DX::DeviceResources>& GetDeviceResources()
       {
           return m_deviceResources;
       }
```

**Exemplo de código:** Um exemplo [de](https://github.com/Microsoft/HoloLensCompanionKit) código de Comunicação Remota Holográfica completo está disponível, que inclui uma exibição de aplicativo holográfico compatível com projetos de host de comunicação remota e comunicação remota para a área de trabalho Win32, UWP DirectX e UWP com XAML. 

**Observação de depuração:** A biblioteca de remoção holográfica pode lançar exceções de primeira chance. Essas exceções podem ser visíveis nas sessões de depuração, dependendo das configurações Visual Studio de exceção que estão ativas no momento. Essas exceções são capturadas internamente pela biblioteca de Comunicação Remográfica Holográfica e podem ser ignoradas.
