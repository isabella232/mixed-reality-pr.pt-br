---
title: Visão geral de remoção holográfica
description: Saiba mais sobre o que a Holographic Remoting e como ela pode beneficiar seu processo de desenvolvimento.
author: hferrone
ms.author: v-vtieto
ms.date: 07/26/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, realidade misturada Toolkit, realidade aumentada, realidade virtual, headsets de realidade misturada, learn, tutorial, introdução, remota holográfica, área de trabalho, versão prévia
ms.openlocfilehash: 6eb3b9e9fe8811ab4666ef1beda0e48668bedbe6
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757378"
---
# <a name="holographic-remoting-overview"></a>Visão geral de remoção holográfica

Quando você adiciona suporte para o Holographic Rendering ao seu aplicativo ou jogo de computador, ele permite que o aplicativo transmitir conteúdo holográfico para seu HoloLens 2 em tempo real. Essa é uma ótima maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo. O olhar, o gesto, a voz e a entrada de mapeamento espacial são enviados do seu HoloLens 2 para o computador, o conteúdo é renderizado em uma exibição imersiva virtual usando os maiores recursos do sistema do PC e os quadros renderizados são então enviados de volta ao seu HoloLens 2. A Holographic Remoting também está disponível para headsets Windows Mixed Reality imersivos.

Você adiciona o Holographic Remoting ao aplicativo UWP ou área de trabalho por meio de um pacote NuGet e a conexão é feita usando o Wi-Fi padrão. É necessário um código adicional que trata a conexão e renderiza em uma exibição imersiva. Uma conexão de remoting típica terá até 50 ms de latência. Seu dispositivo exibe o conteúdo transmitido usando um aplicativo "player" que pode relatar a latência em tempo real.

Se você for um desenvolvedor do Unity, também poderá usar a Holographic Remoting executando seu aplicativo no Editor do Unity no modo Play.

## <a name="see-also"></a>Consulte Também
* [Player de Comunicação Remota Holográfica](holographic-remoting-player.md)
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs Windows Mixed Reality holográficas](holographic-remoting-create-remote-wmr.md)
* [Escrevendo um aplicativo remoto de remoção holográfica usando APIs OpenXR](holographic-remoting-create-remote-openxr.md)
* [Tutorial: Introdução ao PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Criando um aplicativo holográfico de computador de remoção](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
