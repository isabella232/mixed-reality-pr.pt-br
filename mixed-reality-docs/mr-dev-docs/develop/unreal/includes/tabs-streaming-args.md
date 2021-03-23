---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "96855873"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| Opção | Descrição |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | Usa o endereço IP (e a porta opcional) do dispositivo do HoloLens 2 para se conectar. Se nenhuma porta for fornecida, o padrão será 8265. |
| `-RemotingBitrate=<bitrate>` | (opcional) Padrão 8000. Taxa máxima de transferência de rede (KB/s). |
| `-HoloLensRemotingListen` | (opcional) Iniciar um servidor de escuta |
| `-HoloLensRemotingListenPort=<port>` | (opcional) Usa a porta a ser escutada. Usado para se conectar a um computador ou VM de um dispositivo HoloLens. |
| `-HoloLens1Remoting=<IP address>` | (preterido na 4.26) Usa o endereço IP do dispositivo do HoloLens 1 para se conectar |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| Opção | Descrição |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | Usa o endereço IP (e a porta opcional, padrão 8265) do dispositivo de HoloLens 2 para se conectar ou a porta em que o aplicativo deve escutar conexões. |
| `-EnableAudio` | (opcional) Usar áudio do computador quando em comunicação remota  |
| `-Listen` | (opcional) Iniciar um servidor de escuta |
| `-RemotingBitrate=<bitrate>` | (opcional) Padrão 8000. Taxa máxima de transferência de rede (KB/s). |
| `-RemotingCodec=<codec>` | (opcional) Codec de conexão  |