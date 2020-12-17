---
ms.openlocfilehash: 212aa75ae91a7beebbfa609af6cc47106ba34b55
ms.sourcegitcommit: 0509cf6c57067cffd75a0189106e3369e9ecc5c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96855873"
---
# <a name="windows-mixed-reality"></a>[<span data-ttu-id="0fa0f-101">Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="0fa0f-101">Windows Mixed Reality</span></span>](#tab/wmr)

| <span data-ttu-id="0fa0f-102">Opção</span><span class="sxs-lookup"><span data-stu-id="0fa0f-102">Option</span></span> | <span data-ttu-id="0fa0f-103">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fa0f-103">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port>` | <span data-ttu-id="0fa0f-104">Usa o endereço IP (e a porta opcional) do dispositivo do HoloLens 2 para se conectar.</span><span class="sxs-lookup"><span data-stu-id="0fa0f-104">Takes the IP address (and optional port) of the HoloLens 2 device to connect to.</span></span> <span data-ttu-id="0fa0f-105">Se nenhuma porta for fornecida, o padrão será 8265.</span><span class="sxs-lookup"><span data-stu-id="0fa0f-105">If no port is provided, default to 8265.</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="0fa0f-106">(opcional) Padrão 8000.</span><span class="sxs-lookup"><span data-stu-id="0fa0f-106">(optional) Default 8000.</span></span> <span data-ttu-id="0fa0f-107">Taxa máxima de transferência de rede (KB/s).</span><span class="sxs-lookup"><span data-stu-id="0fa0f-107">Max network transfer rate (kb/s).</span></span> |
| `-HoloLensRemotingListen` | <span data-ttu-id="0fa0f-108">(opcional) Iniciar um servidor de escuta</span><span class="sxs-lookup"><span data-stu-id="0fa0f-108">(optional) Start a listen server</span></span> |
| `-HoloLensRemotingListenPort=<port>` | <span data-ttu-id="0fa0f-109">(opcional) Usa a porta a ser escutada.</span><span class="sxs-lookup"><span data-stu-id="0fa0f-109">(optional) Takes the port to listen on.</span></span> <span data-ttu-id="0fa0f-110">Usado para se conectar a um computador ou VM de um dispositivo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="0fa0f-110">Used for connecting to a PC or VM from a HoloLens device.</span></span> |
| `-HoloLens1Remoting=<IP address>` | <span data-ttu-id="0fa0f-111">(preterido na 4.26) Usa o endereço IP do dispositivo do HoloLens 1 para se conectar</span><span class="sxs-lookup"><span data-stu-id="0fa0f-111">(deprecated in 4.26) Takes the IP address of the HoloLens 1 device to connect to</span></span> |

# <a name="openxr"></a>[<span data-ttu-id="0fa0f-112">OpenXR</span><span class="sxs-lookup"><span data-stu-id="0fa0f-112">OpenXR</span></span>](#tab/openxr)

| <span data-ttu-id="0fa0f-113">Opção</span><span class="sxs-lookup"><span data-stu-id="0fa0f-113">Option</span></span> | <span data-ttu-id="0fa0f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fa0f-114">Description</span></span> |
| ------ | ----------- |
| `-HoloLensRemoting=<IP address:port or port>` | <span data-ttu-id="0fa0f-115">Usa o endereço IP (e a porta opcional, padrão 8265) do dispositivo de HoloLens 2 para se conectar ou a porta em que o aplicativo deve escutar conexões.</span><span class="sxs-lookup"><span data-stu-id="0fa0f-115">Takes the IP address (and optional port, default 8265) of the HoloLens 2 device to connect to, or the port on which the app should listen on for connections.</span></span> |
| `-EnableAudio` | <span data-ttu-id="0fa0f-116">(opcional) Usar áudio do computador quando em comunicação remota</span><span class="sxs-lookup"><span data-stu-id="0fa0f-116">(optional) Use audio from PC when remoting</span></span>  |
| `-Listen` | <span data-ttu-id="0fa0f-117">(opcional) Iniciar um servidor de escuta</span><span class="sxs-lookup"><span data-stu-id="0fa0f-117">(optional) Start a listen server</span></span> |
| `-RemotingBitrate=<bitrate>` | <span data-ttu-id="0fa0f-118">(opcional) Padrão 8000.</span><span class="sxs-lookup"><span data-stu-id="0fa0f-118">(optional) Default 8000.</span></span> <span data-ttu-id="0fa0f-119">Taxa máxima de transferência de rede (KB/s).</span><span class="sxs-lookup"><span data-stu-id="0fa0f-119">Max network transfer rate (kb/s).</span></span> |
| `-RemotingCodec=<codec>` | <span data-ttu-id="0fa0f-120">(opcional) Codec de conexão</span><span class="sxs-lookup"><span data-stu-id="0fa0f-120">(optional) Connection codec</span></span>  |