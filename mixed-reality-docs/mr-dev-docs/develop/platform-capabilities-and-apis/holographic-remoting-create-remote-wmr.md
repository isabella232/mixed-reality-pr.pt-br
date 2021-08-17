---
title: Escrevendo um WMR (aplicativo remoto de remoção holográfica)
description: Saiba como transmitir conteúdo remoto renderizado em um computador remoto para HoloLens 2 com aplicativos holográficos de remoting com HolographicSpace.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, NuGet
ms.openlocfilehash: 0c5943ff92ce797e39ec0d2d98c129fa91eb3f14
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184717"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-holographicspace-api"></a>Escrevendo um aplicativo remoto de remoção holográfica usando a API do HolographicSpace

>[!IMPORTANT]
>Este documento descreve a criação de um aplicativo remoto para o HoloLens 2 usando a [API do HolographicSpace.](../native/getting-a-holographicspace.md) Aplicativos **remotos para HoloLens (1ª geração)** devem usar NuGet versão **1.x.x do pacote.** Isso implica que aplicativos remotos escritos para HoloLens 2 não são compatíveis com HoloLens 1 e vice-versa. A documentação HoloLens 1 pode ser encontrada [aqui.](add-holographic-remoting.md)

Os aplicativos de remotação holográfica podem transmitir conteúdo renderizado remotamente para HoloLens 2 e Windows Mixed Reality headsets imersivos. Você também pode acessar mais recursos do sistema e integrar exibições [imersivas remotas](../../design/app-views.md) ao software de computador desktop existente. Um aplicativo remoto recebe um fluxo de dados de entrada do HoloLens 2, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo de volta para HoloLens 2. A conexão é feita usando o Wi-Fi padrão. A remota holográfica é adicionada a um aplicativo de área de trabalho ou UWP por meio de um NuGet pacote. É necessário um código adicional que trata a conexão e renderiza em uma exibição imersiva. Uma conexão de remoting típica terá até 50 ms de latência. O aplicativo player pode relatar a latência em tempo real.

Todo o código nesta página e projetos de trabalho podem ser encontrados no repositório [GitHub](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)de exemplos de Remo holográfica .

## <a name="prerequisites"></a>Pré-requisitos

Um bom ponto de partida é um aplicativo UWP ou área de trabalho baseado em DirectX que tem como alvo a [API do HolographicSpace.](../native/getting-a-holographicspace.md) Para obter detalhes, consulte [Visão geral do desenvolvimento do DirectX.](../native/directx-development-overview.md) O [modelo de projeto holográfico C++](../native/creating-a-holographic-directx-project.md) é um bom ponto de partida.

>[!IMPORTANT]
>Qualquer aplicativo que use a Holographic Remoting deve ser autor para usar um [apartment multi-threaded.](/windows/win32/com/multithreaded-apartments) Há suporte para o uso de um apartment [de thread](/windows/win32/com/single-threaded-apartments) único, mas levará ao desempenho abaixo do ideal e possivelmente à gagueja durante a reprodução. Ao usar C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) um apartment multi-threaded é o padrão.



## <a name="get-the-holographic-remoting-nuget-package"></a>Obter o pacote de NuGet de NuGet Holographic

As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.
1. Abra o projeto no Visual Studio.
2. Clique com o botão direito do mouse no nó do projeto **e selecione Gerenciar NuGet Pacotes...**
3. No painel exibido, selecione **Procurar** e, em seguida, pesquise "Holographic Remoting".
4. Selecione **Microsoft.Holographic.Remoting**, escolha a versão **2.x.x** mais recente e **selecione Instalar**.
5. Se a **caixa de** diálogo Visualização for exibida, selecione **OK.**
6. Selecione **Aceito quando** a caixa de diálogo do contrato de licença for exibida.

>[!NOTE]
>A **versão 1.x.x** do pacote NuGet ainda está disponível para desenvolvedores que querem direcionar HoloLens 1. Para obter [detalhes, consulte Adicionar a HoloLens holográfica (1ª geração))](add-holographic-remoting.md).

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
>A remoção holográfica funciona substituindo o runtime Windows Mixed Reality que faz parte do Windows por um runtime específico de remoção. Isso é feito durante a criação do contexto remoto. Por esse motivo, qualquer chamada em qualquer API Windows Mixed Reality antes de criar o contexto remoto pode resultar em um comportamento inesperado. A abordagem recomendada é criar o contexto remoto o mais cedo possível antes da interação com qualquer API de Realidade Misturada. Nunca misture objetos criados ou recuperados por meio de qualquer API Windows Mixed Reality antes da chamada para CreateRemoteContext com objetos criados ou recuperados posteriormente.

Em seguida, o espaço holográfico precisa ser criado. Não é necessário especificar um CoreWindow. Aplicativos da área de trabalho que não têm um CoreWindow podem passar apenas um ```nullptr``` .

```cpp
m_holographicSpace = winrt::Windows::Graphics::Holographic::HolographicSpace::CreateForCoreWindow(nullptr);
```

## <a name="connect-to-the-device"></a>Conexão para o dispositivo

Quando o aplicativo remoto estiver pronto para renderizar o conteúdo, uma conexão com o dispositivo player poderá ser estabelecida.

A conexão pode ser feita de duas maneiras.
1) O aplicativo remoto se conecta ao player em execução no dispositivo.
2) O player em execução no dispositivo se conecta ao aplicativo remoto.

Para estabelecer uma conexão do aplicativo remoto com o dispositivo player, chame o método no contexto ```Connect``` remoto especificando o nome do host e a porta. A porta usada pelo Holographic Remoting Player é **8265.**

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
>Assim como com qualquer API do C++/WinRT pode lançar um ```Connect``` winrt::hresult_error que precisa ser tratado.

>[!TIP]
>Para evitar o uso da projeção de linguagem [C++/WinRT,](/windows/uwp/cpp-and-winrt-apis/) o arquivo localizado dentro do pacote ```build\native\include\<windows sdk version>\abi\Microsoft.Holographic.AppRemoting.h``` holográfico NuGet remoção pode ser incluído. Ele contém declarações das interfaces COM subjacentes. No entanto, recomendamos o uso de C++/WinRT.

A escuta de conexões de entrada no aplicativo remoto pode ser feita chamando o ```Listen``` método . A porta de handshake e a porta de transporte podem ser especificadas durante essa chamada. A porta de handshake é usada para o handshake inicial. Em seguida, os dados são enviados pela porta de transporte. Por **padrão, 8265** e **8266** são usados.

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
>O dentro do pacote NuGet contém documentação detalhada para a ```build\native\include\HolographicAppRemoting\Microsoft.Holographic.AppRemoting.idl``` API exposta pela Holographic Remoting.

## <a name="handling-remoting-specific-events"></a>Manipulando eventos específicos de remoting

O contexto remoto expõe três eventos, que são importantes para monitorar o estado de uma conexão.
1) OnConnected: disparado quando uma conexão com o dispositivo foi estabelecida com êxito.
```cpp
winrt::weak_ref<winrt::Microsoft::Holographic::AppRemoting::IRemoteContext> remoteContextWeakRef = m_remoteContext;

m_onConnectedEventRevoker = m_remoteContext.OnConnected(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```
2) OnDisconnected: disparado se uma conexão estabelecida for fechada ou não for possível estabelecer uma conexão.
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
3) OnListening: ao escutar conexões de entrada é iniciado.
```cpp
m_onListeningEventRevoker = m_remoteContext.OnListening(winrt::auto_revoke, [this, remoteContextWeakRef]() {
    if (auto remoteContext = remoteContextWeakRef.get())
    {
        // Update UI state
    }
});
```

Além disso, o estado de conexão pode ser consultado usando ```ConnectionState``` a propriedade no contexto remoto.
```cpp
auto connectionState = m_remoteContext.ConnectionState();
```

## <a name="handling-speech-events"></a>Manipulando eventos de fala

Usando a interface de fala remota, é possível registrar gatilhos de fala com HoloLens 2 e fazer com que eles remotos para o aplicativo remoto.

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

Usando um método auxiliar assíncrono, você pode inicializar a fala remota. Isso deve ser feito de forma assíncrona, pois inicializar pode levar um tempo considerável. As operações assíncronas e assíncronas com [C++/WinRT](/windows/uwp/cpp-and-winrt-apis/concurrency) explicam como a adoção de funções assíncronas com C++/WinRT.

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
1) Especificação dentro de um arquivo xml de gramática de fala. Consulte [Como criar uma gramática XML básica para](/previous-versions/office/developer/speech-technologies/hh361658(v=office.14)) obter detalhes.
2) Especifique passando-os dentro do vetor de dicionário para ```ApplyParameters``` .

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

Para exibir o mesmo conteúdo no aplicativo remoto que é enviado ao dispositivo, o ```OnSendFrame``` evento do contexto remoto pode ser usado. O ```OnSendFrame``` evento é disparado sempre que a biblioteca de remoção holográfica envia o quadro atual para o dispositivo remoto. Esse é o momento ideal para pegar o conteúdo e também blit-lo na área de trabalho ou na janela UWP.

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

## <a name="depth-reprojection"></a>Reprodução de profundidade

A partir da [versão 2.1.0,](holographic-remoting-version-history.md#v2.1.0)a Holographic Remoting dá suporte [à Reprojeção de Profundidade.](hologram-stability.md#reprojection) Isso exige que o buffer de cores e o buffer de profundidade sejam transmitidos do aplicativo remoto para o HoloLens 2. Por padrão, o streaming de buffer de profundidade está habilitado e configurado para usar metade da resolução do buffer de cores. Isso pode ser alterado da seguinte forma:

```cpp
// class implementation
#include <HolographicAppRemoting\Streamer.h>

...

CreateRemoteContext(m_remoteContext, 20000, false, PreferredVideoCodec::Default);

// Configure for half-resolution depth.
m_remoteContext.ConfigureDepthVideoStream(DepthBufferStreamResolution::Half_Resolution);

```

Observe que se os valores padrão não devem ser usados devem ser chamados antes de estabelecer uma conexão com ```ConfigureDepthVideoStream``` o HoloLens 2. O melhor lugar é logo depois de você ter criado o contexto remoto. Os valores possíveis para DepthBufferStreamResolution são:

* Full_Resolution
* Half_Resolution
* Quarter_Resolution
* Desabilitado (adicionado com a [versão 2.1.3](holographic-remoting-version-history.md#v2.1.3) e, se usado, nenhum fluxo de vídeo de profundidade adicional é criado)

Tenha em mente que o uso de um buffer de profundidade de resolução completa também afeta os requisitos de largura de banda e precisa ser contabilado no valor máximo de largura de banda que você fornece ao ```CreateRemoteContext``` .

Além de configurar a resolução, você também precisa fazer commit de um buffer de profundidade por meio de [HolographicCameraRenderingParameters.CommitDirect3D11DepthBuffer](/uwp/api/windows.graphics.holographic.holographiccamerarenderingparameters.commitdirect3d11depthbuffer#Windows_Graphics_Holographic_HolographicCameraRenderingParameters_CommitDirect3D11DepthBuffer_Windows_Graphics_DirectX_Direct3D11_IDirect3DSurface_).

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

Para verificar se a reprojetação de profundidade está funcionando corretamente no HoloLens 2, você pode habilitar um visualizador de profundidade por meio do Portal de Dispositivos. Confira [Verificar se a profundidade está definida corretamente para](hologram-stability.md#verifying-depth-is-set-correctly) obter detalhes.

## <a name="optional-custom-data-channels"></a>Opcional: Canais de dados personalizados

Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota já estabelecida. Consulte [canais de dados personalizados](holographic-remoting-custom-data-channels.md) para obter mais informações.

## <a name="see-also"></a>Consulte Também
* [Visão geral da comunicação remota do Holographic](holographic-remoting-overview.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Canais de dados personalizados de comunicação remota holográfica](holographic-remoting-custom-data-channels.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)