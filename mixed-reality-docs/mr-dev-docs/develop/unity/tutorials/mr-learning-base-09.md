---
title: Usando comandos de fala
description: Este curso mostra como configurar, criar e usar comandos de fala em seus aplicativos de realidade misturada com o MRTK (Kit de Ferramentas de Realidade Misturada).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, comandos de fala, entrada de voz
ms.localizationpriority: high
ms.openlocfilehash: 3aea23d5a259e555f47ca9ea41d77f345c977aeb
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982919"
---
# <a name="9-using-speech-commands"></a>9. Usando comandos de fala

Neste tutorial, você aprenderá a criar comandos de fala e a controlá-los globalmente. Você também aprenderá a controlar os comandos de fala locais que exigem que o usuário examine o objeto que controla o comando de fala.

## <a name="objectives"></a>Objetivos

* Saber como criar comandos de fala
* Aprender a controlar comandos de fala globalmente e localmente

[!INCLUDE[](includes/ensuring-microphone-capabality.md)]

## <a name="creating-speech-commands"></a>Criando comandos de fala

Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, selecione a guia MixedRealityToolkit > **Entrada** e execute as seguintes etapas:

* Expanda a seção **Fala**
* Clone o **DefaultMixedRealitySpeechCommandsProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealitySpeechCommandsProfile_
* Verifique se o **Comportamento de Inicialização** está definido como **Iniciar Automaticamente**

![Criando comandos de fala](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do MRTK](mr-learning-base-03.md).

Na seção Fala > **Comandos de Fala**, clique no botão **+ Adicionar um Novo Comando de Fala** quatro vezes para adicionar quatro novos comandos de fala à lista de comandos de fala existentes e, em seguida, nos campos **Palavra-Chave** digite as seguintes frases:

* Habilitar Indicador
* Habilitar Toque para Posicionar
* Habilitar controle de limites
* Desabilitar controle de limites

![Como adicionar novos comandos de fala](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> Se o computador não tiver um microfone, atribua um KeyCode aos comandos de fala, o que lhe permitirá dispará-los quando a tecla correspondente for pressionada.

## <a name="controlling-speech-commands"></a>Controlar comandos de fala

Na janela Projeto, navegue até a pasta **Pacote** > **Mixed Reality Toolkit Foundation** > **SDK** > **Recursos** > **UX** > **Pré-fabricados** > **Dica de Ferramenta** para localizar os pré-fabricados da dica de ferramenta:

![Como abrir a pasta de dica de ferramenta](images/mr-learning-base/base-09-section3-step1-1.png)

Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Criar Vazio** para adicionar um objeto vazio à sua cena.

Nomeie o objeto como **SpeechInputHandler_Global** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **SpeechInputHandler** e configure-o da seguinte maneira:

* **Desmarque** a caixa de seleção **Foco É Necessário** para que os usuários não precisem examinar o objeto com o componente SpeechInputHandler para disparar o comando de fala
* Na janela Projeto, atribua o pré-fabricado **SpeechConfirmation Tooltip** ao campo **Speech Confirmation Tooltip Prefab**, para que esse pré-fabricado seja exibido quando um comando de fala for reconhecido

![Como configurar o componente de manipulador de entrada de fala](images/mr-learning-base/base-09-section3-step1-2.png)

No componente SpeechInputHandler, clique no ícone de pequeno **+** três vezes para adicionar três elementos de palavra-chave:

![Como adicionar elementos de palavra-chave ao manipulador de entrada de fala](images/mr-learning-base/base-09-section3-step1-3.png)

Expanda **Elemento 0** e configure-o da seguinte maneira:

* No campo **Palavra-chave**, digite **Habilitar Indicador** para fazer referência ao comando de fala Habilitar Indicador criado na seção anterior
* Clique no ícone pequeno **+** para adicionar um evento
* Na janela Hierarquia, atribua o objeto **Indicador** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **GameObject** > **SetActive (bool)** para definir essa função como a ação a ser executada quando o evento for disparado
* Verifique se a caixa de seleção de argumento está **marcada**

![Configurar o elemento de palavra-chave 0](images/mr-learning-base/base-09-section3-step1-4.png)

Expanda **Elemento 1** e configure-o da seguinte maneira:

* No campo **Palavra-chave**, digite **Habilitar Controle de Limites** para fazer referência ao comando Habilitar Controle de Limites criado na seção anterior
* Clique no ícone pequeno **+** para adicionar um evento
* Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **BoundsControl** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção de argumento está **marcada**
* Clique no ícone pequeno **+** para adicionar outro evento
* Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção de argumento está **marcada**

![Configurar o elemento de palavra-chave 1](images/mr-learning-base/base-09-section3-step1-5.png)

Expanda **Elemento 2** e configure-o da seguinte maneira:

* No campo **Palavra-chave**, digite **Desabilitar Controle de Limites** para fazer referência ao comando Desabilitar Controle de Limites criado na seção anterior
* Clique no ícone pequeno **+** para adicionar um evento
* Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **BoundsControl** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**
* Clique no ícone pequeno **+** para adicionar outro evento
* Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**

![Configurar o elemento de palavra-chave 2](images/mr-learning-base/base-09-section3-step1-6.png)

Na janela hierarquia, selecione o objeto RoverExplorer > **RoverAssembly** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **SpeechInputHandler** e configure-o da seguinte maneira:

* Verifique se a caixa de seleção **Foco É Necessário** está **marcada** para que os usuários precisem examinar o objeto com o componente SpeechInputHandler, ou seja, o RoverAssembly, para disparar o comando de fala
* Na janela Projeto, atribua o pré-fabricado **SpeechConfirmation Tooltip** ao campo **Speech Confirmation Tooltip Prefab**, para que esse pré-fabricado seja exibido quando um comando de fala for reconhecido

![Adicionar o manipulador de entrada de fala ao Rover Assembly](images/mr-learning-base/base-09-section3-step1-7.png)

No componente SpeechInputHandler, clique no ícone pequeno **+** para adicionar um elemento de palavra-chave. Expanda o elemento recém-criado e configure-o da seguinte maneira:

* No campo **Palavra-chave**, digite **Habilitar Toque para Posicionar** para fazer referência ao comando de fala Habilitar Toque para Posicionar criado na seção anterior
* Clique no ícone pequeno **+** para adicionar um evento
* Na janela Hierarquia, atribua o objeto em si, ou seja, o mesmo objeto **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção de argumento está **marcada**

![Configurar o manipulador de entrada de fala no Rover Assembly](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar comandos de fala e a controlá-los globalmente. Você também aprendeu a controlar os comandos de fala locais que exigem que o usuário examine o objeto que controla o comando de fala.

Isso também conclui a série de [Tutoriais de introdução](mr-learning-base-01.md). Por meio desses tutoriais, você criou com êxito uma experiência de realidade misturada completa do zero usando o MRTK.

Na próxima duas série de tutoriais, [Tutoriais de Âncoras Espaciais do Azure](mr-learning-asa-01.md) e [Tutoriais de funcionalidades de vários usuários](mr-learning-sharing-01.md), você aprenderá primeiro a integrar Âncoras Espaciais do Azure em seu projeto para ancorar a experiência do Rover Explorer criada no mundo real. Em seguida, você aprenderá a adicionar recursos de vários usuários ao seu projeto para compartilhar movimentações de usuários e objetos em tempo real.

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity que apresentamos, sua próxima tarefa é conhecer os principais blocos de construção de aplicativos de Realidade Misturada.

> [!div class="nextstepaction"]
> [Interações básicas](../../../out-of-scope/mrtk-101.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](../unity-development-overview.md#1-getting-started) a qualquer momento.