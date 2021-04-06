---
title: Como criar interfaces do usuário
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para criar interfaces do usuário estáticas e dinâmicas.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, pré-fabricados, hologramas, dicas de ferramentas
ms.localizationpriority: high
ms.openlocfilehash: 4400ce669863b719b409e11076ceb5689e21893e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982969"
---
# <a name="6-creating-user-interfaces"></a>6. Como criar interfaces do usuário

Neste tutorial, você aprenderá a criar uma interface do usuário simples usando os pré-fabricados de menu e de botão do MRTK junto com o componente TextMeshPro do Unity. Você também aprenderá a configurar os botões para disparar eventos e adicionar elementos de interface do usuário de dica de ferramenta dinâmica para fornecer ao usuário informações adicionais.

## <a name="objectives"></a>Objetivos

* Saber como organizar botões em uma coleção
* Saber como usar os pré-fabricados de menu do MRTK
* Saber como interagir com hologramas usando os botões e menus da interface do usuário
* Saber como adicionar elementos de texto
* Saber como gerar dicas de ferramentas em objetos dinamicamente

## <a name="creating-a-static-panel-of-buttons"></a>Criar um painel estático de botões

Na janela Hierarquia, clique com o botão direito do mouse no objeto **RoverExplorer** e selecione **Criar Vazio** para adicionar um objeto vazio como um filho do RoverExplorer, nomeie o objeto **Buttons** e configure o componente **Transformar** da seguinte maneira:

* **Posição**: X = -0,6, Y = 0,036, Z = -0,5
* **Rotação**: X = 90, Y = 0, Z = 0
* **Escala**: X = 1, Y = 1, Z = 1

![Unity com o objeto Buttons recém-criado selecionado e posicionado](images/mr-learning-base/base-06-section1-step1-1.png)

Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados**, clique e arraste o pré-fabricado **PressableRoundButton** no objeto **Buttons** e, em seguida, clique com o botão direito do mouse no PressableRoundButton e selecione **Duplicar** para criar uma cópia, repita até que você tenha um total de três objetos PressableRoundButton:

![Unity com os pré-fabricados PressableRoundButton recém-adicionados](images/mr-learning-base/base-06-section1-step1-2.png)

Na janela hierarquia, selecione o objeto **Buttons**, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **GridObjectCollection** e configure-o da seguinte maneira:

* **Tipo de Classificação**: Ordem do Filho
* **Layout**: Horizontal
* **Largura da Célula**: 0,2
* **Âncora**: Centro Esquerda

Em seguida, clique no botão **Atualizar Coleção** para atualizar a posição dos objetos filho do objeto Buttons:

![Objeto Buttons do Unity com o componente GridObjectCollection adicionado, configurado e aplicado](images/mr-learning-base/base-06-section1-step1-3.png)

Na janela Hierarquia, nomeie os botões **Dicas**, **Detalhar** e **Redefinir**.

Para cada botão, selecione o objeto filho **SeeItSayItLabel** > **TextMeshPro** e, em seguida, na janela Inspetor, altere o respectivo texto de componente **TextMeshPro – Texto** para corresponder aos nomes dos botões:

![Unity com os rótulos de texto dos botões configurados](images/mr-learning-base/base-06-section1-step1-4.png)

Quando tiver terminado, recolha os objetos filho do objeto Buttons.

Na janela Hierarquia, selecione o objeto do botão **Dicas** e, na janela Inspetor, configure o evento **Interactable.OnClick ()** da seguinte maneira:

* Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **PlacementHintsController** > **TogglePlacementHints ()** para definir essa função como a ação a ser executada quando o evento for disparado

![Unity com o evento OnClick do objeto de botão Hints configurado](images/mr-learning-base/base-06-section1-step1-5.png)

> [!TIP]
> O componente de interação é um contêiner all-in-one para facilitar a interação e a resposta à entrada de qualquer objeto. Um componente passível de interação engloba todos os tipos de entrada, incluindo toque, raios de mão, fala etc. e afunila essas interações em eventos e respostas de tema visual. Para saber como configurá-lo para diferentes tipos de entrada e personalizar o tema visual, veja o guia de [Interação](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Interactable.html) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/).

Na janela Hierarquia, selecione o objeto do botão **Detalhar** e, na janela Inspetor, configure o evento **Interactable.OnClick ()** da seguinte maneira:

* Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **ExplodedViewController** > **ToggleExplodedView ()** para definir essa função como a ação a ser executada quando o evento for disparado

![Unity com o evento OnClick do objeto de botão Detalhar configurado](images/mr-learning-base/base-06-section1-step1-6.png)

Pressione o botão Reproduzir para entrar no Modo de jogo e pressione e segure o botão barra de espaço para ativar a mão; e use o mouse para pressionar o botão **Dicas** para alternar a visibilidade dos objetos de dica de posicionamento:

![Modo de exibição dividida do Modo de reprodução do Unity com o botão Dicas recebendo um clique](images/mr-learning-base/base-06-section1-step1-7.png)

e o botão **Detalhar** para ativar e desativar a exibição detalhada:

![Modo de exibição dividida do Modo de reprodução do Unity com o botão Detalhar recebendo um clique](images/mr-learning-base/base-06-section1-step1-8.png)

## <a name="creating-a-dynamic-menu-that-follows-the-user"></a>Como criar um menu dinâmico que segue o usuário

Na janela Projeto, navegue até a pasta **Pacotes** > **Mixed Reality Toolkit Foundation** > **SDK** > **Recursos** > **UX** > **Pré-fabricados** > **Menus**, clique e arraste o pré-fabricado **NearMenu4x1** para a janela Hierarquia, defina a sua **Posição** de Transformação como X = 0, Y = -0,4, Z = 0 e configure-o da seguinte maneira:

* Verifique se o **Tipo de Destino Rastreado** do componente **SolverHandler** está definido como **Cabeça**
* Marque a caixa de seleção ao lado do componente Solucionador **RadialView** para que ele seja habilitado por padrão

![Unity com o pré-fabricado do menu próximo recém-adicionado selecionado](images/mr-learning-base/base-06-section2-step1-1.png)

Na janela Hierarquia, renomeie o objeto para **Menu** e, em seguida, expanda o seu objeto filho **ButtonCollection** para revelar os quatro botões:

![Unity com o objeto Menu selecionado e o objeto ButtonCollection expandido](images/mr-learning-base/base-06-section2-step1-2.png)

Renomeie o primeiro botão em ButtonCollection como Indicador e, na janela Inspetor, configure o componente Button Config Helper (Script) da seguinte maneira:

* Altere o **Texto do Rótulo Principal** para que ele corresponda ao nome do botão
* Atribua o objeto Indicador que parece com uma divisa ao campo Nenhum (Objeto)
* Na lista suspensa **Sem Função**, selecione **GameObject** > **SetActive (bool)** para definir essa função como a ação a ser executada quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **marcada**
* Altere o **Ícone** para o ícone "pesquisar"

![Unity com o Auxiliar de Configuração do Botão do objeto de botão Indicator configurado](images/mr-learning-base/base-06-section2-step1-3.png)

Para desabilitar o objeto Indicador de divisa, na janela Hierarquia, selecione o objeto Indicador que se parece com a divisa e, na janela Inspetor:

* Desmarque a caixa de seleção ao lado do nome para torná-la inativa por padrão
* Use o botão **Adicionar Componente** para adicionar o componente **Controlador de Indicador Direcional (Script)**

![Unity com o objeto Indicator selecionado e desabilitado e o componente DirectionalIndicatorController adicionado](images/mr-learning-base/base-06-section2-step1-4.png)

> [!NOTE]
> Agora, quando o aplicativo é iniciado, o Indicador de divisa é desabilitado por padrão e pode ser habilitado pressionando o botão Indicador.

Renomeie o segundo botão como **TapToPlace** e, na janela Inspetor, configure o componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Altere o **Texto do Rótulo Principal** para que ele corresponda ao nome do botão
* Atribua o objeto RoverExplorer > **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **marcada**
* Altere o **Ícone** para o ícone "mão com raio"

![Unity com o Auxiliar de Configuração do Botão do objeto de botão TapToPlace configurado](images/mr-learning-base/base-06-section2-step1-5.png)

Na janela Hierarquia, selecione o objeto **RoverAssembly** e, na janela Inspetor, configure o componente **Tocar para Posicionar (Script)** da seguinte maneira:

* Desmarque a caixa de seleção ao lado do nome para torná-la inativa por padrão
* Na seção de evento **On Placing Stopped ()** , clique no ícone **+** para adicionar um novo evento:
* Atribua o objeto RoverExplorer > **RoverAssembly** ao campo **Nenhum (Objeto)**
* Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado
* Verifique se a caixa de seleção do argumento está **desmarcada**

![Unity com o componente TapToPlace reconfigurado](images/mr-learning-base/base-06-section2-step1-6.png)

> [!NOTE]
> Agora, quando o aplicativo é iniciado, a funcionalidade Tocar para Posicionar é desabilitada por padrão e pode ser habilitada pressionando o botão Tocar para Posicionar. Além disso, quando o recurso tocar para posicionar for concluído, ele se desabilitará sozinho.

## <a name="adding-text-to-the-scene"></a>Como adicionar texto à cena

Na janela Hierarquia, clique com o botão direito do mouse no objeto **Tabela** e selecione **Objeto 3D** > **Texto – TextMeshPro** para adicionar um objeto de texto como um filho do objeto Table e, em seguida, na janela Inspetor, configure o componente **Transformação de Retângulo** da seguinte maneira:

* Altere a **Posição Y** para 1
* Altere a **Largura** para 1
* Altere a **Altura** para 1
* Altere a **Rotação X** para 90

![Unity com o objeto TextMeshPro recém-criado selecionado](images/mr-learning-base/base-06-section3-step1-1.png)

Em seguida, configure o componente **TextMeshPro – Texto** da seguinte maneira:

* Altere o **Texto** para o Explorador do Rover
* Altere o **Estilo da Fonte** para Negrito
* Altere o **Tamanho da Fonte** para 1
* Altere as Configurações Adicionais > **Margens** para 0,03

![Unity com o componente TextMeshPro configurado](images/mr-learning-base/base-06-section3-step1-2.png)

## <a name="adding-tooltips"></a>Como adicionar dicas de ferramenta

Na janela Projeto, navegue até a pasta **Pacotes** > **Mixed Reality Toolkit Foundation** > **SDK** > **Recursos** > **UX** > **Pré-fabricados** > **Dica de Ferramenta** para localizar os pré-fabricados de dica de ferramenta:

![Janela Projeto do Unity com a pasta Dicas de Ferramentas selecionada](images/mr-learning-base/base-06-section4-step1-1.png)

Na janela Hierarquia, expanda o objeto RoverExplorer > **RoverParts** e selecione todos os seus objetos filhos de peças do rover. Em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **ToolTipSpawner** e configurá-lo da seguinte maneira:

* Verifique se a caixa de seleção **Foco Habilitado** está marcada para exigir que o usuário olhe a peça para que a dica de ferramenta apareça
* Atribua o pré-fabricado **Dica de Ferramenta de Linha Simples** da janela Projeto ao campo **Pré-fabricado**
* Altere as Configurações de Substituição da Dica de Ferramenta > **Modo de Configurações** para **Substituir**
* Altere as Configurações de Substituição da Dica de Ferramenta > **Dinamizar Manualmente a Posição do Local Y** para **1,5**

![Unity com todos os objetos das partes da sonda selecionados e o componente ToolTipSpawner adicionado e configurado](images/mr-learning-base/base-06-section4-step1-2.png)

Na janela Hierarquia, selecione a primeira peça do Rover, RoverParts > **Camera_Part** e configure o componente **ToolTipSpawner** da seguinte maneira:

* Altere o **Texto da Dica de Ferramenta** para refletir o nome da peça, ou seja, **Câmera**

![Unity com o Camera ToolTipText configurado](images/mr-learning-base/base-06-section4-step1-3.png)

**Repita** essa etapa para cada um dos objetos da peça do Rover para configurar o componente **ToolTipSpawner** da seguinte maneira:

* Para o **Generator_Part**, altere o **Texto da Dica de Ferramenta** para **Gerador**
* Para o **Lights_Part**, altere o **Texto da Dica de Ferramenta** para **Luzes**
* Para o **UHFAntenna_Part**, altere o **Texto da Dica de Ferramenta** para o campo **Antena UHF**
* Para o **Spectrometer_Part**, altere o **Texto da Dica de Ferramenta** para **Espectrômetro**

Pressione o botão Reproduzir para entrar no Modo de jogo e pressione e segure o botão direito do mouse enquanto move o mouse até que o olhar esteja em uma das peças e a dica de ferramenta para essa peça seja exibida:

![Modo de exibição dividida do Modo de reprodução do Unity com a dica de ferramenta disparada pelo foco](images/mr-learning-base/base-06-section4-step1-4.png)

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu a criar uma interface do usuário simples usando os pré-fabricados de menu e de botão fornecidos do MRTK junto com o componente TextMeshPro do Unity e como configurar os botões para disparar eventos quando eles forem pressionados. Você também aprendeu como adicionar elementos de interface do usuário de dica de ferramenta dinâmicos para fornecer ao usuário informações adicionais.

> [!div class="nextstepaction"]
>[Próximo tutorial: 7. Interagir com objetos 3D](mr-learning-base-07.md)
