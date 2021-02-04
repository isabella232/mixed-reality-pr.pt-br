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
# <a name="udp-packets-in-unity-uwp-apps"></a>Pacotes UDP em aplicativos de UWP do Unity

Você pode configurar seus aplicativos da Unity Plataforma Universal do Windows (UWP) para receber pacotes UDP com a ajuda de um cliente de soquete UDP e servidor. Os soquetes UDP não mantêm a conexão em ambos os pontos de extremidade, portanto, eles são uma solução rápida e simples para rede entre máquinas remotas. No entanto, você será responsável por verificar se os pacotes são obtidos no destino, pois os soquetes UDP não fazem isso automaticamente.

## <a name="setup"></a>Instalação

Abra seus projetos do HoloLens manifest.jsno arquivo e verifique se você habilitou:
* **Internet (servidor de & de cliente)** 
* **Redes privadas (cliente & Server)**.

## <a name="build-your-socket-client-and-server"></a>Criar seu cliente de soquete e servidor 

Siga as instruções para [criar um cliente e um servidor de soquete UDP básico](https://docs.microsoft.com/windows/uwp/networking/sockets#build-a-basic-udp-socket-client-and-server). Você usará a classe [DatagramSocket](https://docs.microsoft.com/uwp/api/Windows.Networking.Sockets.DatagramSocket) para enviar e receber dados por UDP e formar um cliente e servidor de eco. Também é recomendável ler as seções de outros recursos neste artigo, pois elas se aplicam a casos de uso mais personalizados e complexos. 

> [!IMPORTANT]
> Se você estiver tendo problemas para enviar pacotes UDP do PC para o PC, verifique se a rede permite essas operações. Se sua rede estiver bloqueando os pacotes UDP de alguma forma, o dispositivo do HoloLens não poderá ouvi-los.

Você pode baixar um aplicativo de exemplo DatagramSocket UDP completo do link abaixo:

> [!div class="nextstepaction"]
> [Instalar as ferramentas](https://docs.microsoft.com/samples/microsoft/windows-universal-samples/datagramsocket/)

## <a name="see-also"></a>Veja também 
* [Experimentos com hologramas compartilhados e armazenamento de BLOBs do Azure/multicast de UDP](https://mtaulty.com/2017/12/29/experiments-with-shared-holograms-and-azure-blob-storage-udp-multicasting-part-1/)