---
title: Introdução às Âncoras Espaciais do Azure
description: Conclua este curso para aprender a usar as Âncoras Espaciais do Azure para ancorar objetos em um aplicativo de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, âncoras espaciais do Azure
ms.localizationpriority: high
ms.openlocfilehash: 9c3ae23c39bf4d0b32d8a5d82716f93fee48b6db
ms.sourcegitcommit: fd1964ec6c645e8088ec120661f73739bb7775a9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/13/2021
ms.locfileid: "113656639"
---
# <a name="2-getting-started-with-azure-spatial-anchors"></a>2. Introdução às Âncoras Espaciais do Azure

Neste tutorial, você vai explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure e criar, carregar e baixá-las em apenas um dispositivo.

## <a name="objectives"></a>Objetivos

* Conheça os conceitos básicos do desenvolvimento com Âncoras Espaciais do Azure para o HoloLens 2
* Saber como criar âncoras espaciais e buscá-las no Azure

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Primeiro, siga [Como inicializar o seu projeto e implantar o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar o seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais do MRTK*
2. [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform)
3. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Como importar o Kit de ferramentas de Realidade Misturada e configurar o projeto do Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Criar e configurar a cena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e dar um nome adequado à cena, por exemplo, *AzureSpatialAnchors*

Em seguida, siga as instruções em [Alterar a Opção de Exibição de Reconhecimento Espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para verificar se o perfil de configuração do MRTK da sua cena é o **DefaultHoloLens2ConfigurationProfile** e alterar as opções de exibição da malha de reconhecimento espacial para **Oclusão**.

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>Instalação de pacotes incorporados do Unity e importação de ativos do tutorial

[!INCLUDE[](includes/installing-packages-for-asa.md)]

## <a name="preparing-the-scene"></a>Preparando a cena

Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureSpatialAnchors** > **Pré-fabricados** e clique e arraste os seguintes pré-fabricados para a janela Hierarquia para adicioná-los à sua cena:

* Pré-fabricados **ButtonParent**
* Pré-fabricados **DebugWindow**
* Pré-fabricados **Instructions**
* Pré-fabricados **ParentAnchor**

![Unity com os pré-fabricados recém-adicionados selecionados](images/mr-learning-asa/asa-02-section4-step1-1.png)

> [!TIP]
> Se você considerar que ícones grandes na sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Utensílio</a> para a posição de desligado, conforme mostrado na imagem acima.

Selecione o objeto **MixedRealityToolkit** na janela Hierarquia e use o botão **Adicionar Componente** na janela Inspetor para adicionar os seguintes componentes:

* AR Anchor Manager (Script)
* DisableDiagnosticsSystem (Script)

![Objeto MixedRealityToolkit do Unity com o AR Anchor Manager e os componentes DisableDiagnosticsSystem adicionados ](images/mr-learning-asa/asa-02-section4-step1-2.PNG)

> [!WARNING]
> Existe um problema conhecido com o ASA v2.9.0 e o v2.10.0-versão prévia.1 que exige que dois objetos adicionais sejam incluidos. Use o botão **Adicionar componente** na janela Inspetor para adicionar um Gerenciador de Câmera AR (script) e uma sessão AR (script) ao objeto **MixedRealityToolkit**. Não se esqueça de desabilitar a Câmera, que é criada automaticamente ao adicionar o Gerenciador de câmera AR (script), desmarcando a caixa de seleção ao lado do objeto Câmera na janela Inspetor. Esse problema será abordado na versão completa do ASA v2.10.0.
>

> [!NOTE]
> Quando você adiciona o componente AR Anchor Manager (script), o componente AR Session Origin (script) é adicionado automaticamente, pois ele é exigido pelo componente AR Anchor Manager (script).

## <a name="configuring-the-buttons-to-operate-the-scene"></a>Como configurar os botões para operar a cena

Nesta seção, você adicionará scripts à cena para criar uma série de eventos de botão que demonstram os conceitos básicos de como as âncoras locais e as Âncoras Espaciais do Azure se comportam em um aplicativo.

Na janela Hierarquia, expanda o objeto **ButtonParent** e selecione o primeiro objeto filho chamado **StartAzureSession**, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **StartAzureSession ()** para definir essa função como a ação a ser executada quando o evento for disparado

![Unity com o evento OnClick do botão StartAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-1.png)

Na janela Hierarquia, selecione o próximo botão denominado **StopAzureSession**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **StopAzureSession ()** para definir essa função como a ação a ser executada quando o evento for disparado

![Unity com o evento OnClick do botão StopAzureSession configurado](images/mr-learning-asa/asa-02-section5-step1-2.png)

Na janela Hierarquia, selecione o próximo botão denominado **CreateAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **CreateAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado
* Atribua o objeto **ParentAnchor** ao campo vazio **Nenhum (Objeto de Jogo)** para torná-lo o argumento para a função CreateAzureAnchor ()

![Unity com o evento OnClick do botão CreateAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-3.png)

Na janela Hierarquia, selecione o próximo botão denominado **RemoveLocalAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **RemoveLocalAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado
* Atribua o objeto **ParentAnchor** ao campo vazio **Nenhum (Objeto de Jogo)** para torná-lo o argumento para a função RemoveLocalAnchor ()

![Unity com o evento OnClick do botão RemoveLocalAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-4.png)

Na janela Hierarquia, selecione o próximo botão denominado **FindAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **FindAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado

![Unity com o evento OnClick do botão FindAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-5.png)

Na janela Hierarquia, selecione o próximo botão denominado **DeleteAzureAnchor**, em seguida, na janela Inspetor, configure o evento **On Click ()** do componente **Auxiliar de Configuração do Botão (Script)** da seguinte maneira:

* Atribua o objeto **ParentAnchor** como ouvinte para o evento On Click () arrastando-o da janela Hierarquia até o campo **Nenhum (objeto)**
* Na lista suspensa **Sem Função**, selecione **AnchorModuleScript** > **DeleteAzureAnchor ()** para definir essa função como a ação a ser executada quando o evento for disparado

![Unity com o evento OnClick do botão DeleteAzureAnchor configurado](images/mr-learning-asa/asa-02-section5-step1-6.png)

## <a name="connecting-the-scene-to-the-azure-resource"></a>Como conectar a cena ao recurso do Azure

Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, localize o componente **Gerenciador de Âncora Espacial (Script)** . Configure a seção **Credenciais** com as credenciais da conta das Âncoras Espaciais do Azure criada como parte dos [Pré-requisitos](mr-learning-asa-01.md#prerequisites) desta série de tutoriais:

* No campo **ID da Conta das Âncoras Espaciais**, cole a **ID da Conta** da sua conta das Âncoras Espaciais do Azure
* No campo **Chave de Conta das Âncoras Espaciais**, cole a **Chave de Acesso** primária ou secundária da sua conta das Âncoras Espaciais do Azure
* No campo **Domínio da Conta das Âncoras Espaciais**, cole o **Domínio da Conta** da sua conta das Âncoras Espaciais do Azure

![Unity com o Gerenciador de Âncora Espacial configurado](images/mr-learning-asa/asa-02-section6-step1-1.png)

## <a name="trying-the-basic-behaviors-of-azure-spatial-anchors"></a>Experimentando os comportamentos básicos das Âncoras Espaciais do Azure

As Âncoras Espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade delas, você precisa criar o projeto e implantar o aplicativo no seu dispositivo.

> [!TIP]
> Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo para o seu HoloLens 2](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

Quando o aplicativo for executado no seu dispositivo, siga as instruções na tela exibidas no painel Instruções do Tutorial de Âncora Espacial do Azure:

1. Mover o cubo para uma localização diferente
2. Iniciar a Sessão do Azure
3. Criar Âncora do Azure (cria uma âncora na localização do cubo).
4. Interromper a Sessão do Azure
5. Remover a Âncora Local (permite que o usuário mova o cubo)
6. Mover o cubo para outro lugar
7. Iniciar a Sessão do Azure
8. Localizar a Âncora do Azure (posiciona o cubo na localização da etapa 3)
9. Excluir a Âncora do Azure
10. Interromper a sessão do Azure

![Unity com o objeto Instructions selecionado](images/mr-learning-asa/asa-02-section7-step1-1.png)

> [!CAUTION]
> As Âncoras Espaciais do Azure usam a Internet para salvar e carregar os dados de âncora para garantir que o dispositivo esteja conectado à Internet.

## <a name="anchoring-an-experience"></a>Como ancorar uma experiência

Nas seções anteriores, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure. Usamos um cubo para representar e visualizar o objeto de jogo pai com a âncora anexada. Nesta seção, você aprenderá a ancorar uma experiência inteira colocando-a como um filho do objeto ParentAnchor.

Na janela Hierarquia, selecione o objeto **ParentAnchor** e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:

* Altere a **Escala X** para 1,1
* Altere a **Escala Z** para 1,1

![Unity com o objeto ParentAnchor selecionado, posicionado e escalado](images/mr-learning-asa/asa-02-section8-step1-1.png)

Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados** > **Rover** e, em seguida, clique e arraste o pré-fabricado **RoverExplorer_Complete** na janela Hierarquia para adicioná-lo à cena:

![Unity com o pré-fabricado RoverExplorer_Complete recém-adicionado](images/mr-learning-asa/asa-02-section8-step1-2.png)

Com o objeto RocketLauncher_Complete recém-adicionado ainda selecionado na janela Hierarquia, arraste-o sobre o objeto **ParentAnchor** para torná-lo um filho do objeto ParentAnchor:

![Unity com o objeto RoverExplorer_Complete definido como filho de ParentAnchor](images/mr-learning-asa/asa-02-section8-step1-3.png)

Se agora você recompilar o projeto e implantar o aplicativo no seu dispositivo, você poderá reposicionar toda a experiência do Explorador do Rover movendo o cubo redimensionado.

> [!TIP]
> Há uma variedade de fluxos de experiência do usuário para reposicionar experiências, incluindo o uso de um objeto de reposicionamento (como o cubo usado neste tutorial), o uso de um botão para alternar um controle de limites que envolve a experiência, o uso de utensílios de posição e rotação e muito mais.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu os conceitos básicos das Âncoras Espaciais do Azure. Este tutorial forneceu vários botões que permitem explorar as várias etapas necessárias para iniciar e parar uma sessão de Âncoras Espaciais do Azure. Além disso, para criar, carregar e baixar Âncoras Espaciais do Azure em um único dispositivo.

No próximo tutorial, você aprenderá a salvar as IDs de âncora do Azure no seu HoloLens 2 para recuperação, mesmo depois que o aplicativo for reiniciado, bem como a transferir IDs de âncora entre vários dispositivos para obter o alinhamento espacial.

> [!div class="nextstepaction"]
> [Próximo tutorial: 3. Salvar, recuperar e compartilhar Âncoras Espaciais do Azure](mr-learning-asa-03.md)
