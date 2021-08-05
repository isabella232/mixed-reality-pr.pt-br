---
title: Escrevendo um aplicativo remoto de remota remota holográfico (OpenXR)
description: Saiba como transmitir conteúdo remoto renderizado em um computador remoto para HoloLens 2 com aplicativos holográficos de remota com OpenXR.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, Remoting, Holographic Remoting, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, NuGet
ms.openlocfilehash: 6cf44bd031aec4b475d7496a999a3c7d4d40cae7cc921ff39cfe61698f3dd532
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115212064"
---
# <a name="writing-a-holographic-remoting-remote-app-using-the-openxr-api"></a>Escrevendo um aplicativo remoto de remoção holográfica usando a API openXR

>[!IMPORTANT]
>Este documento descreve a criação de um aplicativo remoto para headsets HoloLens 2 e Windows Mixed Reality usando a [API openXR](../native/openxr.md). Os aplicativos **remotos HoloLens (1ª geração)** devem usar NuGet versão **1.x.x do pacote.** Isso implica que aplicativos remotos escritos para HoloLens 2 não são compatíveis com HoloLens 1 e vice-versa. A documentação HoloLens 1 pode ser encontrada [aqui.](add-holographic-remoting.md)

Os aplicativos de remotação holográfica podem transmitir conteúdo renderizado remotamente para HoloLens 2 e Windows Mixed Reality headsets imersivos. Você também pode acessar mais recursos do sistema e integrar exibições [imersivas remotas](../../design/app-views.md) ao software de computador desktop existente. Um aplicativo remoto recebe um fluxo de dados de entrada do HoloLens 2, renderiza o conteúdo em uma exibição imersiva virtual e transmite quadros de conteúdo de volta para HoloLens 2. A conexão é feita usando o Wi-Fi padrão. A remota holográfica é adicionada a um aplicativo UWP ou área de trabalho por meio de um NuGet pacote. É necessário um código adicional que trata a conexão e renderiza em uma exibição imersiva. Uma conexão de remoting típica terá até 50 ms de latência. O aplicativo player pode relatar a latência em tempo real.

Todo o código nesta página e projetos de trabalho podem ser encontrados no repositório [GitHub](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)de exemplos de Remo holográfica .

## <a name="prerequisites"></a>Pré-requisitos

Um bom ponto de partida é um aplicativo UWP ou Área de Trabalho baseado em OpenXR em funcionamento. Para obter [detalhes, consulte Getting started with OpenXR](../native/openxr-getting-started.md).

>[!IMPORTANT]
>Qualquer aplicativo que use a Holographic Remoting deve ser autor para usar um [apartment multi-threaded.](/windows/win32/com/multithreaded-apartments) Há suporte para o uso de um apartment de [thread](/windows/win32/com/single-threaded-apartments) único, mas levará ao desempenho abaixo do ideal e possivelmente à gagueja durante a reprodução. Ao usar C++/WinRT [winrt::init_apartment](/windows/uwp/cpp-and-winrt-apis/get-started) um apartment multi-threaded é o padrão.

## <a name="get-the-holographic-remoting-nuget-package"></a>Obter o pacote de NuGet de NuGet Holographic

As etapas a seguir são necessárias para adicionar o pacote NuGet a um projeto no Visual Studio.
1. Abra o projeto no Visual Studio.
2. Clique com o botão direito do mouse no nó do projeto **e selecione Gerenciar NuGet Pacotes...**
3. No painel exibido, selecione **Procurar** e, em seguida, pesquise "Holographic Remoting".
4. Selecione **Microsoft.Holographic.Remoting.OpenXr,** escolha a versão **2.x.x** mais recente e **selecione Instalar**.
5. Se a **caixa de** diálogo Visualização for exibida, selecione **OK.**
6. Selecione **Aceito quando** a caixa de diálogo do contrato de licença for exibida.
7. Repita as etapas de 3 a 6 para os seguintes pacotes NuGet: OpenXR.Headers, OpenXR.Loader

>[!NOTE]
>A **versão 1.x.x** do pacote NuGet ainda está disponível para desenvolvedores que querem direcionar HoloLens 1. Para obter [detalhes, consulte Adicionar a remoção holográfica (HoloLens (1ª geração))](add-holographic-remoting.md).

## <a name="select-the-holographic-remoting-openxr-runtime"></a>Selecione o runtime do OpenXR de Remoção Holográfica

A primeira etapa que você precisa fazer em seu aplicativo remoto é selecionar o runtime do OpenXR de Remota holográfica, que faz parte do pacote de NuGet Microsoft.Holographic.Remoting.OpenXr. Você pode fazer isso definindo a variável de ambiente como o caminho do ```XR_RUNTIME_JSON``` RemotingXR.jsno arquivo em seu aplicativo. Essa variável de ambiente é usada pelo carregador OpenXR para não usar o runtime do OpenXR padrão do sistema, mas redirecionar para o runtime do OpenXR de remoção holográfica. Ao usar o pacote NuGet Microsoft.Holographic.Remoting.OpenXr, o arquivo RemotingXR.json é copiado automaticamente durante a compilação para a pasta de saída, a seleção de runtime do OpenXR normalmente é a seguinte.

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

## <a name="create-xrinstance-with-holographic-remoting-extension"></a>Criar XrInstance com extensão de remoção holográfica

A primeira etapa que um aplicativo OpenXR típico deve fazer é selecionar extensões OpenXR e criar um XrInstance. A especificação do núcleo do OpenXR não fornece nenhuma API específica de remoção. Por esse motivo, a Holographic Remoting introduz sua própria extensão OpenXR chamada ```XR_MSFT_holographic_remoting``` . Verifique se, ao chamar xrCreateInstance, ```XR_MSFT_HOLOGRAPHIC_REMOTING_EXTENSION_NAME``` o está incluído no XrInstanceCreateInfo.

>[!TIP]
>Por padrão, o conteúdo renderizado do seu aplicativo é transmitido somente para o player de Remoção Holográfica em execução em um HoloLens 2 ou em um Windows Mixed Reality headsets. Para também exibir o conteúdo renderizado no computador remoto, por meio de uma cadeia de troca de uma janela, por exemplo, o Holographic Remoting fornece uma segunda extensão OpenXR chamada ```XR_MSFT_holographic_remoting_frame_mirroring``` . Certifique-se de também habilitar essa ```XR_MSFT_HOLOGRAPHIC_REMOTING_FRAME_MIRRORING_EXTENSION_NAME``` extensão usando caso você queira usar essa funcionalidade.

>[!IMPORTANT]
>Para saber mais sobre a API de extensão do [](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html) OpenXR de Remoção Holográfica, confira a especificação que pode ser encontrada no repositório [github de exemplos de Remo holográfica.](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples)

## <a name="connect-to-the-device"></a>Conexão para o dispositivo

Depois que seu aplicativo remoto tiver criado o XrInstance e consultado xrSystemId por meio de xrGetSystem, uma conexão com o dispositivo player poderá ser estabelecida.

>[!WARNING]
> O runtime do OpenXR de Remoção Holográfica só é capaz de fornecer dados específicos do dispositivo, como configurações de exibição ou modos de mesclagem de ambiente depois que uma conexão é estabelecida. ```xrEnumerateViewConfigurations```, , , e lhe darão valores padrão, correspondendo ao que você normalmente obteria se se conectasse a um player em execução em um ```xrEnumerateViewConfigurationViews``` ```xrGetViewConfigurationProperties``` HoloLens ```xrEnumerateEnvironmentBlendModes``` 2, antes de estar ```xrGetSystemProperties``` totalmente conectado.
É altamente recomendável não chamar esses métodos antes que uma conexão seja estabelecida. A sugestão é usada esses métodos depois que a XrSession tiver sido criada com êxito e o estado da sessão for pelo menos XR_SESSION_STATE_READY.

Propriedades gerais, como taxa de bits máxima, áudio habilitado, codec de vídeo ou resolução de fluxo de buffer de profundidade, podem ser configuradas por meio ```xrRemotingSetContextPropertiesMSFT``` da seguinte maneira.

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
1) O aplicativo remoto se conecta ao player em execução no dispositivo.
2) O player em execução no dispositivo se conecta ao aplicativo remoto.

Para estabelecer uma conexão do aplicativo remoto com o dispositivo player, chame o método especificando o nome do host e a ```xrRemotingConnectMSFT``` porta por meio da estrutura  ```XrRemotingConnectInfoMSFT``` . A porta usada pelo Holographic Remoting Player é **8265.**

```cpp
XrRemotingConnectInfoMSFT connectInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_CONNECT_INFO_MSFT)};
connectInfo.remoteHostName = "192.168.x.x";
connectInfo.remotePort = 8265;
connectInfo.secureConnection = false;
xrRemotingConnectMSFT(m_instance.Get(), m_systemId, &connectInfo);
```

A escuta de conexões de entrada no aplicativo remoto pode ser feita chamando o ```xrRemotingListenMSFT``` método . A porta de handshake e a porta de transporte podem ser especificadas por meio da ```XrRemotingListenInfoMSFT``` estrutura . A porta de handshake é usada para o handshake inicial. Em seguida, os dados são enviados pela porta de transporte. Por **padrão, 8265** e **8266** são usados.

```cpp
XrRemotingListenInfoMSFT listenInfo{static_cast<XrStructureType>(XR_TYPE_REMOTING_LISTEN_INFO_MSFT)};
listenInfo.listenInterface = "0.0.0.0";
listenInfo.handshakeListenPort = 8265;
listenInfo.transportListenPort = 8266;
listenInfo.secureConnection = false;
xrRemotingListenMSFT(m_instance.Get(), m_systemId, &listenInfo);
```

O estado de conexão deve ser desconectado quando você chama ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` . Você pode obter o estado de conexão a qualquer momento depois de ter criado um XrInstance e consultado para o XrSystemId via ```xrRemotingGetConnectionStateMSFT``` .

```cpp
XrRemotingConnectionStateMSFT connectionState;
xrRemotingGetConnectionStateMSFT(m_instance.Get(), m_systemId, &connectionState, nullptr);
```

Os estados de conexão disponíveis são:
- XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTING_MSFT
- XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT

>[!IMPORTANT]
> ```xrRemotingConnectMSFT``` ou ```xrRemotingListenMSFT``` deve ser chamado antes de tentar criar uma XrSession por meio de xrCreateSession. Se você tentar criar uma XrSession enquanto o estado de conexão for a criação da sessão terá êxito, mas o estado da sessão fará a transição imediatamente para ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` XR_SESSION_STATE_LOSS_PENDING.

A implementação do Holographic Remoting de ```xrCreateSession``` dá suporte à espera de uma conexão ser estabelecida. Você pode chamar ou imediatamente seguido por uma chamada para, que bloqueará e ```xrRemotingConnectMSFT``` ```xrRemotingListenMSFT``` aguardará que uma conexão seja estabelecida. O tempo de vida é fixo em 10 segundos. Se uma conexão puder ser estabelecida dentro desse tempo, a criação de XrSession terá êxito e o estado da sessão fará a transição para XR_SESSION_STATE_READY. Caso nenhuma conexão possa ser estabelecida, a criação da sessão também terá êxito, mas faz a transição imediatamente para XR_SESSION_STATE_LOSS_PENDING.

Em geral, o estado de conexão é junto com o estado XrSession. Qualquer alteração no estado de conexão também afeta o estado da sessão. Por exemplo, se o estado de conexão mudar de para o estado de sessão, a transição para `XR_REMOTING_CONNECTION_STATE_CONNECTED_MSFT` ```XR_REMOTING_CONNECTION_STATE_DISCONNECTED_MSFT``` XR_SESSION_STATE_LOSS_PENDING também.

## <a name="handling-remoting-specific-events"></a>Manipulando eventos específicos de remoting

O runtime do OpenXR de Remoção Holográfica expõe três eventos, que são importantes para monitorar o estado de uma conexão.
1) ```XR_TYPE_REMOTING_EVENT_DATA_CONNECTED_MSFT```: disparado quando uma conexão com o dispositivo foi estabelecida com êxito.
2) ```XR_TYPE_REMOTING_EVENT_DATA_DISCONNECTED_MSFT```: disparado se uma conexão estabelecida for fechada ou não for possível estabelecer uma conexão.
3) ```XR_TYPE_REMOTING_EVENT_DATA_LISTENING_MSFT```: ao escutar conexões de entrada é iniciado.

Esses eventos são colocados em uma fila e seu aplicativo remoto deve ler da fila com regularidade por meio de ```xrPollEvent``` .

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

Para exibir o mesmo conteúdo no aplicativo remoto que é enviado ao dispositivo, a ```XR_MSFT_holographic_remoting_frame_mirroring``` extensão pode ser usada. Com essa extensão, você pode enviar uma textura para xrEndFrame usando o que não está encadeado ao ```XrRemotingFrameMirrorImageInfoMSFT``` XrFrameEndInfo da seguinte forma.

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

O exemplo acima usa uma textura de cadeia de permuta DX11 e apresenta a janela imediatamente após a chamada para xrEndFrame. O uso não está restrito a texturas de cadeia de permuta e nenhuma sincronização de GPU adicional é necessária. Para obter detalhes sobre o uso e as restrições, confira a [especificação de extensão](https://htmlpreview.github.io/?https://github.com/microsoft/MixedReality-HolographicRemoting-Samples/blob/master/remote_openxr/specification.html#XR_MSFT_remoting_frame_mirroring).
Se o aplicativo remoto estiver usando DX12, use XrRemotingFrameMirrorImageD3D12MSFT em vez de XrRemotingFrameMirrorImageD3D11MSFT.

## <a name="see-also"></a>Consulte Também
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Como estabelecer uma conexão segura com o Holographic Remoting](holographic-remoting-secure-connection.md)
* [Solução de problemas e limitações de remoção holográfica](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)