---
title: Serviços de Nuvem do Azure para HoloLens 2
description: Conclua este curso para aprender a implementar diversos serviços do Azure em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: azure, realidade misturada, unity, tutorial, hololens, hololens 2, armazenamento de blobs do azure, armazenamento de tabelas do azure, âncoras espaciais do azure, azure bot framework, serviços de nuvem do azure, visão personalizada do azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 84eb1555d0020eebe9de440fcdbdd58ac17875ab417a209ea083664ab17fbfd8
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115226938"
---
# <a name="1-azure-cloud-services-for-hololens-2"></a>1. Serviços de Nuvem do Azure para HoloLens 2

Bem-vindo(a) a esta série de tutoriais voltados para colocar serviços de **Nuvem do Azure** em um aplicativo do **HoloLens 2**. Nesta série de tutoriais em cinco partes, você aprenderá a integrar vários serviços de **Nuvem do Azure** em um projeto **Unity** para o **HoloLens 2**. Ao passar em cada capítulo, você adicionará novos serviços de **Nuvem do Azure** para expandir os recursos do aplicativo e a experiência do usuário, aprendendo ao mesmo tempo os conceitos básicos de cada serviço de **Nuvem do Azure**.

> [!NOTE]
> Esta série de tutoriais se concentrará no **HoloLens 2** mas, devido à natureza multiplataforma do Unity, a maioria dos seus aprendizados também se aplicará a aplicativos para Desktop e Smartphone.

Neste primeiro tutorial, você conhecerá as metas da série e de cada serviço de nuvem do Azure que você usará, além de configurar o projeto inicial do Unity.

No segundo tutorial, [Integrar o Armazenamento do Azure](mr-learning-azure-02.md), você começará integrando o Armazenamento do Azure como a solução de persistência para o aplicativo de demonstração. Você também conhecerá as diferenças entre o Armazenamento de Blobs e o Armazenamento de Tabela, preparará os recursos de projeto necessários e configurará a cena. Por fim, você aprenderá a verificar as operações de leitura, atualização e exclusão de dados.

Continuando com o terceiro tutorial, [Integração da Visão Personalizada do Azure](mr-learning-azure-03.md), você usará a Visão Personalizada do Azure para treinar e detectar imagens no aplicativo do HoloLens 2. O capítulo começa com a configuração de seu próprio recurso de Visão Personalizada do Azure, preparando os componentes da cena e entrando em ação treinando e detectando suas próprias imagens de dentro do aplicativo.

Em seguida, você avançará para o quarto tutorial, [Integração de Âncoras Espaciais do Azure](mr-learning-azure-04.md), com a exploração do serviço Âncoras Espaciais do Azure para salvar e encontrar locais, aprender os principais conceitos, preparar os recursos necessários, configurar a cena e começar a usar o novo recurso no aplicativo.

Com o quinto tutorial, [Integração do Serviço de Bot do Azure com o LUIS](mr-learning-azure-05.md), você finaliza fornecendo ao aplicativo um novo método de interação do usuário: idioma natural! Esse recurso será realizado usando o Azure Bot Framework junto com o LUIS (Reconhecimento Vocal). Este capítulo final ensina os conceitos básicos do Serviço de Bot do Azure e para acelerar o processo, você usará o Bot Framework Composer como uma solução sem código. Depois que o bot for criado, você o integrará à cena e fará com que ele seja executado com o estágio final do aplicativo do HoloLens 2.

## <a name="application-goals"></a>Metas do aplicativo

Nesta série de tutoriais, você criará um aplicativo do **HoloLens 2** que poderá detectar objetos em imagens e encontrar seu local espacial. Para definir um idioma de domínio, essas entidades passarão a ser chamadas de **Objeto Rastreado**.
O usuário pode criar um **Objeto Rastreado** para associar um conjunto de imagens por meio da pesquisa visual computacional e/ou de um local espacial. Todos os dados devem ser persistidos na nuvem. Além disso, alguns aspectos do aplicativo serão controlados opcionalmente pelo idioma natural por meio de um bot.

### <a name="features"></a>Recursos

* Gerenciamento básico de dados e imagens
* Treinamento e detecção de imagem
* Armazenamento de um local espacial e diretrizes para ele
* Assistente de bot para usar alguns recursos por meio de linguagem natural

## <a name="azure-cloud-services"></a>Serviços de Nuvem do Azure

Você usará os seguintes serviços de **Nuvem do Azure** para implementar os recursos acima:

### <a name="azure-storage"></a>Armazenamento do Azure

Você usará o [Armazenamento do Azure](https://azure.microsoft.com/services/storage/) para a solução de persistência. Ele permite que você armazene dados em uma tabela e carregue binários grandes, como imagens.

### <a name="azure-custom-vision"></a>Visão Personalizada do Azure

Com a [Visão Personalizada do Azure](https://azure.microsoft.com/services/cognitive-services/custom-vision-service/) (parte dos [Serviços Cognitivos do Azure](https://azure.microsoft.com/services/cognitive-services/)), você pode associar um conjunto de imagens a *Objetos Rastreados*, treinar um modelo de machine learning no conjunto e detectar o *Objeto Rastreado*.

### <a name="azure-spatial-anchors"></a>Âncoras Espaciais do Azure

Para armazenar o local de um *Objeto Rastreado* e fornecer instruções guiadas para encontrá-lo, você usa [Âncoras Espaciais do Azure](https://azure.microsoft.com/services/spatial-anchors/).

### <a name="azure-bot-service"></a>Serviço de Bot do Azure

O aplicativo é conduzido principalmente pela interface do usuário tradicional, por isso você usa o [Serviço de Bot do Azure](https://azure.microsoft.com/services/bot-service/) para adicionar alguma personalidade e agir como um novo método de interação.

## <a name="prerequisites"></a>Pré-requisitos

>[!TIP]
>Se você ainda não concluiu a série de [Tutoriais de introdução](mr-learning-base-01.md), recomendamos que você a conclua primeiro.

* Um PC com Windows 10 configurado com as [ferramentas corretas instaladas](../../install-the-tools.md)
* SDK do Windows 10 10.0.18362.0 ou posterior
* Alguma habilidade básica de programação em C#
* Um dispositivo HoloLens 2 [configurado para desenvolvimento](../../platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)
* Uma webcam conectada se você quiser testar no editor do Unity
* <a href="https://docs.unity3d.com/Manual/GettingStartedInstallingHub.html" target="_blank">Hub do Unity</a> com o Unity 2020/2019 LTS instalado e o módulo Suporte de Build da Plataforma Universal do Windows adicionado

> [!Important]
> Essa série de tutoriais suporta o Unity 2020 LTS (atualmente 2020.3.x) se você estiver usando o plug-in Open XR ou Windows XR, e também o Unity 2019 LTS (atualmente 2019.4.x) se estiver usando o Legacy WSA. Ela substitui todos os requisitos de versão do Unity indicadas nos pré-requisitos vinculados acima.

## <a name="creating-and-preparing-the-unity-project"></a>Como criar e preparar o projeto do Unity

Nesta seção, você criará um projeto do Unity e o deixará pronto para o desenvolvimento do MRTK.

Primeiro, siga [Inicializar seu projeto e o primeiro aplicativo](mr-learning-base-02.md), excluindo as instruções [Criar seu aplicativo para o dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2), que incluem as seguintes etapas:

1. [Criar um projeto do Unity](mr-learning-base-02.md#creating-the-unity-project) e dar a ele um nome adequado, por exemplo, *Tutoriais de Nuvem do Azure*
2. [Como alternar a plataforma de build](mr-learning-base-02.md#switching-the-build-platform)
3. [Como importar os Recursos Essenciais do TextMeshPro](mr-learning-base-04.md#importing-the-textmeshpro-essential-resources)
4. [Como importar o Kit de ferramentas de Realidade Misturada e configurar o projeto do Unity](mr-learning-base-02.md#importing-the-mixed-reality-toolkit-and-configuring-the-unity-project)
5. [Criar e configurar a cena](mr-learning-base-02.md#creating-the-scene-and-configuring-mrtk) e dar um nome adequado à cena, por exemplo, *AzureCloudServices*

Em seguida, siga as instruções em [Alterar a opção de exibição de reconhecimento espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) para garantir que o perfil de configuração MRTK para sua cena seja **DefaultHololens2ConfigurationProfile** e altere as opções de exibição da malha de reconhecimento espacial para **Oclusão**.

## <a name="installing-inbuilt-unity-packages-and-importing-the-tutorial-assets"></a>Instalação de pacotes incorporados do Unity e importação de ativos do tutorial

[!INCLUDE[](includes/installing-packages-for-azure-cloud-services.md)]

## <a name="creating-and-preparing-the-scene"></a>Como criar e preparar a cena

Nesta seção, você vai preparar a cena adicionando alguns pré-fabricados do tutorial.

Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**. Mantendo pressionada a tecla CTRL, clique em **SceneController**, **RootMenu** e **DataManager** para selecionar os três pré-fabricados:

![Unity com os pré-fabricados SceneController, RootMenu e DataManager selecionados](images/mr-learning-azure/tutorial1-section5-step1-1.png)

O **SceneController (pré-fabricado)** contém dois scripts, **SceneController (script)** e **AppDispatcher (script)** . O componente de script **SceneController** contém várias funções de experiência do usuário e facilita a funcionalidade de captura de fotos. O **AppDispatcher** é uma classe auxiliar para permitir a execução de ações no thread principal do Unity.

O **RootMenu (prefab)** é o pré-fabricado da interface do usuário principal que mantém todas as janelas da interface do usuário conectadas entre si por meio de vários pequenos componentes de script e que controla o fluxo geral de UX do aplicativo.

O **DataManager (prefab)** é responsável por conversar com o armazenamento do Azure e será explicado mais detalhadamente no próximo tutorial.

Agora, com os três pré-fabricados ainda selecionados, arraste-os para a janela Hierarquia para adicioná-los à cena:

![Unity com os pré-fabricados SceneController, RootMenu e DataManager recém-adicionados ainda selecionados](images/mr-learning-azure/tutorial1-section5-step1-2.png)

Para se concentrar nos objetos da cena, clique duas vezes no objeto **RootMenu** e, em seguida, reduzir levemente o zoom de novo:

![Unity com o objeto RootMenu selecionado](images/mr-learning-azure/tutorial1-section5-step1-3.png)

> [!TIP]
> Se você considerar que ícones grandes em sua cena, por exemplo, os ícones "T" grandes, causam distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição de desligado.

## <a name="configuring-the-scene"></a>Configurando a cena

Nesta seção, você conectará *SceneManager*, *DataManager* e *RootMenu* juntos para ter uma cena funcional pronta para o seguinte tutorial, [Integrar o armazenamento do Azure](mr-learning-azure-01.md).

### <a name="connect-the-objects"></a>Conectar os objetos

Na janela Hierarquia, selecione o objeto **DataManager**:

![Unity com o objeto DataManager selecionado](images/mr-learning-azure/tutorial1-section6-step1-1.png)

Na janela do Inspetor, localize o componente **DataManager (script)** e você verá um slot vazio no evento **On Data Manager Ready ()** . Agora, na janela Hierarquia, arraste o objeto **SceneController** para o evento **On Data Manager Ready ()** .

![Unity com o ouvinte de eventos do DataManager adicionado](images/mr-learning-azure/tutorial1-section6-step1-2.png)

Você observará que o menu suspenso do evento se tornou ativo; clique no menu suspenso e navegue até **SceneController** e, no submenu, selecione a opção **Init ()** :

![Unity com a ação de evento do DataManager adicionada](images/mr-learning-azure/tutorial1-section6-step1-3.png)

Na janela Hierarquia, selecione o objeto **SceneController**; então, no Inspetor, você encontrará o componente **SceneController** (script).

![Unity com a opção SceneController selecionada](images/mr-learning-azure/tutorial1-section6-step1-4.png)

Você verá que há vários campos não preenchidos; nós vamos alterar isso. Mova o objeto **DataManager** da Hierarquia para o campo *Gerenciador de Dados* e mova o GameObject **RootMenu** da Hierarquia para o campo *Menu Principal*.

![Unity com a opção SceneController configurada](images/mr-learning-azure/tutorial1-section6-step1-5.png)

Agora, sua cena está pronta para os próximos tutoriais. Não se esqueça de salvá-la em seu projeto.

## <a name="prepare-project-build-pipeline"></a>Preparar pipeline de Build do projeto

Embora o projeto ainda tenha que ser preenchido com conteúdo, você precisa executar alguns preparativos para que o projeto fique pronto para a compilação para o **HoloLens 2**.

### <a name="1-add-additional-required-capabilities"></a>1. Adicionar funcionalidades adicionais necessárias

No menu do Unity, selecione **Editar** > **Configurações de Projeto...** para abrir a janela Configurações de Projeto:

![Abrir Configurações de Projeto do Unity](images/mr-learning-azure/tutorial1-section7-step1-1.png)

Na janela Configurações do Projeto, selecione **Jogador** e **Configurações de Publicação**:

![Configurações de Publicação do Unity](images/mr-learning-azure/tutorial1-section7-step1-2.png)

Em **Configurações de Publicação**, role para baixo até a seção **Funcionalidades** e verifique se as funcionalidades **InternetClient**, **Microphone** e **SpatialPerception**, que você habilitou ao criar o projeto no início do tutorial, estão habilitadas. Em seguida, habilite as funcionalidades **InternetClientServer**, **PrivateNetworkClientServer** e **Webcam**:

![Funcionalidades do Unity](images/mr-learning-azure/tutorial1-section7-step1-3.png)

### <a name="2-deploy-the-app-to-your-hololens-2"></a>2. Implantar o aplicativo em seu HoloLens 2

Nem todos os recursos que você usará nesta série de tutoriais podem ser executados dentro do editor do Unity; isso significa que você precisa estar familiarizado com a implantação do aplicativo em seu dispositivo do HoloLens 2.

> [!TIP]
> Para se lembrar de como criar e implantar seu projeto do Unity no HoloLens 2, confira as instruções em [Tutoriais de introdução – Criar o aplicativo para seu dispositivo](mr-learning-base-02.md#building-your-application-to-your-hololens-2).

### <a name="3-run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a>3. Execute o aplicativo no seu HoloLens 2 e siga as instruções no aplicativo

> [!CAUTION]
> Todos os Serviços do Azure usam a Internet, portanto, verifique se o dispositivo está conectado à Internet.

Quando o aplicativo estiver em execução no dispositivo, aceite o acesso às seguintes funcionalidades solicitadas:

* Microfone
* Câmera

Esses recursos são necessários para serviços como *Chat Bot* e *Visão Personalizada* funcionarem corretamente.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você foi apresentado à série de tutoriais, aprendeu sobre os recursos que você implementará e como os serviços de **Nuvem do Azure** se unem para dar vida ao seu aplicativo do *HoloLens 2*. Você adicionou os componentes necessários ao projeto e preparou a cena para esta série de tutoriais.

Na próxima lição, você usará o armazenamento do Azure como uma solução de persistência baseada em nuvem para armazenar dados e imagens.

> [!div class="nextstepaction"]
> [Próximo tutorial: 2. Integrar o armazenamento do Azure](mr-learning-azure-02.md)