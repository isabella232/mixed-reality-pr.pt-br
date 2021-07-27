---
title: Integrar o Serviço de Bot do Azure com o LUIS
description: Conclua este curso para aprender a implementar o Serviço de Bot do Azure e o reconhecimento vocal natural em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, hololens 2, serviço de bot do Azure, luis, linguagem natural, bot de conversa, serviços de nuvem do azure, visão personalizada do azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: bade124dff639e6f30fb67039debfddef54a22db
ms.sourcegitcommit: 114c304a416bfe9d9b294c4adbb4c23cbe60ea4e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/15/2021
ms.locfileid: "114224504"
---
# <a name="5-integrating-azure-bot-service"></a>5. Integrar o Serviço de Bot do Azure

Neste tutorial, você aprenderá a usar o **Serviço de Bot do Azure** no aplicativo de demonstração do **HoloLens 2** para adicionar o Reconhecimento Vocal (LUIS) e permitir que o bot auxilie o usuário ao procurar **Objetos Rastreados**. Este é um tutorial de duas partes. Na primeira, você cria o bot com o [Criador de Bot](/composer/introduction) como uma solução de código gratuito e examina rapidamente a função do Azure que alimenta o bot com os dados necessários. Na segunda parte, você usa o **BotManager (Script)** no projeto do Unity para consumir o Serviço de Bot hospedado.

## <a name="objectives"></a>Objetivos

## <a name="part-1"></a>Parte 1

* Conheça os conceitos básicos sobre o Serviço de Bot do Azure
* Saiba como usar o Criador de Bot para criar um bot
* Saiba como usar uma Função do Azure para fornecer dados do Armazenamento do Azure

## <a name="part-2"></a>Parte 2

* Saiba como configurar a cena para usar o Serviço de Bot do Azure neste projeto
* Saiba como definir e localizar objetos conversando com o bot

## <a name="understanding-azure-bot-service"></a>Como entender o Serviço de Bot do Azure

O **Serviço de Bot do Azure** capacita os desenvolvedores a criar bots inteligentes que podem manter a conversa natural com os usuários graças à **LUIS**. Um Bot de conversa é uma ótima maneira de expandir as maneiras como um usuário pode interagir com seu aplicativo. Um Bot pode atuar como uma base de dados de conhecimento com um [QnA Maker](/azure/bot-service/bot-builder-howto-qna?preserve-view=true&tabs=cs&view=azure-bot-service-4.0) para manter uma conversa sofisticada com a potência do [LUIS (Reconhecimento Vocal)](/azure/bot-service/bot-builder-howto-v4-luis?preserve-view=true&tabs=csharp&view=azure-bot-service-4.0).

Saiba mais sobre o [Serviço de Bot do Azure](/azure/bot-service/bot-service-overview-introduction?preserve-view=true&view=azure-bot-service-4.0).

## <a name="part-1---creating-the-bot"></a>Parte 1 – Como criar o bot

Para usar o bot no aplicativo Unity, desenvolva-o, forneça dados a ele e hospede-o no **Azure**.
A meta do bot é ter as capacidades de informar quantos *Objetos Rastreados* são armazenados no banco de dados, encontrar um *Objeto Rastreado* pelo seu nome e informar ao usuário algumas informações básicas sobre ele.

### <a name="a-quick-look-into-tracked-objects-azure-function"></a>Uma visão rápida da Função do Azure de Objetos Rastreados

Você está prestes a começar a criar o bot, porém, para torná-lo útil, você precisa fornecer a ele um recurso do qual ele pode efetuar pull de dados. Como o *Bot* poderá contar a quantidade de **Objetos Rastreados**, localizar objetos específicos pelo nome e informar detalhes, você usará uma função simples do Azure que tem acesso ao **armazenamento de Tabelas do Azure**.

Baixe o projeto da Função do Azure de Objetos Rastreados: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) e o extraia para o disco rígido.

Esta função do Azure tem duas ações, **Contar** e **Localizar**, que podem ser invocadas por meio de chamadas básicas *HTTP* *GET*. Você pode inspecionar o código no **Visual Studio**.

Saiba mais sobre [Funções do Azure](/azure/azure-functions/functions-overview).

As função **Contar** consulta do **Armazenamento de tabela** todos os **TrackedObjects** da tabela, muito simples. Por outro lado, a função **Localizar** usa um parâmetro de consulta *name* na solicitação *GET* e consulta o **Armazenamento de tabelas** para um **TrackedObject** correspondente e retorna um DTO como JSON.

Para implantar essa **função do Azure** diretamente do **Visual Studio**, abra a pasta AzureFunction_TrackedObjectsService baixada e abra o arquivo **.sln** presente com a ![pasta AzureFunction_TrackedObjectsService](images/mr-learning-azure/tutorial5-section3-step1-1.png) do Visual Studio

Depois que o arquivo for carregado no Visual Studio, clique com o botão direito do mouse em **Serviço de objeto acompanhado** no Gerenciador de Soluções e selecione ![Publicar serviço de objeto acompanhado](images/mr-learning-azure/tutorial5-section3-step1-2.png)

O pop-up de publicação será exibido e solicitará a plataforma de destino. Selecione Azure e clique no botão **Avançar**

![Selecionar a plataforma de destino](images/mr-learning-azure/tutorial5-section3-step1-3.png)

No destino específico, selecione **Aplicativo de Funções do Azure (Windows)** e clique no botão **Avançar**

![Selecionar o host de destino](images/mr-learning-azure/tutorial5-section3-step1-4.png)

Se você não estiver conectado ao Azure, faça logon por meio do Visual Studio. A janela será parecida com esta

![Selecionar ou criar uma função do Azure](images/mr-learning-azure/tutorial5-section3-step1-5.png)

Clique no botão de pulso para criar um Aplicativo de Funções na conta do Azure

![Criar um aplicativo de funções](images/mr-learning-azure/tutorial5-section3-step1-6.png)

* Em **Nome**, insira um nome adequado para o serviço, por exemplo, *TrackedObjectsService*
* Em **Tipo de Plano**, escolha consumo
* Em **Localização**, escolha uma localização próxima à localização física dos usuários do seu aplicativo, por exemplo, *(EUA) Oeste dos EUA*
* Em **Grupo de Recursos** e **Armazenamento**, escolha a respectiva conta de armazenamento e o grupo do Azure que foram criados nos capítulos anteriores.

Depois que Aplicativo de Funções for criado, clique no botão **Concluir**.

![Concluir a criação do aplicativo de funções](images/mr-learning-azure/tutorial5-section3-step1-7.png)

Para atualizar a cadeia de conexão, clique nos **três pontos** na guia de **hospedagem** e selecione **Configurações de gerenciamento do Serviço de Aplicativo do Azure**

![Abrir Configurações do aplicativo](images/mr-learning-azure/tutorial5-section3-step1-8.png)

Essa opção abre a janela **Configurações do aplicativo** e substitui AzureStorageConnectionString em **Local** e **Remoto** por AzureStorageConnectionString. Depois de substituído, clique em ok.

![Atualize a cadeia de conexão](images/mr-learning-azure/tutorial5-section3-step1-8a.png)

Agora, clique no botão **Publicar** para publicar a função e aguarde a publicação.

Após a conclusão da publicação, clique em **Gerenciar no portal do Azure** na seção Ações. É necessário que você use uma função específica no portal do Azure e clique em **Configuração**, que está na seção *Configurações*. Em **Configurações do Aplicativo**, forneça a *Cadeia de conexão* para o **Armazenamento do Azure** em que os **Objetos Rastreados** são armazenados. Clique em **Configuração de Novo Aplicativo** e use para nome: **AzureStorageConnectionString** e, para Valor, forneça a *Cadeia de conexão* correta. Depois disso, clique em **Salvar** e a **Função do Azure** estará pronta para atender ao *Bot* que será criado em seguida.

Para obter a URL das funções Contar e Localizar, selecione **Funções** localizada na seção *Funções*. Aqui, você poderá encontrar as funções Contar e Localizar. Selecione a função Contar no lado superior e você encontrará o botão *Obter URL da Função*.
Siga o mesmo procedimento para obter a URL da função Localizar.

### <a name="creating-a-conversation-bot"></a>Como criar um bot de conversa

Há várias maneiras de desenvolver um bot de conversa baseado no Bot Framework. Nesta lição, você usará o aplicativo da área de trabalho [Bot Framework Composer](/composer/), que é um designer visual perfeito para desenvolvimento rápido.

Você pode baixar as versões mais recentes do [repositório do GitHub](https://github.com/microsoft/BotFramework-Composer/releases). Ele está disponível para Windows, Mac e Linux.

Depois que o **Bot Framework Composer** estiver instalado, inicie o aplicativo e você verá essa interface:

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

Preparamos um projeto do criador de bot que fornece os diálogos e os gatilhos necessários para este tutorial. Baixe o projeto Bot Framework Composer: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) e o extraia para seu disco rígido.

Na barra superior, clique em **Abrir** e selecione o projeto do Bot Framework que você baixou, que se chama **TrackedObjectsBot**. Depois que o projeto estiver totalmente carregado, você deverá ver o projeto pronto.

![O Bot Framework Composer com o projeto TrackedObjectsBot aberto](images/mr-learning-azure/tutorial5-section4-step1-2.png)

Vamos nos concentrar no lado esquerdo, em que é possível ver o **Painel Caixas de Diálogo**. Lá, você tem uma caixa de diálogo chamada **TrackedObjectsBot** sob a qual pode ver vários **Gatilhos**.

Saiba mais sobre os [conceitos do Bot Framework](/composer/concept-dialog).

Esses gatilhos fazem o seguinte:

#### <a name="greeting"></a>Saudação

Esse é o ponto de entrada do *bot* de chat quando sempre um *usuário* inicia uma conversa.

![Saudação do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a>AskingForCount

Essa caixa de diálogo é disparada quando o *usuário* solicita a contagem de todos os **Objetos Rastreados**.
Estas são as frases de gatilho:

>* conte tudo para mim
>* quantos estão armazenados

![AskForCount do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

Graças ao [LUIS](/composer/how-to-use-luis), o *usuário* não precisa perguntar as frases exatamente dessa maneira, o que permite uma conversa natural para o *usuário*.

Nesta caixa de diálogo, o *bot* também se comunicará com a Função do Azure de **Contar**. Veja mais sobre isso posteriormente.

#### <a name="unknown-intent"></a>Intenção desconhecida

Essa caixa de diálogo será disparada se a entrada do *usuário* não se ajustar a nenhuma outra condição de gatilho e responder ao usuário tentando sua pergunta novamente.

![Intenção desconhecida do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a>FindEntity

A última caixa de diálogo é mais complexa, ramificando e armazenando na memória dos *bots*.
Ele solicita ao usuário o *nome* do **Objeto Rastreado** sobre o qual ele quer saber mais, executa uma consulta para a Função do Azure de **Localizar** e usa a resposta para continuar com a conversa.

![FindEntity do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

Se o **Objeto Rastreado** não for encontrado, o usuário será informado e a conversa terminará. Quando o **Objeto Rastreado** em questão for encontrado, a inicialização verificará quais propriedades estão disponíveis e relatará sobre elas.

### <a name="adapting-the-bot"></a>Como adaptar o bot

O gatilho **AskingForCount** e **FindEntity** precisam se comunicar com o back-end, o que significa que você precisa adicionar a URL correta da **Função do Azure** implantada anteriormente.

No painel de diálogo, clique em **AskingForCount** e localize a ação *Enviar uma solicitação HTTP*. Aqui, você pode ver o campo **URL** para o qual você precisa alterar a URL correta para o ponto de extremidade da função **Contar**.

![Configuração do ponto de extremidade do gatilho da caixa de diálogo AskingForCount do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-1.png)

Por fim, procure o gatilho **FindEntity** e localize a ação *Enviar uma solicitação HTTP*; no campo **URL**, altere a URL para o ponto de extremidade da função **Localizar**.

![Configuração do ponto de extremidade do gatilho da caixa de diálogo FindEntity do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-2.png)

Com tudo definido, agora você está pronto para implantar o bot. Como você tem o Bot Framework Composer instalado, pode publicá-lo diretamente dele.

Saiba mais sobre [Publicar um bot do Bot Composer](/composer/how-to-publish-bot).

> [!TIP]
> Fique à vontade para explorar o bot adicionando mais frases de gatilho, novas respostas ou ramificação de conversa.

## <a name="part-2---putting-everything-together-in-unity"></a>Parte 2 – Reunindo tudo no Unity

### <a name="preparing-the-scene"></a>Preparando a cena

Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**.

![Janela Projeto do Unity com o pré-fabricado ChatBotManager selecionado](images/mr-learning-azure/tutorial5-section6-step1-1.png)

Daí, mova o pré-fabricado **ChatBotManager** para a cena Hierarquia.

Depois de adicionar o ChatBotManager à cena, clique no componente **Gerenciador de Bot de Chat**.
No Inspetor, você verá que há um campo **Chave Secreta da Direct Line** vazio que você precisa preencher.

> [!TIP]
> Você pode recuperar a *chave secreta* do portal do Azure procurando o recurso do tipo **Registro de Canais de Bot** que você criou na primeira parte deste tutorial.

![Unity com o pré-fabricado ChatBotManager recém-adicionado ainda selecionado](images/mr-learning-azure/tutorial5-section6-step1-2.png)

Agora, você conectará o objeto **ChatBotManager** com o componente **ChatBotController** que está anexado ao objeto **ChatBotPanel**. Na hierarquia, selecione o **ChatBotPanel** e você verá um campo **Gerenciador de Bot de Chat** vazio, arraste da Hierarquia o objeto **ChatBotManager** para o campo **Gerenciador de Bot de Chat** vazio.

![Unity com ChatBotPanel configurado](images/mr-learning-azure/tutorial5-section6-step1-3.png)

Em seguida, você precisa de uma forma de abrir o **ChatBotPanel** para que o usuário possa interagir com ele. Na janela de cena, você pode ter notado que há um botão *Bot de Chat* no objeto **MainMenu**. Você o usará para resolver esse problema.

Na hierarquia, localize **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** e localize no Inspetor o script *ButtonConfigHelper*. Lá, você verá um slot vazio no retorno de chamada do evento de **OnClick()** . Arraste e solte o **ChatBotPanel** para o slot de evento, na lista suspensa, navegue para *GameObject* e, em seguida, selecione no submenu *SetActive (bool)* e habilite a caixa de seleção.

![Unity com ButtonChatBot configurado](images/mr-learning-azure/tutorial5-section6-step1-4.png)

Agora, o bot de bate-papo pode ser pausado no menu principal e, com isso, a cena estará pronta para uso.

### <a name="putting-the-bot-to-a-test"></a>Como testar o bot

#### <a name="asking-about-the-quantity-of-tracked-objects"></a>Como perguntar a quantidade de objetos rastreados

Primeiro, você testa perguntando ao bot quantos **Objetos Rastreados** estão armazenados no banco de dados.

> [!NOTE]
> Desta vez, você deve executar o aplicativo do HoloLens 2 porque serviços como *conversão de texto em fala* podem não estar disponíveis no seu sistema.

Execute o aplicativo no seu HoloLens 2 e clique no botão *Bot de Chat* ao lado do menu principal.
O bot o saudará, agora pergunte **quantos objetos temos?**
Ele deverá informar a quantidade e encerrar a conversa.

#### <a name="asking-about-a-tracked-object"></a>Como perguntar sobre um objeto acompanhado

Agora, execute o aplicativo novamente e, desta vez, peça **encontre um objeto rastreado para mim**, o bot perguntará o nome, e você deverá responder com "carro" ou o nome de outro *Objeto Rastreado* que você saiba que existe no banco de dados. O bot informará detalhes como a descrição e se há uma âncora espacial atribuída.

> [!TIP]
> Experimente pedir **Objetos Rastreados** que não existam e ouça como o bot responde.

## <a name="congratulations"></a>Parabéns

Neste tutorial, você aprendeu como o Azure Bot Framework pode ser usado para interagir com o aplicativo por meio de conversa com linguagem natural. Você aprendeu a desenvolver o próprio bot e conheceu todas as partes móveis para executá-lo.

## <a name="conclusion"></a>Conclusão

No decorrer desta série de tutoriais, você viu como os **Serviços de Nuvem do Azure** trouxeram recursos novos e empolgantes para seu aplicativo.
Agora você pode armazenar dados e imagens na nuvem com **Armazenamento do Azure**, usar a **Visão Personalizada do Azure** para associar imagens e treinar um modelo, trazer objetos para um contexto local com **Âncoras Espaciais do Azure** e implementar o **Azure Bot Framework desenvolvido com LUIS** para adicionar um bot de conversa para um padrão de interação novo e natural.