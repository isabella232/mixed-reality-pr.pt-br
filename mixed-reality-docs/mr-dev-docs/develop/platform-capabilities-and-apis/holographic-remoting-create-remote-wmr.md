---
title: Escrevendo um aplicativo remoto de comunicação remota do Holographic (WMR)
description: Saiba como transmitir conteúdo remoto renderizado em um computador remoto para o HoloLens 2 com aplicativos de comunicação remota Holographic com HolographicSpace.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, comunicação remota Holographic, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, NuGet
ms.openlocfilehash: 65c76266c00f51cbe17f6bfd2991a6adf4103855
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583851"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>Escrevendo um aplicativo remoto de comunicação remota do Holographic usando a API do HolographicSpace

>[!IMPORTANT]
>Este documento descreve a criação de um aplicativo remoto para o HoloLens 2 usando a [API HolographicSpace](../native/getting-a-holographicspace.md). Os aplicativos remotos para o **HoloLens (1º gen)** devem usar o pacote NuGet versão **1. x**. x. Isso significa que os aplicativos remotos escritos para o HoloLens 2 não são compatíveis com o HoloLens 1 e vice-versa. A documentação do HoloLens 1 pode ser encontrada [aqui](add-holographic-remoting.md).

Os aplicativos de comunicação remota Holographic podem transmitir conteúdo renderizado remotamente para o HoloLens 2 e os headsets de imersão de realidade mista do Windows. Você também pode acessar mais recursos do sistema e integrar [exibições de imersão](../../design/app-views.md) remotas ao software de PC desktop existente. Um aplicativo remoto recebe um fluxo de dados de entrada do HoloLens 2, renderiza o conteúdo em uma exibição de imersão virtual e transmite os quadros de conteúdo de volta para o HoloLens 2. A conexão é feita usando Wi-Fi padrão. A comunicação remota do Holographic é adicionada a um aplicativo de desktop ou UWP por meio de um pacote NuGet. É necessário um código adicional que manipula a conexão e é renderizado em uma exibição de imersão. Uma conexão de comunicação remota típica terá um mínimo de 50 ms de latência. O aplicativo de player pode relatar a latência em tempo real.

Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="prerequisites"></a>Pré-requisitos

Um bom ponto de partida é um aplicativo de área de trabalho baseado em DirectX em funcionamento ou UWP, que tem como alvo a [API HolographicSpace](../native/getting-a-holographicspace.md). Para obter detalhes, consulte [visão geral do desenvolvimento do DirectX](../native/directx-development-overview.md). O [modelo de projeto C++ Holographic](../native/creating-a-holographic-directx-project.md) é um bom ponto de partida.

>[!IMPORTANT]
>Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](//windows/win32/com/multithreaded-apartments)multi-threaded. O uso de um [apartamento de thread único](//windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução. Ao usar C++/WinRT [WinRT:: init_apartment](//windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.



## <a name="get-the-holographic-remoting-nuget-package"></a>Obter o pacote NuGet de comunicação remota do Holographic

As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.
1. Abra o projeto no Visual Studio.
2. Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**
3. No painel que aparece, selecione **procurar** e, em seguida, pesquise "comunicação remota do Holographic".
4. Selecione **Microsoft. Holographic. Remoting**, certifique-se de selecionar a versão **2. x. x** mais recente e selecione **instalar**.
5. Se a caixa de diálogo **Visualizar** for exibida, selecione **OK**.
6. Selecione **aceito** quando a caixa de diálogo do contrato de licença for exibida.

>[!NOTE]
>A versão **1. x. x** do pacote NuGet ainda está disponível para desenvolvedores que desejam direcionar para o HoloLens 1. Para obter detalhes, consulte [Add Holographic Remoting (HoloLens (1º gen))](add-holographic-remoting.md).

## <a name="create-the-remote-context"></a>Criar o contexto remoto

Como primeira etapa, o aplicativo deve criar um contexto remoto.

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
>O Holographic Remoting funciona substituindo o tempo de execução do Windows Mixed Reality que faz parte do Windows com um tempo de execução específico de comunicação remota. Isso é feito durante a criação do contexto remoto. Por esse motivo, qualquer chamada em qualquer API de realidade mista do Windows antes de criar o contexto remoto pode resultar em um comportamento inesperado. A abordagem recomendada é criar o contexto remoto o mais cedo possível antes da interação com qualquer API de realidade misturada. Nunca misture objetos criados ou recuperados por meio de qualquer API de realidade mista do Windows antes da chamada para CreateRemoteContext com objetos criados ou recuperados posteriormente.

Em seguida, o espaço Holographic precisa ser criado. Não é necessário especificar um CoreWindow. Os aplicativos da área de trabalho que não têm um CoreWindow podem apenas passar um ```nullptr``` .

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Conectar-se ao dispositivo

Quando o aplicativo remoto estiver pronto para renderizar o conteúdo, pode ser estabelecida uma conexão com o dispositivo do Player.

A conexão pode ser feita de duas maneiras.
1) O aplicativo remoto se conecta ao Player em execução no dispositivo.
2) O Player em execução no dispositivo se conecta ao aplicativo remoto.

Para estabelecer uma conexão do aplicativo remoto com o dispositivo do Player, chame o ```Connect``` método no contexto remoto especificando o nome do host e a porta. A porta usada pelo Holographic Remoting Player é **8265**.

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
>Assim como acontece com qualquer API do C++/WinRT, você ```Connect``` pode lançar um WinRT:: hresult_error que precisa ser manipulado.

>[!TIP]
>Para evitar o uso da projeção de linguagem [C++/WinRT](//windows/uwp/cpp-and-winrt-apis/) , o arquivo ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` localizado no pacote NuGet de comunicação remota do Holographic pode ser incluído. Ele contém declarações das interfaces COM subjacentes. No entanto, o uso de C++/WinRT é recomendado.

A escuta de conexões de entrada no aplicativo remoto pode ser feita chamando o ```Listen``` método. A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada. A porta de handshake é usada para o handshake inicial. Os dados são enviados pela porta de transporte. Por padrão, **8265** e **8266** são usados.

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
>O ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` dentro do pacote NuGet contém documentação detalhada para a API exposta pela comunicação remota do Holographic.

## <a name="handling-remoting-specific-events"></a>Manipulando eventos específicos de comunicação remota

O contexto remoto expõe três eventos, que são importantes para monitorar o estado de uma conexão.
1) Onconnected: disparado quando uma conexão com o dispositivo tiver sido estabelecida com êxito.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnect: disparado se uma conexão estabelecida estiver fechada ou não foi possível estabelecer uma conexão.
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
3) Desescutando: quando a escuta de conexões de entrada é iniciada.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Além disso, o estado da conexão pode ser consultado usando a ```ConnectionState``` propriedade no contexto remoto.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Manipulando eventos de fala

Usando a interface de fala remota, é possível registrar gatilhos de fala com o HoloLens 2 e tê-los remotos no aplicativo remoto.

Esse membro adicional é necessário para acompanhar o estado da fala remota.

```cpp
winrt::Microsoft::Holographic::AppRemoting::IRemoteSpeech::OnRecognizedSpeech_revoker m_onRecognizedSpeechRevoker;

```

Primeiro, a interface de fala remota precisa ser recuperada.

```cpp
if (auto remoteSpeech = m_remoteContext.GetRemoteSpeech())
{
    InitializeSpeechAsync(remoteSpeech, m_onRecognizedSpeechRevoker, weak_from_this());
}
```

Usando um método auxiliar assíncrono, você pode inicializar a fala remota. Isso deve ser feito de forma assíncrona, pois a inicialização pode levar um tempo considerável. [Operações de simultaneidade e assíncronas com c++/WinRT](//windows/uwp/cpp-and-winrt-apis/concurrency) explica como criar funções assíncronas com c++/WinRT.

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

Há duas maneiras de especificar frases a serem reconhecidas.
1) Especificação dentro de um arquivo XML de gramática de fala. Consulte [como criar uma gramática XML básica](//previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) para obter detalhes.
2) Especifique ao passá-los dentro do vetor do dicionário para ```ApplyParameters``` .

Dentro do retorno de chamada OnRecognizedSpeech, os eventos de fala podem ser processados:

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

## <a name="preview-streamed-content-locally"></a>Visualizar conteúdo transmitido localmente

Para exibir o mesmo conteúdo no aplicativo remoto que é enviado para o dispositivo, o ```OnSendFrame``` evento do contexto remoto pode ser usado. O ```OnSendFrame``` evento é disparado toda vez que a biblioteca de comunicação remota do Holographic envia o quadro atual para o dispositivo remoto. Esse é o momento ideal para pegar o conteúdo e também blit-lo na janela Desktop ou UWP.

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

## <a name="depth-reprojection"></a>Reprojeção de profundidade

A partir da versão [2.1.0](holographic-remoting-version-history.md#v2.1.0), a comunicação remota Holographic dá suporte à [Reprojeção de profundidade](hologram-stability.md#reprojection). Isso exige que o buffer de cores e o buffer de profundidade sejam transmitidos do aplicativo remoto para o HoloLens 2. Por padrão, o streaming de buffer de profundidade é habilitado e configurado para usar metade da resolução do buffer de cores. Isso pode ser alterado da seguinte maneira:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Observe que, se os valores padrão não devem ser usados, ```ConfigureDepthVideoStream``` deve ser chamado antes de estabelecer uma conexão com o HoloLens 2. O melhor local é logo após a criação do contexto remoto. Os valores possíveis para DepthBufferStreamResolution são:

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Disabled (adicionado com a versão [2.1.3](holographic-remoting-version-history.md#v2.1.3) e, se usado, nenhum fluxo de vídeo de profundidade adicional é criado)

Tenha em mente que o uso de um buffer de profundidade de resolução completa também afeta os requisitos de largura de banda e precisa ser considerado no valor máximo de largura de banda fornecido para o ```CreateRemoteContext``` .

Ao lado de configurar a resolução, você também precisa confirmar um buffer de profundidade por meio de [HolographicCameraRenderingParameters. CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).

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

Para verificar se a Reprojeção de profundidade está trabalhando corretamente no HoloLens 2, você pode habilitar um visualizador de profundidade por meio do portal do dispositivo. Consulte [verificação de profundidade está definido corretamente](hologram-stability.md#verifying-depth-is-set-correctly) para obter detalhes.

## <a name="optional-custom-data-channels"></a>Opcional: canais de dados personalizados

Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida. Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.

## <a name="see-also"></a>Consulte Também
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Canais de dados personalizados de comunicação remota holográfica](holographic-remoting-custom-data-channels.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)