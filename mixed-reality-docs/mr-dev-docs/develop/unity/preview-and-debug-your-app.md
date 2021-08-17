---
title: Visualizar e depurar seu aplicativo com o modo de execução e comunicação remota do Holographic
description: Usar a comunicação remota Holographic e o modo de reprodução para visualizar e depurar seu aplicativo
author: vtieto
ms.author: v-vtieto
ms.date: 08/12/2021
ms.topic: article
keywords: openxr, unity, hololens, hololens 2, realidade misturada, MRTK, realidade misturada Toolkit, realidade aumentada, realidade virtual, headsets de realidade misturada, aprendizado, tutorial, introdução, holographic comunicação remota, área de trabalho, visualização, depuração
ms.openlocfilehash: fe15d55037f09c47fe1e8a1dd996d0c69480f7b2
ms.sourcegitcommit: 820f2dfe98065298f6978a651f838de12620dd45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/14/2021
ms.locfileid: "122203830"
---
# <a name="preview-and-debug-your-app-using-holographic-remoting-and-play-mode"></a>Visualizar e depurar seu aplicativo usando a comunicação remota do Holographic e o modo de reprodução

Este artigo explica o seguinte caso de uso para a comunicação remota do Holographic: 

- **Você deseja visualizar e depurar seu aplicativo durante o processo de desenvolvimento**: você pode executar seu aplicativo localmente no editor do Unity em seu PC no modo de reprodução e transmitir a experiência para seu HoloLens. Isso fornece uma maneira de depurar rapidamente seu aplicativo sem criar e implantar um projeto completo. Chamamos esse tipo de aplicativo para um _aplicativo de visualização do modo de reprodução de comunicação remota Holographic_. as entradas do HoloLens--olhar, gesto, voz e mapeamento espacial – são enviadas para o PC, onde o conteúdo é renderizado em uma exibição de imersão virtual. Os quadros renderizados são enviados para a HoloLens. 

Para saber mais sobre a comunicação remota do Holographic, consulte [visão geral da comunicação remota do Holographic](../platform-capabilities-and-apis/holographic-remoting-overview.md)

observe que você também pode usar a comunicação remota do Holographic se [quiser que os recursos de um PC liguem seu aplicativo](use-pc-resources.md) em vez de depender do HoloLens recursos integrados.

## <a name="set-up-holographic-remoting"></a>Configurar a comunicação remota do Holographic

para usar a comunicação remota do Holographic, você precisa instalar o aplicativo de [Player de comunicação remota do Holographic](../platform-capabilities-and-apis/holographic-remoting-player.md) do Microsoft Store no seu HoloLens. Conforme explicado abaixo, depois de baixar e executar o aplicativo, você verá o número de versão e o endereço IP para se conectar. **Você precisará do v 2.4 ou posterior para trabalhar com o plug-in OpenXR**.

A comunicação remota do Holographic exige um PC rápido e uma conexão Wi-Fi. Você pode encontrar mais detalhes no artigo do player de comunicação remota do Holographic vinculado acima.

![Captura de tela do player de comunicação remota do Holographic em execução no HoloLens](images/openxr-features-img-01.png)

[!INCLUDE[](includes/unity-play-mode.md)]

## <a name="see-also"></a>Consulte Também
* [Player de Comunicação Remota Holográfica](../platform-capabilities-and-apis/holographic-remoting-player.md)
* [Tutorial: introdução ao PC Holographic de comunicação remota](tutorials/mr-learning-pc-holographic-remoting-01.md)
* [Tutorial: Criando um aplicativo de PC de comunicação remota Holographic](tutorials/mr-learning-pc-holographic-remoting-02.md)
