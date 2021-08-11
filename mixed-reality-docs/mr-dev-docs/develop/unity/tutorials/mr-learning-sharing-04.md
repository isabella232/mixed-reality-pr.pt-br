---
title: Compartilhar movimentações de objeto com vários usuários
description: Conclua este curso para aprender a compartilhar movimentos de objetos com vários usuários em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, funcionalidades de multiusuários, Photon, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure
ms.localizationpriority: high
ms.openlocfilehash: c9a37dd94083b796da6d5fba2727d739112e411b494af5882ad08525e733a722
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115200766"
---
# <a name="4-sharing-object-movements-with-multiple-users"></a>4. Compartilhar movimentações de objeto com vários usuários

Neste tutorial, você aprenderá a compartilhar os movimentos de objetos, de modo que todos os participantes de uma experiência compartilhada possam colaborar e exibir as interações uns dos outros.

## <a name="objectives"></a>Objetivos

* Configurar o projeto para compartilhar os movimentos de objetos
* Saber como criar um aplicativo básico de colaboração de vários usuários

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você vai preparar a cena adicionando o pré-fabricado do tutorial.

Na janela Hierarquia, expanda o objeto **MixedRealityPlayspace** e selecione o objeto filho **Câmera Principal** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Gerenciador de Câmera de RA (Script)** no objeto **Câmera Principal**:

![Unity com o componente Gerenciador de Câmera de RA parcialmente configurado](images/mr-learning-sharing/sharing-04-section1-step1-0.png)

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Pré-fabricados** e arraste o pré-fabricado **TableAnchor** sobre o objeto **SharedPlayground** na janela Hierarquia para adicioná-lo à cena como um filho do objeto SharedPlayground:

![Unity com o pré-fabricado TableAnchor recém-adicionado selecionado](images/mr-learning-sharing/sharing-04-section1-step1-1.png)

Na janela Hierarquia, verifique se o objeto **MixedRealityPlayspace** está expandido e se o objeto **TableAnchor** está selecionado. Arraste o componente **Câmera Principal** para o campo **Câmera** do componente **Origem da Sessão de RA** do **TableAnchor**:

![Unity com a atribuição de Câmera Principal de Origem da Sessão de RA configurada](images/mr-learning-sharing/sharing-04-section1-step1-2.png)

## <a name="configuring-pun-to-instantiate-the-objects"></a>Como configurar o PUN para criar uma instância dos objetos

Nesta seção, você vai configurar o projeto para usar a experiência do Explorador do Rover criada durante os [Tutoriais de introdução](mr-learning-base-01.md) e definir onde ele será instanciado.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.MultiUserCapabilities** > **Recursos**.

Na janela Hierarquia, expanda o objeto **NetworkLobby** e selecione o objeto filho **NetworkRoom**. Em seguida, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:

* Para o campo **Pré-fabricado do Rover Explorer**, atribua o pré-fabricado **RoverExplorer_Complete_Variant** da pasta Recursos

![Unity com o componente Sala do Photon parcialmente configurado](images/mr-learning-sharing/sharing-04-section2-step1-1.png)

Com o objeto filho **NetworkRoom** ainda selecionado, na janela Hierarquia, expanda o objeto **TableAnchor** e, na janela Inspetor, localize o componente **Sala do Photon (Script)** e configure-o da seguinte maneira:

* No campo **Localização do Explorador do Rover**, atribua o objeto filho TableAnchor > **Table** por meio da janela Hierarquia

![Unity com o componente Sala do Photon configurado](images/mr-learning-sharing/sharing-04-section2-step1-2.png)

## <a name="trying-the-experience-with-shared-object-movement"></a>Como testar a experiência com a movimentação de objetos compartilhados

Se você criar e implantar agora o projeto do Unity no HoloLens e, no Unity, selecionar o botão Reproduzir para entrar no Modo de jogo enquanto o aplicativo estiver em execução no HoloLens, verá o objeto se mover no Unity ao mover o objeto no HoloLens:

![Animação mostrando o Unity com os objetos em rede](images/mr-learning-sharing/sharing-04-section3-step1-1.gif)

## <a name="congratulations"></a>Parabéns

Você configurou com êxito o projeto para sincronizar os movimentos do objeto para que os usuários possam ver os objetos se moverem quando os outros usuários os moverem. No próximo tutorial, você implementará a funcionalidade para alinhar a experiência no mundo físico. Isso garantirá que os usuários vejam uns aos outros na sua localização física real e, portanto, os objetos aparecerão na mesma posição física e rotação para todos os usuários.

> [!div class="nextstepaction"]
> [Próximo tutorial: 5. Integrar âncoras espaciais do Azure a uma experiência compartilhada](mr-learning-sharing-05.md)
