---
title: Canais de dados personalizados de comunicação remota holográfica
description: Os canais de dados personalizados podem ser usados para enviar dados do usuário pela conexão remota Holographic já estabelecida.
author: florianbagarmicrosoft
ms.author: flbagar
ms.date: 12/01/2020
ms.topic: article
keywords: HoloLens, comunicação remota, comunicação remota Holographic, headset de realidade misturada, headset de realidade mista do windows, headset da realidade virtual, canais de dados
ms.openlocfilehash: 1adda10aa7792eaeab0ac32cb37d73dcfd2b58e6
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184707"
---
# <a name="custom-holographic-remoting-data-channels-c"></a>Canais de dados de comunicação remota Holographic personalizados (C++)

>[!NOTE]
>estas diretrizes são específicas para a comunicação remota do Holographic no HoloLens 2.

Use canais de dados personalizados para enviar dados personalizados por meio de uma conexão remota estabelecida.

>[!IMPORTANT]
>Os canais de dados personalizados exigem um aplicativo remoto personalizado e um aplicativo de player personalizado, pois ele permite a comunicação entre os dois aplicativos personalizados.

>[!TIP]
>Um exemplo simples de pingue-pongue pode ser encontrado nos exemplos remoto e de Player dentro do [repositório GitHub de exemplos de comunicação remota do Holographic](https://github.com/microsoft/MixedReality-HolographicRemoting-Samples). Remova os comentários nos ```#define ENABLE_CUSTOM_DATA_CHANNEL_SAMPLE``` arquivos SampleRemoteMain. h/SamplePlayerMain. h para habilitar o código de exemplo.


## <a name="create-a-custom-data-channel"></a>Criar um canal de dados personalizado


Para criar um canal de dados personalizado, são necessários os seguintes campos:
```cpp
std::recursive_mutex m_customDataChannelLock;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel m_customDataChannel = nullptr;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnDataReceived_revoker m_customChannelDataReceivedEventRevoker;
winrt::Microsoft::Holographic::AppRemoting::IDataChannel::OnClosed_revoker m_customChannelClosedEventRevoker;
```

Depois que uma conexão é estabelecida com êxito, você pode criar novos canais de dados do lado remoto, do lado do jogador ou de ambos. O RemoteContext e o PlayerContext fornecem um ```CreateDataChannel()``` método para a criação de canais de dados. O primeiro parâmetro é a ID do canal, que é usada para identificar o canal de dados em operações subsequentes. O segundo parâmetro é a prioridade, que especifica a prioridade com a qual os dados desse canal são transferidos para o outro lado. As IDs de canal válidas no lado remoto são de 0 até e incluindo 63 e 64 até e incluindo 127 para o lado do jogador. As prioridades válidas são ```Low``` , ```Medium``` ou ```High``` (em ambos os lados).

Para iniciar a criação de um canal de dados no lado **remoto** :
```cpp
// Valid channel ids for channels created on the remote side are 0 up to and including 63
m_remoteContext.CreateDataChannel(0, DataChannelPriority::Low);
```

Para iniciar a criação de um canal de dados no lado do **jogador** :
```cpp
// Valid channel ids for channels created on the player side are 64 up to and including 127
m_playerContext.CreateDataChannel(64, DataChannelPriority::Low);
```

>[!NOTE]
>Para criar um novo canal de dados personalizado, apenas um lado (remoto ou Player) precisa chamar o ```CreateDataChannel``` método.

## <a name="handling-custom-data-channel-events"></a>Manipulando eventos de canal de dados personalizados

Para estabelecer um canal de dados personalizado, o ```OnDataChannelCreated``` evento precisa ser tratado (tanto no Player quanto no lado remoto). Ele é disparado quando um canal de dados do usuário é criado por um dos lados e fornece um ```IDataChannel``` objeto, que pode ser usado para enviar e receber dados por esse canal.

Para registrar um ouvinte no ```OnDataChannelCreated``` evento:
```cpp
m_onDataChannelCreatedEventRevoker = m_remoteContext.OnDataChannelCreated(winrt::auto_revoke,
    [this](const IDataChannel& dataChannel, uint8_t channelId)
    {
        std::lock_guard lock(m_customDataChannelLock);
        m_customDataChannel = dataChannel;

        // Register to OnDataReceived and OnClosed event of the data channel here, see below...
    });
```

Para ser notificado quando os dados são recebidos, registre-se ```OnDataReceived``` no evento no ```IDataChannel``` objeto fornecido pelo ```OnDataChannelCreated``` manipulador. Registre-se no ```OnClosed``` evento para ser notificado quando o canal de dados tiver sido fechado.

```cpp
m_customChannelDataReceivedEventRevoker = m_customDataChannel.OnDataReceived(winrt::auto_revoke, 
    [this]()
    {
        // React on data received via the custom data channel here.
    });

m_customChannelClosedEventRevoker = m_customDataChannel.OnClosed(winrt::auto_revoke,
    [this]()
    {
        // React on data channel closed here.

        std::lock_guard lock(m_customDataChannelLock);
        if (m_customDataChannel)
        {
            m_customDataChannel = nullptr;
        }
    });
```

## <a name="sending-data"></a>Enviar dados

Para enviar dados por um canal de dados personalizado, use o ```IDataChannel::SendData()``` método. O primeiro parâmetro é um ```winrt::array_view<const uint8_t>``` para os dados que devem ser enviados. O segundo parâmetro especifica onde os dados devem ser reenviados, até o outro lado reconhecer a recepção. 

>[!IMPORTANT]
>No caso de condições de rede inadequadas, o mesmo pacote de dados pode chegar mais de uma vez. O código de recebimento deve ser capaz de lidar com essa situação.

```cpp
uint8_t data[] = {1};
m_customDataChannel.SendData(data, true);
```

## <a name="closing-a-custom-data-channel"></a>Fechando um canal de dados personalizado

Para fechar um canal de dados personalizado, use o ```IDataChannel::Close()``` método. Os dois lados serão notificados pelo ```OnClosed``` evento depois que o canal de dados personalizado for fechado.

```cpp
m_customDataChannel.Close();
```

## <a name="see-also"></a>Consulte Também
* [Visão geral da comunicação remota do Holographic](holographic-remoting-overview.md)
* [escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs de Windows Mixed Reality](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de comunicação remota do Holographic usando APIs do OpenXR](holographic-remoting-create-remote-openxr.md)
* [Como escrever um aplicativo personalizado do Holographic Remoting Player](holographic-remoting-create-player.md)
* [Solução de problemas e limitações de comunicação remota do Holographic](holographic-remoting-troubleshooting.md)
* [Termos de licença de software de comunicação remota holográfica](/legal/mixed-reality/microsoft-holographic-remoting-software-license-terms)
* [Política de Privacidade da Microsoft](https://go.microsoft.com/fwlink/?LinkId=521839)