---
title: Como conectar vários usuários
description: Conclua este curso para aprender a conectar vários usuários em um aplicativo de realidade misturada do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, funcionalidades de multiusuários, Photon, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure
ms.localizationpriority: high
ms.openlocfilehash: 207c451ee616ee4065e948ca78c17ad59f7dd190
ms.sourcegitcommit: cf8df1720ddb8236207ab581bc149edcc76e6199
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114702466"
---
# <a name="3-connecting-multiple-users"></a>3. Como conectar vários usuários

Neste tutorial, você aprenderá a conectar vários usuários como parte de uma experiência compartilhada ao vivo. Ao final do tutorial, você estará apto a executar o aplicativo em vários dispositivos e fazer com que cada usuário veja o avatar dos outros usuários se mover em tempo real.

## <a name="objectives"></a>Objetivos

* Saiba como conectar vários usuários em uma experiência compartilhada

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:

* Pré-fabricado **NetworkLobby**
* Pré-fabricado **SharedPlayground**

![Unity com os pré-fabricados NetworkLobby e SharedPlayground recém-adicionados selecionados](images/mr-learning-sharing/sharing-03-section1-step1-1.png)

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureSpatialAnchors** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:

* **DebugWindow** pré-fabricado

![Unity com o pré-fabricado DebugWindow recém-adicionado selecionado](images/mr-learning-sharing/sharing-03-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-user-prefab"></a>Como configurar o PUN para criar uma instância do pré-fabricado do usuário

Nesta seção, o projeto será configurado para usar o pré-fabricado do PhotonUser.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:

* Ao campo **Pré-fabricado do Usuário do Photon**, atribua o pré-fabricado **PhotonUser** da pasta Recursos

![Unity com o componente Sala do Photon parcialmente configurado](images/mr-learning-sharing/sharing-03-section3-step1-1.png)

## <a name="trying-the-experience-with-multiple-users"></a>Como testar a experiência com vários usuários

Se você criar e implantar agora o projeto do Unity no HoloLens, então, no Unity, entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá a movimentação do avatar do usuário do HoloLens quando mover a cabeça (HoloLens):

![Animação mostrando o Unity com os usuários em rede](images/mr-learning-sharing/sharing-03-section4-step1-1.gif)

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

> [!CAUTION]
> O aplicativo precisa se conectar ao Photon; portanto, verifique se o computador/o dispositivo está conectado à Internet.

## <a name="congratulations"></a>Parabéns

Você configurou com êxito seu projeto para permitir que vários usuários se conectem à mesma experiência e vejam os movimentos uns dos outros. No próximo tutorial, você implementará uma funcionalidade para que os movimentos dos objetos também sejam compartilhados entre vários dispositivos.

> [!div class="nextstepaction"]
> [Próximo tutorial: 4. Compartilhar movimentações de objeto com vários usuários](mr-learning-sharing-04.md)
