---
title: Escrevendo um aplicativo remoto de comunicação remota do Holographic (OpenXR)
description: Ao criar um aplicativo remoto de comunicação remota do Holographic, o conteúdo remoto, que é processado em um computador remoto, pode ser transmitido para o HoloLens 2. Este artigo descreve como isso pode ser feito.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, comunicação remota Holographic, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, NuGet
ms.openlocfilehash: 7e46c67e7dac08759890fa66d540379991414aad
ms.sourcegitcommit: 9664bcc10ed7e60f7593f3a7ae58c66060802ab1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96469489"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Escrevendo um aplicativo remoto de comunicação remota do Holographic usando a API do OpenXR

>[!IMPORTANT]
>Este documento descreve a criação de um aplicativo remoto para os headsets do HoloLens 2 e do Windows Mixed Reality usando a [API OpenXR](../native/openxr.md). Os aplicativos remotos para o **HoloLens (1º gen)** devem usar o pacote NuGet versão **1. x**. x. Isso significa que os aplicativos remotos escritos para o HoloLens 2 não são compatíveis com o HoloLens 1 e vice-versa. A documentação do HoloLens 1 pode ser encontrada [aqui](add-holographic-remoting.md).

Ao criar um aplicativo remoto de comunicação remota do Holographic, o conteúdo remoto que é processado em um computador remoto pode ser transmitido para dispositivos HoloLens 2 e de imersão, como headsets de realidade mista do Windows. Este artigo descreve como isso pode ser feito. Todo o código nesta página e projetos de trabalho podem ser encontrados no [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

A comunicação remota do Holographic permite que um aplicativo direcione fones de ouvido 2 e Windows Mixed Realm headsets com conteúdo Holographic processado em um PC desktop ou em um dispositivo UWP, como o Xbox, permitindo o acesso a mais recursos do sistema e possibilitando a integração de [exibições de imersão](../../design/app-views.md) remotas ao software de PC desktop existente. Um aplicativo remoto recebe um fluxo de dados de entrada do HoloLens 2, renderiza o conteúdo em uma exibição de imersão virtual e transmite os quadros de conteúdo de volta para o HoloLens 2. A conexão é feita usando Wi-Fi padrão. A comunicação remota do Holographic é adicionada a um aplicativo de desktop ou UWP por meio de um pacote NuGet. É necessário um código adicional que manipula a conexão e é renderizado em uma exibição de imersão.

Uma conexão de comunicação remota típica terá um mínimo de 50 ms de latência. O aplicativo de player pode relatar a latência em tempo real.

## <a name="prerequisites"></a>Pré-requisitos

Um bom ponto de partida é um aplicativo de desktop ou UWP baseado em OpenXR de trabalho. Para obter detalhes, consulte [introdução ao OpenXR](../native/openxr-getting-started.md).

>[!IMPORTANT]
>Qualquer aplicativo usando a comunicação remota do Holographic deve ser criado para usar um [apartamento](https://docs.microsoft.com//windows/win32/com/multithreaded-apartments)multi-threaded. O uso de um [apartamento de thread único](https://docs.microsoft.com//windows/win32/com/single-threaded-apartments) é suportado, mas levará a um desempenho abaixo do ideal e possivelmente ocorrendo durante a reprodução. Ao usar C++/WinRT [WinRT:: init_apartment](https://docs.microsoft.com//windows/uwp/cpp-and-winrt-apis/get-started) um apartamento multi-threaded é o padrão.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obter o pacote NuGet de comunicação remota do Holographic

As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.
1. Abra o projeto no Visual Studio.
2. Clique com o botão direito do mouse no nó do projeto e selecione **gerenciar pacotes NuGet...**
3. No painel que aparece, clique em **procurar** e procure "comunicação remota do Holographic".
4. Selecione **Microsoft. Holographic. Remoting. OpenXr**, certifique-se de escolher a versão mais recente do **2. x. x** e clique em **instalar**.
5. Se a caixa de diálogo **Visualizar** for exibida, clique em **OK**.
6. A próxima caixa de diálogo exibida é o contrato de licença. Clique em **aceito** para aceitar o contrato de licença.
7. Repita as etapas de 3 a 6 para os seguintes pacotes NuGet: OpenXR. Headers, OpenXR. Loader

>[!NOTE]
>A versão **1. x. x** do pacote NuGet ainda está disponível para desenvolvedores que desejam direcionar para o HoloLens 1. Para obter detalhes, consulte [Add Holographic Remoting (HoloLens (1º gen))](add-holographic-remoting.md).

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Selecione o tempo de execução do Holographic Remoting OpenXR

A primeira etapa que você precisa fazer em seu aplicativo remoto é selecionar o tempo de execução do Holographic Remoting OpenXR que faz parte do pacote NuGet Microsoft. Holographic. Remoting. OpenXr. Você pode fazer isso definindo a ```XR_RUNTIME_JSON``` variável de ambiente para o caminho do RemotingXR.jsno arquivo em seu aplicativo. Essa variável de ambiente é usada pelo carregador OpenXR para não usar o tempo de execução OpenXR padrão do sistema, mas em vez disso, redirecionar para o tempo de execução do Holographic Remoting OpenXR. Ao usar o pacote NuGet Microsoft. Holographic. Remoting. OpenXr, o RemotingXR.jsno arquivo é copiado automaticamente durante a compilação para a pasta de saída, portanto, a seleção do OpenXR Runtime geralmente tem a seguinte aparência.

```cpp
bool EnableRemotingXR() {
    wchar_t executablePath[MAX_PATH];
    if (GetModuleFileNameW(NULL, executablePath, ARRAYSIZE(executablePath)) == 0) {
        return false;
    }
    
    std::filesystem::path filename(executablePath);
    filename = filename.replace_filename("RemotingXR.json");

    if (std::filesystem::exists(filename)) {
        SetEnvironmentVariableW(L"XR_RUNTIME_JSON", filename.c_str());
            return true;
        }

    return false;
}
```

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Criar XrInstance com a extensão de comunicação remota Holographic

A primeira etapa que um aplicativo OpenXR típico deve fazer é selecionar extensões OpenXR e criar um XrInstance. A especificação OpenXR Core não fornece nenhuma API específica de comunicação remota. Por esse motivo, a comunicação remota Holographic introduz sua própria extensão OpenXR chamada ```XR_MSFT_holographic_remoting``` . Certifique-se de que, quando você chamar xrCreateInstance, o ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` esteja incluído no XrInstanceCreateInfo.

>[!TIP]
>Por padrão, o conteúdo renderizado de seu aplicativo é transmitido somente para o player de comunicação remota Holographic em execução em um HoloLens 2 ou em headsets de realidade mista do Windows. Para exibir também o conteúdo renderizado no PC remoto, por meio de uma cadeia de troca de uma janela por exemplo, a comunicação remota do Holographic fornece uma segunda extensão OpenXR chamada ```XR_MSFT_holographic_remoting_frame_mirroring``` . Certifique-se também de habilitar essa extensão usando o ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` caso queira usar essa funcionalidade.

>[!IMPORTANT]
>Para saber mais sobre a API de extensão de OpenXR de comunicação remota Holographic, confira a [especificação](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) que pode ser encontrada no [repositório GitHub de exemplos de comunicação remota Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples).

## <a name="connect-to-the-device"></a>Conectar-se ao dispositivo

Depois que seu aplicativo remoto tiver criado o XrInstance e consultado o XrSystemId por meio do xrGetSystem, uma conexão com o dispositivo do Player poderá ser estabelecida.

>[!WARNING]
> O tempo de execução do Holographic Remoting OpenXR só é capaz de fornecer dados específicos do dispositivo, como configurações de exibição ou modos de mistura de ambiente depois que uma conexão é estabelecida. ```xrEnumerateViewConfigurations```, ```xrEnumerateViewConfigurationViews``` , ```xrGetViewConfigurationProperties``` , ```xrEnumerateEnvironmentBlendModes``` e fornecerão ```xrGetSystemProperties``` valores padrão, correspondendo ao que você normalmente obteria se você se conectar a um player em execução em um HoloLens 2, antes de ser totalmente conectado.
É altamente recomendável não chamar esses métodos antes que uma conexão seja estabelecida. A sugestão é usar esses métodos depois que o XrSession tiver sido criado com êxito e o estado da sessão for pelo menos XR_SESSION_STATE_READY.

As propriedades gerais, como taxa de bits máxima, habilitação de áudio, codec de vídeo ou resolução de fluxo de buffer de profundidade, podem ser configuradas ```xrRemotingSetContextPropertiesMSFT``` da seguinte maneira.

```cpp
XrRemotingRemoteContextPropertiesMSFT contextProperties;
contextProperties = XrRemotingRemoteContextPropertiesMSFT{static_cast<XrStructureType>(XR_TYPE_REMOTING_REMOTE_CONTEXT_PROPERTIES_MSFT)};
contextProperties.enableAudio = false;
contextProperties.maxBitrateKbps = 20000;
contextProperties.videoCodec = XR_REMOTING_VIDEO_CODEC_H265_MSFT;
contextProperties.depthBufferStreamResolution = XR_REMOTING_DEPTH_BUFFER_STREAM_RESOLUTION_HALF_MSFT;
xrRemotingSetContextPropertiesMSFT(m_instance.Get(), m_systemId, &contextProperties);
```

A conexão pode ser feita de duas maneiras.
1) O aplicativo remoto se conecta ao Player em execução no dispositivo.
2) O Player em execução no dispositivo se conecta ao aplicativo remoto.

Para estabelecer uma conexão do aplicativo remoto com o dispositivo do Player, chame o ```xrRemotingConnectMSFT``` método que especifica o nome do host e a porta por meio da  ```XrRemotingConnectInfoMSFT``` estrutura. A porta usada pelo Holographic Remoting Player é **8265**.

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

A escuta de conexões de entrada no aplicativo remoto pode ser feita chamando o ```xrRemotingListenMSFT``` método. A porta de handshake e a porta de transporte podem ser especificadas por meio da ```XrRemotingListenInfoMSFT``` estrutura. A porta de handshake é usada para o handshake inicial. Os dados são enviados pela porta de transporte. Por padrão, **8265** e **8266** são usados.

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

O estado da conexão deve ser desconectado quando você chama ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` . Você pode obter o estado da conexão a qualquer momento depois de ter criado um XrInstance e consultado para o XrSystemId por meio de ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Os Estados de conexão disponíveis são:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` deve ser chamado antes de tentar criar um XrSession via xrCreateSession. Se você tentar criar um XrSession enquanto o estado da conexão for ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` a criação da sessão terá sucesso, mas o estado da sessão passará imediatamente para XR_SESSION_STATE_LOSS_PENDING.

A implementação de comunicação remota Holographic do ```xrCreateSession``` dá suporte à espera de uma conexão ser estabelecida. Você pode chamar ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` imediatamente seguido por uma chamada para a ```xrCreateSession``` qual bloqueará e aguardará que uma conexão seja estabelecida. O tempo limite é fixo para 10 segundos. Se uma conexão puder ser estabelecida dentro dessa hora, a criação do XrSession terá sucesso e o estado da sessão passará para XR_SESSION_STATE_READY. Caso nenhuma conexão possa ser estabelecida, a criação da sessão também é bem sucedido, mas imediatamente faz a transição para XR_SESSION_STATE_LOSS_PENDING.

Em geral, o estado de conexão é combinado com o estado XrSession. Qualquer alteração no estado da conexão também afeta o estado da sessão. Por exemplo, se o estado de conexão mudar de `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` para ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` o estado de sessão também fará a transição para XR_SESSION_STATE_LOSS_PENDING.

## <a name="handling-remoting-specific-events"></a>Manipulando eventos específicos de comunicação remota

O tempo de execução de OpenXR de comunicação remota do Holographic expõe três eventos que são importantes para monitorar o estado de uma conexão.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: Disparado quando uma conexão com o dispositivo foi estabelecida com êxito.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: Disparado se uma conexão estabelecida é fechada ou uma conexão não pôde ser estabelecida.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: Quando a escuta de conexões de entrada é iniciada.

Esses eventos são colocados em uma fila e seu aplicativo remoto deve ler a partir da fila com regularidade via ```xrPollEvent``` .

```cpp
auto pollEvent = [&](XrEventDataBuffer& eventData) -> bool {
    eventData.type = XR_TYPE_EVENT_DATA_BUFFER;
    eventData.next = nullptr;
    return CHECK_XRCMD(xrPollEvent(m_instance.Get(), &eventData)) == XR_SUCCESS;
};

XrEventDataBuffer eventData{};
while (pollEvent(eventData)) {
    switch (eventData.type) {
    
    ...
    
    case XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Listening on port %d",
                    reinterpret_cast<const XrRemotingEventDataListeningMSFT*>(&eventData)->listeningPort);
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Connected.");
        break;
    }
    case XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT: {
        DEBUG_PRINT("Holographic Remoting: Disconnected - Reason: %d",
                    reinterpret_cast<const XrRemotingEventDataDisconnectedMSFT*>(&eventData)->disconnectReason);
        break;
    }
}
```

## <a name="preview-streamed-content-locally"></a>Visualizar conteúdo transmitido localmente

Para exibir o mesmo conteúdo no aplicativo remoto que é enviado para o dispositivo, a ```XR_MSFT_holographic_remoting_frame_mirroring``` extensão pode ser usada. Com essa extensão, você pode enviar uma textura para xrEndFrame. Isso é feito usando a ```XrRemotingFrameMirrorImageInfoMSFT``` estrutura que é encadeada ao XrFrameEndInfo da seguinte maneira.

```cpp
XrFrameEndInfo frameEndInfo{XR_TYPE_FRAME_END_INFO};
...

XrRemotingFrameMirrorImageD3D11MSFT mirrorImageD3D11{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_D3D11_MSFT)};
mirrorImageD3D11.texture = m_window->GetNextSwapchainTexture();

XrRemotingFrameMirrorImageInfoMSFT mirrorImageEndInfo{
    static_cast<XrStructureType>(XR_TYPE_REMOTING_FRAME_MIRROR_IMAGE_INFO_MSFT)};
mirrorImageEndInfo.image = reinterpret_cast<const XrRemotingFrameMirrorImageBaseHeaderMSFT*>(&mirrorImageD3D11);

frameEndInfo.next = &mirrorImageEndInfo;

xrEndFrame(m_session.Get(), &frameEndInfo);

m_window->PresentSwapchain();
```

O exemplo acima usa uma textura de cadeia de permuta DX11 e apresenta a janela imediatamente após a chamada para xrEndFrame. O uso não é restrito a texturas de cadeia de permuta e nenhuma sincronização de GPU adicional é necessária. Para obter detalhes sobre o uso e as restrições, confira a [especificação de extensão](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Se seu aplicativo remoto estiver usando o DX12, use XrRemotingFrameMirrorImageD3D12MSFT em vez de XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Consulte Também
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](https://docs.microsoft.com//legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)
