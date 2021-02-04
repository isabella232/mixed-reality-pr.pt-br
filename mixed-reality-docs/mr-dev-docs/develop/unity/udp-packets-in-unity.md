---
title: Pacotes UDP em aplicativos de UWP do Unity
description: Saiba como configurar um aplicativo UWP do Unity para enviar e receber pacotes UDP em uma rede segura.
author: hferrone
ms.author: v-hferrone
ms.date: 02/3/2021
ms.topic: article
keywords: UDP, UWP, Unity, pacotes UDP, soquete, servidor cliente, ponto de extremidade, rede, máquina remota, datagramsocket, exemplo, .net
ms.openlocfilehash: e4fbdc12a1f7fbca44e14f6ace89ef791a09608f
ms.sourcegitcommit: 8647702638f7600c51df1d89d76c761b52bdf0d7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/04/2021
ms.locfileid: "99566970"
---
# <a name="udp-packets-in-unity-uwp-apps"></a><span data-ttu-id="84a50-104">Pacotes UDP em aplicativos de UWP do Unity</span><span class="sxs-lookup"><span data-stu-id="84a50-104">UDP packets in Unity UWP apps</span></span>

<span data-ttu-id="84a50-105">Você pode configurar seus aplicativos da Unity Plataforma Universal do Windows (UWP) para receber pacotes UDP com a ajuda de um cliente de soquete UDP e servidor.</span><span class="sxs-lookup"><span data-stu-id="84a50-105">You can setup your Universal Windows Platform (UWP) Unity apps to receive UDP packets with the help of a UDP socket client and server.</span></span> <span data-ttu-id="84a50-106">Os soquetes UDP não mantêm a conexão em ambos os pontos de extremidade, portanto, eles são uma solução rápida e simples para rede entre máquinas remotas.</span><span class="sxs-lookup"><span data-stu-id="84a50-106">UDP sockets don't maintain connection on both endpoints, so they're a fast and simple solution for networking between remote machines.</span></span> <span data-ttu-id="84a50-107">No entanto, você será responsável por verificar se os pacotes são obtidos no destino, pois os soquetes UDP não fazem isso automaticamente.</span><span class="sxs-lookup"><span data-stu-id="84a50-107">However, you'll be responsible for checking if the packets get to their destination, as UDP sockets don't do that automatically.</span></span>

## <a name="setup"></a><span data-ttu-id="84a50-108">Instalação</span><span class="sxs-lookup"><span data-stu-id="84a50-108">Setup</span></span>

<span data-ttu-id="84a50-109">Abra seus projetos do HoloLens manifest.jsno arquivo e verifique se você habilitou:</span><span class="sxs-lookup"><span data-stu-id="84a50-109">Open your projects HoloLens manifest.json file and make sure you've enabled:</span></span>
* <span data-ttu-id="84a50-110">**Internet (servidor de & de cliente)**</span><span class="sxs-lookup"><span data-stu-id="84a50-110">**Internet (Client & Server)**</span></span> 
* <span data-ttu-id="84a50-111">**Redes privadas (cliente & Server)**.</span><span class="sxs-lookup"><span data-stu-id="84a50-111">**Private Networks (Client & Server)**.</span></span>

## <a name="build-your-socket-client-and-server"></a><span data-ttu-id="84a50-112">Criar seu cliente de soquete e servidor</span><span class="sxs-lookup"><span data-stu-id="84a50-112">Build your socket client and server</span></span> 

<span data-ttu-id="84a50-113">Siga as instruções para [criar um cliente e um servidor de soquete UDP básico](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span><span class="sxs-lookup"><span data-stu-id="84a50-113">Follow the instructions for [building a basic UDP socket client and server](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server).</span></span> <span data-ttu-id="84a50-114">Você usará a classe [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) para enviar e receber dados por UDP e formar um cliente e servidor de eco.</span><span class="sxs-lookup"><span data-stu-id="84a50-114">You'll be using the [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) class to send and receive data over UDP and form an echo client and server.</span></span> <span data-ttu-id="84a50-115">Também é recomendável ler as seções de outros recursos neste artigo, pois elas se aplicam a casos de uso mais personalizados e complexos.</span><span class="sxs-lookup"><span data-stu-id="84a50-115">We also recommend reading through the other resource sections in this article, as they apply to more customized and complex use cases.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="84a50-116">Se você estiver tendo problemas para enviar pacotes UDP do PC para o PC, verifique se a rede permite essas operações.</span><span class="sxs-lookup"><span data-stu-id="84a50-116">If you're having trouble sending UDP packets from PC to PC, check that your network allows these operations.</span></span> <span data-ttu-id="84a50-117">Se sua rede estiver bloqueando os pacotes UDP de alguma forma, o dispositivo do HoloLens não poderá ouvi-los.</span><span class="sxs-lookup"><span data-stu-id="84a50-117">If your network is blocking the UDP packets in any way, your HoloLens device won't be able to listen for them.</span></span>

<span data-ttu-id="84a50-118">Você pode baixar um aplicativo de exemplo DatagramSocket UDP completo do link abaixo:</span><span class="sxs-lookup"><span data-stu-id="84a50-118">You can download a complete DatagramSocket UDP sample app from the link below:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="84a50-119">Instalar as ferramentas</span><span class="sxs-lookup"><span data-stu-id="84a50-119">Install the tools</span></span>](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a><span data-ttu-id="84a50-120">Veja também</span><span class="sxs-lookup"><span data-stu-id="84a50-120">See also</span></span> 
* [<span data-ttu-id="84a50-121">Experimentos com hologramas compartilhados e armazenamento de BLOBs do Azure/multicast de UDP</span><span class="sxs-lookup"><span data-stu-id="84a50-121">Experiments with Shared Holograms and Azure Blob Storage/UDP Multicasting</span></span>](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)