---
ms.openlocfilehash: 12634c1fc18366e28a51688b19fc739ea69d37ec
ms.sourcegitcommit: 71c2a4884bd83599e35dd894771a5e43e951b574
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2021
ms.locfileid: "128184611"
---
# <a name="windows-mixed-reality"></a>[Windows Mixed Reality](#tab/wmr)

| Opção | Descrição |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | Usa o endereço IP (e a porta opcional) do dispositivo do HoloLens 2 para se conectar. Se nenhuma porta for fornecida, o padrão será 8265. |
| `-RemotingBitrate=<bitrate>` | (opcional) Padrão 8000. Taxa máxima de transferência de rede (KB/s). |
| `-HoloLensRemotingListen` | (opcional) Iniciar um servidor de escuta |
| `-HoloLensRemotingListenPort=<port>` | (opcional) Usa a porta a ser escutada. Usado para se conectar a um computador ou VM de um dispositivo HoloLens. |
| `-HoloLens1Remoting=<IP address>` | (preterido na 4.26) Usa o endereço IP do dispositivo do HoloLens 1 para se conectar |
| `-eyetracking=WindowsMixedRealityEyeTracker` | (opcional) Usar o rastreador ocular Windows Mixed Reality |

# <a name="openxr"></a>[OpenXR](#tab/openxr)

| Opção | Descrição |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | Usa o endereço IP (e a porta opcional, padrão 8265) do dispositivo de HoloLens 2 para se conectar ou a porta em que o aplicativo deve escutar conexões. |
| `-EnableAudio` | (opcional) Usar áudio do computador quando em comunicação remota  |
| `-Listen` | (opcional) Iniciar um servidor de escuta |
| `-RemotingBitrate=<bitrate>` | (opcional) Padrão 8000. Taxa máxima de transferência de rede (KB/s). |
| `-RemotingCodec=<codec>` | (opcional) Codec de conexão  |
| `-eyetracking=OpenXREyeTracker` | (opcional) Usar o rastreador ocular OpenXR |