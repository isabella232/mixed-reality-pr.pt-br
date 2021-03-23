---
title: Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure
description: Neste curso, você aprenderá a adicionar a tradução de fala dos Serviços Cognitivos do Azure em aplicativos de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure, reconhecimento de fala, Windows 10, tradução de fala
ms.localizationpriority: high
ms.openlocfilehash: bcc966b63f4c3e5bb9e6d6a38dc7f0312b288402
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590138"
---
# <a name="3-adding-the-azure-cognitive-services-speech-translation-component"></a>3. Adicionar o componente de tradução de fala dos Serviços Cognitivos do Azure

Neste tutorial, você adicionará a tradução de fala ao seu projeto, o que permitirá que você traduza e transcreva sua fala em três idiomas diferentes.

## <a name="objectives"></a>Objetivos

* Saiba como integrar a Tradução de Fala do Azure

## <a name="instructions"></a>Instruções

Na janela Hierarquia, selecione o objeto **Lunarcom** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Reconhecedor de Tradução do Lunarcom (Script)** ao objeto Lunarcom e configure-o da seguinte maneira:

* Altere o **Idioma de Destino** para um idioma de sua escolha, por exemplo, _Alemão_

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-1.png)

> [!NOTE]
> O componente Reconhecedor de Tradução do Lunarcom (Script) não faz parte do MRTK. Ele foi fornecido com os ativos deste tutorial.

Se agora você entrar no modo de Jogo, poderá testar a tradução de fala primeiro pressionando o botão de satélite. Em seguida, supondo que o computador tenha um microfone, quando você disser algo, sua fala será traduzida para o idioma escolhido e transcrita no painel do terminal:

![mrlearning-speech](images/mrlearning-speech/tutorial3-section1-step1-2.png)

> [!CAUTION]
> O aplicativo precisa se conectar ao Azure, portanto, verifique se o computador/dispositivo está conectado à Internet.

## <a name="congratulations"></a>Parabéns

Agora, seu projeto pode traduzir com êxito as palavras que você fala em vários idiomas diferentes. Execute o aplicativo em seu dispositivo para garantir que o recurso esteja funcionando corretamente.

> [!div class="nextstepaction"]
> [Próximo tutorial: 4. Configurar a intenção e o reconhecimento vocal natural](mrlearning-speechSDK-ch4.md)
