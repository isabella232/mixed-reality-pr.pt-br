---
title: Visão geral de remoção holográfica
description: Saiba mais sobre o que é a Holographic Remoting e como ela pode beneficiar seu processo de desenvolvimento.
author: hferrone
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, Realidade Misturada Toolkit, realidade aumentada, realidade virtual, headsets de realidade misturada, saiba mais, tutorial, introdução, remota holográfica, área de trabalho, versão prévia
ms.openlocfilehash: 52b69f942797b1f0a6a9bcc5276a49d4d2cebba5
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122184597"
---
# <a name="holographic-remoting-overview"></a>Visão geral de remoção holográfica

Você pode usar a Holographic Remoting para transmitir conteúdo holográfico para seu HoloLens em tempo real. Há dois usos principais para isso e é importante entender a diferença:

1. (Unity ou Unreal): você deseja visualizar e **depurar** seu aplicativo durante o processo de desenvolvimento: você pode executar seu aplicativo localmente no editor do Unity em seu computador no Modo de Reprodução e transmitir a experiência para seu HoloLens. Isso fornece uma maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo. Chamamos esse tipo de aplicativo de aplicativo de visualização do modo de reprodução de remo _holográfica._

    - [Saiba mais sobre como visualizar e depurar seu aplicativo no Unity](../unity/preview-and-debug-your-app.md)

    - [Saiba mais sobre como visualizar e depurar seu aplicativo no Unreal](../unreal/unreal-streaming.md)

1. (Unity, Unreal ou C++): você deseja que os recursos de um pc aumentem seu aplicativo, em vez de depender dos recursos do **HoloLens** na placa: você pode criar e criar um aplicativo que tenha a funcionalidade de remoção holográfica. O usuário experimenta o aplicativo no HoloLens, mas o aplicativo realmente é executado em um pc, o que permite que ele aproveite os recursos mais poderosos do pc. Isso pode ser especialmente útil se seu aplicativo tiver modelos ou ativos de alta resolução e você não quiser que a taxa de quadros seja prejudicado. Chamamos esse tipo de aplicativo de _aplicativo remoto holográfico._

    - [Saiba mais sobre como usar recursos do PC no Unity](../unity/use-pc-resources.md)

    - [Saiba mais sobre como usar recursos de PC no Unreal](../unreal/unreal-streaming.md)

    - [Escrever um aplicativo remoto de remota de Windows Mixed Reality holográfico usando APIs de Windows Mixed Reality (C++)](holographic-remoting-create-remote-wmr.md)

    - [Escrever um aplicativo remoto de remoção holográfica usando APIs OpenXR (C++)](holographic-remoting-create-remote-openxr.md)

Em ambos os casos, as entradas do HoloLens – o olhar, o gesto, a voz e o mapeamento espacial – são enviadas para o COMPUTADOR, o conteúdo é renderizado em uma exibição imersiva virtual e os quadros renderizados são enviados para o HoloLens. 

## <a name="see-also"></a>Consulte Também

* [Player de Comunicação Remota Holográfica](holographic-remoting-player.md)
* [Tutorial: Introdução ao PC Holographic Remoting](../unity/tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Criando um aplicativo holográfico de computador de remoção](../unity/tutorials/mr-learning-pc-holographic-remoting-02.md)
