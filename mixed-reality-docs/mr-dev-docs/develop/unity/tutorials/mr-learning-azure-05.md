---
title: Integrar o Serviço de Bot do Azure com o LUIS
description: Conclua este curso para aprender a implementar o Serviço de Bot do Azure e o reconhecimento vocal natural em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, hololens 2, serviço de bot do Azure, luis, linguagem natural, bot de conversa, serviços de nuvem do azure, visão personalizada do azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 70d136467bc677c028614429e6e197ce25b30327
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008246"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="6244e-104">5. Integrar o Serviço de Bot do Azure</span><span class="sxs-lookup"><span data-stu-id="6244e-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="6244e-105">Neste tutorial, você aprenderá a usar o **Serviço de Bot do Azure** no aplicativo de demonstração do **HoloLens 2** para adicionar o Reconhecimento Vocal (LUIS) e permitir que o bot auxilie o usuário ao procurar **Objetos Rastreados**.</span><span class="sxs-lookup"><span data-stu-id="6244e-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="6244e-106">Este é um tutorial de duas partes. Na primeira, você cria o bot com o [Criador de Bot](https://docs.microsoft.com/composer/introduction) como uma solução de código gratuito e examina rapidamente a função do Azure que alimenta o bot com os dados necessários.</span><span class="sxs-lookup"><span data-stu-id="6244e-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="6244e-107">Na segunda parte, você usa o **BotManager (Script)** no projeto do Unity para consumir o Serviço de Bot hospedado.</span><span class="sxs-lookup"><span data-stu-id="6244e-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="6244e-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6244e-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="6244e-109">Parte 1</span><span class="sxs-lookup"><span data-stu-id="6244e-109">Part 1</span></span>

* <span data-ttu-id="6244e-110">Conheça os conceitos básicos sobre o Serviço de Bot do Azure</span><span class="sxs-lookup"><span data-stu-id="6244e-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="6244e-111">Saiba como usar o Criador de Bot para criar um bot</span><span class="sxs-lookup"><span data-stu-id="6244e-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="6244e-112">Saiba como usar uma Função do Azure para fornecer dados do Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="6244e-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="6244e-113">Parte 2</span><span class="sxs-lookup"><span data-stu-id="6244e-113">Part 2</span></span>

* <span data-ttu-id="6244e-114">Saiba como configurar a cena para usar o Serviço de Bot do Azure neste projeto</span><span class="sxs-lookup"><span data-stu-id="6244e-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="6244e-115">Saiba como definir e localizar objetos conversando com o bot</span><span class="sxs-lookup"><span data-stu-id="6244e-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="6244e-116">Como entender o Serviço de Bot do Azure</span><span class="sxs-lookup"><span data-stu-id="6244e-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="6244e-117">O **Serviço de Bot do Azure** capacita os desenvolvedores a criar bots inteligentes que podem manter a conversa natural com os usuários graças à **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="6244e-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="6244e-118">Um Bot de conversa é uma ótima maneira de expandir as maneiras como um usuário pode interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6244e-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="6244e-119">Um Bot pode atuar como uma base de dados de conhecimento com um [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) para manter uma conversa sofisticada com a potência do [LUIS (Reconhecimento Vocal)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6244e-119">A Bot can act as a knowledge base with a [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

<span data-ttu-id="6244e-120">Saiba mais sobre o [Serviço de Bot do Azure](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6244e-120">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="6244e-121">Parte 1 – Como criar o bot</span><span class="sxs-lookup"><span data-stu-id="6244e-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="6244e-122">Para usar o bot no aplicativo Unity, desenvolva-o, forneça dados a ele e hospede-o no **Azure**.</span><span class="sxs-lookup"><span data-stu-id="6244e-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="6244e-123">A meta do bot é ter as capacidades de informar quantos *Objetos Rastreados* são armazenados no banco de dados, encontrar um *Objeto Rastreado* pelo seu nome e informar ao usuário algumas informações básicas sobre ele.</span><span class="sxs-lookup"><span data-stu-id="6244e-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="6244e-124">Uma visão rápida da Função do Azure de Objetos Rastreados</span><span class="sxs-lookup"><span data-stu-id="6244e-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="6244e-125">Você está prestes a começar a criar o bot, porém, para torná-lo útil, você precisa fornecer a ele um recurso do qual ele pode efetuar pull de dados.</span><span class="sxs-lookup"><span data-stu-id="6244e-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="6244e-126">Como o *Bot* poderá contar a quantidade de **Objetos Rastreados**, localizar objetos específicos pelo nome e informar detalhes, você usará uma função simples do Azure que tem acesso ao **armazenamento de Tabelas do Azure**.</span><span class="sxs-lookup"><span data-stu-id="6244e-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="6244e-127">Baixe o projeto da Função do Azure de Objetos Rastreados: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) e o extraia para o disco rígido.</span><span class="sxs-lookup"><span data-stu-id="6244e-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="6244e-128">Esta função do Azure tem duas ações, **Contar** e **Localizar**, que podem ser invocadas por meio de chamadas básicas *HTTP* *GET*.</span><span class="sxs-lookup"><span data-stu-id="6244e-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="6244e-129">Você pode inspecionar o código no **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6244e-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="6244e-130">Saiba mais sobre [Funções do Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="6244e-130">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="6244e-131">As função **Contar** consulta do **Armazenamento de tabela** todos os **TrackedObjects** da tabela, muito simples.</span><span class="sxs-lookup"><span data-stu-id="6244e-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="6244e-132">Por outro lado, a função **Localizar** usa um parâmetro de consulta *name* na solicitação *GET* e consulta o **Armazenamento de tabelas** para um **TrackedObject** correspondente e retorna um DTO como JSON.</span><span class="sxs-lookup"><span data-stu-id="6244e-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="6244e-133">Você pode implantar essa **Função do Azure** diretamente do **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6244e-133">You can deploy this **Azure Function** directly from **Visual Studio**.</span></span>
<span data-ttu-id="6244e-134">Encontre aqui todas as informações sobre a [implantação de Função do Azure](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6244e-134">Find here all information regarding [Azure Function deployment](https://docs.microsoft.com/azure/devops/pipelines/targets/azure-functions?view=azure-devops&tabs=dotnet-core%2Cyaml&preserve-view=true).</span></span>

<span data-ttu-id="6244e-135">Depois de concluir a implantação, no **portal do Azure**, abra o recurso correspondente e clique em **Configuração**, que está na seção *Configurações*.</span><span class="sxs-lookup"><span data-stu-id="6244e-135">Once you have completed the deployment, in the **Azure Portal**, open the corresponding resource and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="6244e-136">Em **Configurações do Aplicativo**, forneça a *Cadeia de conexão* para o **Armazenamento do Azure** em que os **Objetos Rastreados** são armazenados.</span><span class="sxs-lookup"><span data-stu-id="6244e-136">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="6244e-137">Clique em **Configuração de Novo Aplicativo** e use para nome: **AzureStorageConnectionString** e, para Valor, forneça a *Cadeia de conexão* correta.</span><span class="sxs-lookup"><span data-stu-id="6244e-137">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="6244e-138">Depois disso, clique em **Salvar** e a **Função do Azure** estará pronta para atender ao *Bot* que será criado em seguida.</span><span class="sxs-lookup"><span data-stu-id="6244e-138">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="6244e-139">Como criar um bot de conversa</span><span class="sxs-lookup"><span data-stu-id="6244e-139">Creating a conversation Bot</span></span>

<span data-ttu-id="6244e-140">Há várias maneiras de desenvolver um bot de conversa baseado no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="6244e-140">There are several ways to develope a Bot Framework based conversational bot.</span></span> <span data-ttu-id="6244e-141">Nesta lição, você usará o aplicativo da área de trabalho [Bot Framework Composer](https://docs.microsoft.com/composer/), que é um designer visual perfeito para desenvolvimento rápido.</span><span class="sxs-lookup"><span data-stu-id="6244e-141">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="6244e-142">Você pode baixar as versões mais recentes do [repositório do GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="6244e-142">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="6244e-143">Ele está disponível para Windows, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="6244e-143">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="6244e-144">Depois que o **Bot Framework Composer** estiver instalado, inicie o aplicativo e você verá essa interface:</span><span class="sxs-lookup"><span data-stu-id="6244e-144">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="6244e-146">Preparamos um projeto do criador de bot que fornece os diálogos e os gatilhos necessários para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="6244e-146">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="6244e-147">Baixe o projeto Bot Framework Composer: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) e o extraia para seu disco rígido.</span><span class="sxs-lookup"><span data-stu-id="6244e-147">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="6244e-148">Na barra superior, clique em **Abrir** e selecione o projeto do Bot Framework que você baixou, que se chama **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="6244e-148">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="6244e-149">Depois que o projeto estiver totalmente carregado, você deverá ver o projeto pronto.</span><span class="sxs-lookup"><span data-stu-id="6244e-149">After the project is fully loaded, you should see the project ready.</span></span>

![O Bot Framework Composer com o projeto TrackedObjectsBot aberto](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="6244e-151">Vamos nos concentrar no lado esquerdo, em que é possível ver o **Painel Caixas de Diálogo**.</span><span class="sxs-lookup"><span data-stu-id="6244e-151">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="6244e-152">Lá, você tem uma caixa de diálogo chamada **TrackedObjectsBot** sob a qual pode ver vários **Gatilhos**.</span><span class="sxs-lookup"><span data-stu-id="6244e-152">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="6244e-153">Saiba mais sobre os [conceitos do Bot Framework](https://docs.microsoft.com/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="6244e-153">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="6244e-154">Esses gatilhos fazem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6244e-154">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="6244e-155">Saudação</span><span class="sxs-lookup"><span data-stu-id="6244e-155">Greeting</span></span>

<span data-ttu-id="6244e-156">Esse é o ponto de entrada do *bot* de chat quando sempre um *usuário* inicia uma conversa.</span><span class="sxs-lookup"><span data-stu-id="6244e-156">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![Saudação do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="6244e-158">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="6244e-158">AskingForCount</span></span>

<span data-ttu-id="6244e-159">Essa caixa de diálogo é disparada quando o *usuário* solicita a contagem de todos os **Objetos Rastreados**.</span><span class="sxs-lookup"><span data-stu-id="6244e-159">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="6244e-160">Estas são as frases de gatilho:</span><span class="sxs-lookup"><span data-stu-id="6244e-160">These are the trigger phrases:</span></span>

>* <span data-ttu-id="6244e-161">conte tudo para mim</span><span class="sxs-lookup"><span data-stu-id="6244e-161">count me all</span></span>
>* <span data-ttu-id="6244e-162">quantos estão armazenados</span><span class="sxs-lookup"><span data-stu-id="6244e-162">how many are stored</span></span>

![AskForCount do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="6244e-164">Graças ao [LUIS](https://docs.microsoft.com/composer/how-to-use-luis), o *usuário* não precisa perguntar as frases exatamente dessa maneira, o que permite uma conversa natural para o *usuário*.</span><span class="sxs-lookup"><span data-stu-id="6244e-164">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="6244e-165">Nesta caixa de diálogo, o *bot* também se comunicará com a Função do Azure de **Contar**. Veja mais sobre isso posteriormente.</span><span class="sxs-lookup"><span data-stu-id="6244e-165">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="6244e-166">Intenção desconhecida</span><span class="sxs-lookup"><span data-stu-id="6244e-166">Unknown Intent</span></span>

<span data-ttu-id="6244e-167">Essa caixa de diálogo será disparada se a entrada do *usuário* não se ajustar a nenhuma outra condição de gatilho e responder ao usuário tentando sua pergunta novamente.</span><span class="sxs-lookup"><span data-stu-id="6244e-167">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![Intenção desconhecida do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="6244e-169">FindEntity</span><span class="sxs-lookup"><span data-stu-id="6244e-169">FindEntity</span></span>

<span data-ttu-id="6244e-170">A última caixa de diálogo é mais complexa, ramificando e armazenando na memória dos *bots*.</span><span class="sxs-lookup"><span data-stu-id="6244e-170">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="6244e-171">Ele solicita ao usuário o *nome* do **Objeto Rastreado** sobre o qual ele quer saber mais, executa uma consulta para a Função do Azure de **Localizar** e usa a resposta para continuar com a conversa.</span><span class="sxs-lookup"><span data-stu-id="6244e-171">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![FindEntity do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="6244e-173">Se o **Objeto Rastreado** não for encontrado, o usuário será informado e a conversa terminará.</span><span class="sxs-lookup"><span data-stu-id="6244e-173">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="6244e-174">Quando o **Objeto Rastreado** em questão for encontrado, a inicialização verificará quais propriedades estão disponíveis e relatará sobre elas.</span><span class="sxs-lookup"><span data-stu-id="6244e-174">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="6244e-175">Como adaptar o bot</span><span class="sxs-lookup"><span data-stu-id="6244e-175">Adapting the Bot</span></span>

<span data-ttu-id="6244e-176">O gatilho **AskingForCount** e **FindEntity** precisam se comunicar com o back-end, o que significa que você precisa adicionar a URL correta da **Função do Azure** implantada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="6244e-176">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="6244e-177">No painel de diálogo, clique em **AskingForCount** e localize a ação *Enviar uma solicitação HTTP*. Aqui, você pode ver o campo **URL** para o qual você precisa alterar a URL correta para o ponto de extremidade da função **Contar**.</span><span class="sxs-lookup"><span data-stu-id="6244e-177">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![Configuração do ponto de extremidade do gatilho da caixa de diálogo AskingForCount do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="6244e-179">Por fim, procure o gatilho **FindEntity** e localize a ação *Enviar uma solicitação HTTP*; no campo **URL**, altere a URL para o ponto de extremidade da função **Localizar**.</span><span class="sxs-lookup"><span data-stu-id="6244e-179">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![Configuração do ponto de extremidade do gatilho da caixa de diálogo FindEntity do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="6244e-181">Com tudo definido, agora você está pronto para implantar o bot.</span><span class="sxs-lookup"><span data-stu-id="6244e-181">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="6244e-182">Como você tem o Bot Framework Composer instalado, pode publicá-lo diretamente dele.</span><span class="sxs-lookup"><span data-stu-id="6244e-182">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="6244e-183">Saiba mais sobre [Publicar um bot do Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="6244e-183">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="6244e-184">Fique à vontade para explorar o bot adicionando mais frases de gatilho, novas respostas ou ramificação de conversa.</span><span class="sxs-lookup"><span data-stu-id="6244e-184">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="6244e-185">Parte 2 – Reunindo tudo no Unity</span><span class="sxs-lookup"><span data-stu-id="6244e-185">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="6244e-186">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="6244e-186">Preparing the scene</span></span>

<span data-ttu-id="6244e-187">Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**.</span><span class="sxs-lookup"><span data-stu-id="6244e-187">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Janela Projeto do Unity com o pré-fabricado ChatBotManager selecionado](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="6244e-189">Daí, mova o pré-fabricado **ChatBotManager** para a cena Hierarquia.</span><span class="sxs-lookup"><span data-stu-id="6244e-189">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="6244e-190">Depois de adicionar o ChatBotManager à cena, clique no componente **Gerenciador de Bot de Chat**.</span><span class="sxs-lookup"><span data-stu-id="6244e-190">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="6244e-191">No Inspetor, você verá que há um campo **Chave Secreta da Direct Line** vazio que você precisa preencher.</span><span class="sxs-lookup"><span data-stu-id="6244e-191">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="6244e-192">Você pode recuperar a *chave secreta* do portal do Azure procurando o recurso do tipo **Registro de Canais de Bot** que você criou na primeira parte deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="6244e-192">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![Unity com o pré-fabricado ChatBotManager recém-adicionado ainda selecionado](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="6244e-194">Agora, você conectará o objeto **ChatBotManager** com o componente **ChatBotController** que está anexado ao objeto **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="6244e-194">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="6244e-195">Na hierarquia, selecione o **ChatBotPanel** e você verá um campo **Gerenciador de Bot de Chat** vazio, arraste da Hierarquia o objeto **ChatBotManager** para o campo **Gerenciador de Bot de Chat** vazio.</span><span class="sxs-lookup"><span data-stu-id="6244e-195">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![Unity com ChatBotPanel configurado](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="6244e-197">Em seguida, você precisa de uma forma de abrir o **ChatBotPanel** para que o usuário possa interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="6244e-197">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="6244e-198">Na janela de cena, você pode ter notado que há um botão *Bot de Chat* no objeto **MainMenu**. Você o usará para resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="6244e-198">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="6244e-199">Na hierarquia, localize **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** e localize no Inspetor o script *ButtonConfigHelper*.</span><span class="sxs-lookup"><span data-stu-id="6244e-199">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="6244e-200">Lá, você verá um slot vazio no retorno de chamada do evento de **OnClick()** .</span><span class="sxs-lookup"><span data-stu-id="6244e-200">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="6244e-201">Arraste e solte o **ChatBotPanel** para o slot de evento, na lista suspensa, navegue para *GameObject* e, em seguida, selecione no submenu *SetActive (bool)* e habilite a caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="6244e-201">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![Unity com ButtonChatBot configurado](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="6244e-203">Agora, o bot de bate-papo pode ser pausado no menu principal e, com isso, a cena estará pronta para uso.</span><span class="sxs-lookup"><span data-stu-id="6244e-203">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="6244e-204">Como testar o bot</span><span class="sxs-lookup"><span data-stu-id="6244e-204">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="6244e-205">Como perguntar a quantidade de objetos rastreados</span><span class="sxs-lookup"><span data-stu-id="6244e-205">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="6244e-206">Primeiro, você testa perguntando ao bot quantos **Objetos Rastreados** estão armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6244e-206">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="6244e-207">Desta vez, você deve executar o aplicativo do HoloLens 2 porque serviços como *conversão de texto em fala* podem não estar disponíveis no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="6244e-207">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="6244e-208">Execute o aplicativo no seu HoloLens 2 e clique no botão *Bot de Chat* ao lado do menu principal.</span><span class="sxs-lookup"><span data-stu-id="6244e-208">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="6244e-209">O bot o saudará, agora pergunte **quantos objetos temos?**</span><span class="sxs-lookup"><span data-stu-id="6244e-209">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="6244e-210">Ele deverá informar a quantidade e encerrar a conversa.</span><span class="sxs-lookup"><span data-stu-id="6244e-210">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="6244e-211">Como perguntar sobre um objeto acompanhado</span><span class="sxs-lookup"><span data-stu-id="6244e-211">Asking about a tracked object</span></span>

<span data-ttu-id="6244e-212">Agora, execute o aplicativo novamente e, desta vez, peça **encontre um objeto rastreado para mim**, o bot perguntará o nome, e você deverá responder com "carro" ou o nome de outro *Objeto Rastreado* que você saiba que existe no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6244e-212">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="6244e-213">O bot informará detalhes como a descrição e se há uma âncora espacial atribuída.</span><span class="sxs-lookup"><span data-stu-id="6244e-213">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="6244e-214">Experimente pedir **Objetos Rastreados** que não existam e ouça como o bot responde.</span><span class="sxs-lookup"><span data-stu-id="6244e-214">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6244e-215">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6244e-215">Congratulations</span></span>

<span data-ttu-id="6244e-216">Neste tutorial, você aprendeu como o Azure Bot Framework pode ser usado para interagir com o aplicativo por meio de conversa com linguagem natural.</span><span class="sxs-lookup"><span data-stu-id="6244e-216">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="6244e-217">Você aprendeu a desenvolver o próprio bot e conheceu todas as partes móveis para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="6244e-217">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="6244e-218">Conclusão</span><span class="sxs-lookup"><span data-stu-id="6244e-218">Conclusion</span></span>

<span data-ttu-id="6244e-219">No decorrer desta série de tutoriais, você viu como os **Serviços de Nuvem do Azure** trouxeram recursos novos e empolgantes para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6244e-219">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="6244e-220">Agora você pode armazenar dados e imagens na nuvem com **Armazenamento do Azure**, usar a **Visão Personalizada do Azure** para associar imagens e treinar um modelo, trazer objetos para um contexto local com **Âncoras Espaciais do Azure** e implementar o **Azure Bot Framework desenvolvido com LUIS** para adicionar um bot de conversa para um padrão de interação novo e natural.</span><span class="sxs-lookup"><span data-stu-id="6244e-220">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
