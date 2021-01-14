---
title: Adicionar um modo offline para tradução de fala em texto local
description: Conclua este curso para saber como adicionar o modo offline para a conversão local de fala em texto em aplicativos de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 06/27/2019
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, reconhecimento de fala, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: db495d6cdfa99721e68b4004535a5411bde9b17d
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98010076"
---
# <a name="2-adding-an-offline-mode-for-local-speech-to-text-translation"></a>2. Adicionar um modo offline para tradução de fala em texto local

Neste tutorial, você adicionará a capacidade de executar comandos usando o reconhecimento de fala do Azure, que permitirá que você faça algo com base na palavra ou na frase que você definir.

## <a name="objectives"></a>Objetivos

* Saiba como o reconhecimento de fala do Azure pode ser usado para executar comandos

## <a name="instructions"></a>Instruções

Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Palavra de Despertar do Lunarcom (Script)** ao objeto Lunarcom e configure-o da seguinte maneira:

* No campo **Palavra de Despertar**, insira uma frase adequada, por exemplo, _Ativar o terminal_.
* No campo **Palavra de Ignorar**, insira uma frase adequada, por exemplo, _Ignorar o terminal_.

![Editor do Unity com o componente de script Reconhecedor de Palavra de Despertar do Lunarcom realçado](images/mrlearning-speech/tutorial2-section1-step1-1.png)

> [!NOTE]
> O componente Reconhecedor de Palavra de Despertar do Lunarcom (Script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

Se agora você inserir o modo de jogo, como no tutorial anterior, o painel do terminal será habilitado por padrão, mas você poderá desabilitá-lo dizendo a Palavra de Ignorar, **Ignorar terminal**:

![Editor do Unity no modo de reprodução com o recurso de reconhecimento de fala em uso](images/mrlearning-speech/tutorial2-section1-step1-2.png)

E habilitá-la novamente dizendo a Palavra de Despertar, **Ativar terminal**:

![Editor do Unity no modo de reprodução com terminal ativo](images/mrlearning-speech/tutorial2-section1-step1-3.png)

> [!CAUTION]
> O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.

> [!TIP]
> Se você prever que frequentemente não poderá se conectar ao Azure, também poderá implementar comandos de fala usando o MRTK de acordo com as instruções [Usar comandos de fala](mr-learning-base-09.md).

## <a name="congratulations"></a>Parabéns

Você implementou comandos de fala da plataforma Azure. Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.

No próximo tutorial, você aprenderá a traduzir a fala usando a Tradução de Fala do Azure.

> [!div class="nextstepaction"]
> [Próximo tutorial: 3. Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure](mrlearning-speechSDK-ch3.md)
