---
title: Integrar o Serviço de Bot do Azure com o LUIS
description: Conclua este curso para aprender a implementar o Serviço de Bot do Azure e o reconhecimento vocal natural em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, hololens 2, serviço de bot do Azure, luis, linguagem natural, bot de conversa, serviços de nuvem do azure, visão personalizada do azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 66737f798ef87e756cf1935b12a368bbd22a3423
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590578"
---
# <a name="5-integrating-azure-bot-service"></a><span data-ttu-id="6973f-104">5. Integrar o Serviço de Bot do Azure</span><span class="sxs-lookup"><span data-stu-id="6973f-104">5. Integrating Azure Bot Service</span></span>

<span data-ttu-id="6973f-105">Neste tutorial, você aprenderá a usar o **Serviço de Bot do Azure** no aplicativo de demonstração do **HoloLens 2** para adicionar o Reconhecimento Vocal (LUIS) e permitir que o bot auxilie o usuário ao procurar **Objetos Rastreados**.</span><span class="sxs-lookup"><span data-stu-id="6973f-105">In this tutorial, you will learn how to use **Azure Bot Service** in the **HoloLens 2** demo application to add Language Understanding (LUIS) and letting the Bot assist the user when searching for **Tracked Objects**.</span></span> <span data-ttu-id="6973f-106">Este é um tutorial de duas partes. Na primeira, você cria o bot com o [Criador de Bot](https://docs.microsoft.com/composer/introduction) como uma solução de código gratuito e examina rapidamente a função do Azure que alimenta o bot com os dados necessários.</span><span class="sxs-lookup"><span data-stu-id="6973f-106">This is a two part tutorial where in the first part you create the Bot with the [Bot Composer](https://docs.microsoft.com/composer/introduction) as a code free solution and take a quick look in the Azure Function that feeds the Bot with the needed data.</span></span> <span data-ttu-id="6973f-107">Na segunda parte, você usa o **BotManager (Script)** no projeto do Unity para consumir o Serviço de Bot hospedado.</span><span class="sxs-lookup"><span data-stu-id="6973f-107">In the second part you use the **BotManager (script)** in the Unity project to consume the hosted Bot Service.</span></span>

## <a name="objectives"></a><span data-ttu-id="6973f-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="6973f-108">Objectives</span></span>

## <a name="part-1"></a><span data-ttu-id="6973f-109">Parte 1</span><span class="sxs-lookup"><span data-stu-id="6973f-109">Part 1</span></span>

* <span data-ttu-id="6973f-110">Conheça os conceitos básicos sobre o Serviço de Bot do Azure</span><span class="sxs-lookup"><span data-stu-id="6973f-110">Learn the basics about Azure Bot Service</span></span>
* <span data-ttu-id="6973f-111">Saiba como usar o Criador de Bot para criar um bot</span><span class="sxs-lookup"><span data-stu-id="6973f-111">Learn how to use the Bot Composer to create a Bot</span></span>
* <span data-ttu-id="6973f-112">Saiba como usar uma Função do Azure para fornecer dados do Armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="6973f-112">Learn how to use an Azure Function to provide data from the Azure Storage</span></span>

## <a name="part-2"></a><span data-ttu-id="6973f-113">Parte 2</span><span class="sxs-lookup"><span data-stu-id="6973f-113">Part 2</span></span>

* <span data-ttu-id="6973f-114">Saiba como configurar a cena para usar o Serviço de Bot do Azure neste projeto</span><span class="sxs-lookup"><span data-stu-id="6973f-114">Learn how to setup the scene to use Azure Bot Service in this project</span></span>
* <span data-ttu-id="6973f-115">Saiba como definir e localizar objetos conversando com o bot</span><span class="sxs-lookup"><span data-stu-id="6973f-115">Learn how to set and find objects via conversing with the Bot</span></span>

## <a name="understanding-azure-bot-service"></a><span data-ttu-id="6973f-116">Como entender o Serviço de Bot do Azure</span><span class="sxs-lookup"><span data-stu-id="6973f-116">Understanding Azure Bot Service</span></span>

<span data-ttu-id="6973f-117">O **Serviço de Bot do Azure** capacita os desenvolvedores a criar bots inteligentes que podem manter a conversa natural com os usuários graças à **LUIS**.</span><span class="sxs-lookup"><span data-stu-id="6973f-117">The **Azure Bot Service** empowers developers to create intelligent bots that can maintain natural conversation with users thanks to **LUIS**.</span></span> <span data-ttu-id="6973f-118">Um Bot de conversa é uma ótima maneira de expandir as maneiras como um usuário pode interagir com seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6973f-118">A conversational Bot is a great way to expand the ways a user can interact with your application.</span></span> <span data-ttu-id="6973f-119">Um Bot pode atuar como uma base de dados de conhecimento com um [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) para manter uma conversa sofisticada com a potência do [LUIS (Reconhecimento Vocal)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6973f-119">A Bot can act as a knowledge base with a [QnA Maker](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-qna?view=azure-bot-service-4.0&tabs=cs&preserve-view=true) to maintaining sophisticated conversation with the power of [Language Understanding (LUIS)](https://docs.microsoft.com/azure/bot-service/bot-builder-howto-v4-luis?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true).</span></span>

<span data-ttu-id="6973f-120">Saiba mais sobre o [Serviço de Bot do Azure](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="6973f-120">Learn more about [Azure Bot Service](https://docs.microsoft.com/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0&preserve-view=true).</span></span>

## <a name="part-1---creating-the-bot"></a><span data-ttu-id="6973f-121">Parte 1 – Como criar o bot</span><span class="sxs-lookup"><span data-stu-id="6973f-121">Part 1 - Creating the Bot</span></span>

<span data-ttu-id="6973f-122">Para usar o bot no aplicativo Unity, desenvolva-o, forneça dados a ele e hospede-o no **Azure**.</span><span class="sxs-lookup"><span data-stu-id="6973f-122">Before you can use the bot in the Unity application, you need to develope it, provide it with data and host it on **Azure**.</span></span>
<span data-ttu-id="6973f-123">A meta do bot é ter as capacidades de informar quantos *Objetos Rastreados* são armazenados no banco de dados, encontrar um *Objeto Rastreado* pelo seu nome e informar ao usuário algumas informações básicas sobre ele.</span><span class="sxs-lookup"><span data-stu-id="6973f-123">The goal of the bot is to have the abilities to tell how many *Tracked Objects* are stored in the database, find a *Tracked Object* by its name, and tell the user some basic information about it.</span></span>

### <a name="a-quick-look-into-tracked-objects-azure-function"></a><span data-ttu-id="6973f-124">Uma visão rápida da Função do Azure de Objetos Rastreados</span><span class="sxs-lookup"><span data-stu-id="6973f-124">A quick look into Tracked Objects Azure Function</span></span>

<span data-ttu-id="6973f-125">Você está prestes a começar a criar o bot, porém, para torná-lo útil, você precisa fornecer a ele um recurso do qual ele pode efetuar pull de dados.</span><span class="sxs-lookup"><span data-stu-id="6973f-125">You are about to start creating the Bot, but to make it useful you need to give it a resource from which it can pull data.</span></span> <span data-ttu-id="6973f-126">Como o *Bot* poderá contar a quantidade de **Objetos Rastreados**, localizar objetos específicos pelo nome e informar detalhes, você usará uma função simples do Azure que tem acesso ao **armazenamento de Tabelas do Azure**.</span><span class="sxs-lookup"><span data-stu-id="6973f-126">Since the *Bot* will be able to count the amount of **Tracked Objects**, find specific ones by name and tell details, you will use a simple Azure Function that has access to the **Azure Table storage**.</span></span>

<span data-ttu-id="6973f-127">Baixe o projeto da Função do Azure de Objetos Rastreados: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) e o extraia para o disco rígido.</span><span class="sxs-lookup"><span data-stu-id="6973f-127">Download the Tracked Objects Azure Function project: [AzureFunction_TrackedObjectsService.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/AzureFunction_TrackedObjectsService.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="6973f-128">Esta função do Azure tem duas ações, **Contar** e **Localizar**, que podem ser invocadas por meio de chamadas básicas *HTTP* *GET*.</span><span class="sxs-lookup"><span data-stu-id="6973f-128">This Azure Function has two actions, **Count** and **Find** which can be invoked via basic *HTTP* *GET* calls.</span></span> <span data-ttu-id="6973f-129">Você pode inspecionar o código no **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="6973f-129">You can inspect the code in **Visual Studio**.</span></span>

<span data-ttu-id="6973f-130">Saiba mais sobre [Funções do Azure](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span><span class="sxs-lookup"><span data-stu-id="6973f-130">Learn more about [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span>

<span data-ttu-id="6973f-131">As função **Contar** consulta do **Armazenamento de tabela** todos os **TrackedObjects** da tabela, muito simples.</span><span class="sxs-lookup"><span data-stu-id="6973f-131">The **Count** function queries from the **Table storage** all **TrackedObjects** from the table, very simple.</span></span> <span data-ttu-id="6973f-132">Por outro lado, a função **Localizar** usa um parâmetro de consulta *name* na solicitação *GET* e consulta o **Armazenamento de tabelas** para um **TrackedObject** correspondente e retorna um DTO como JSON.</span><span class="sxs-lookup"><span data-stu-id="6973f-132">On the other hand the **Find** function takes a *name* query parameter from the *GET* request and queries the **Table storage** for a matching **TrackedObject** and returns a DTO as JSON.</span></span>

<span data-ttu-id="6973f-133">Para implantar essa **Função do Azure** diretamente do **Visual Studio**, abra a pasta AzureFunction_TrackedObjectsService baixada e abra o arquivo presente **.sln** com a ![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-1.png) do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6973f-133">To deploy this **Azure Function** directly from **Visual Studio**, open the downloaded AzureFunction_TrackedObjectsService folder and open the present **.sln** file with visual studio ![Bot Framework Composer Home](images/mr-learning-azure/tutorial5-section3-step1-1.png)</span></span>

<span data-ttu-id="6973f-134">Depois que o arquivo for carregado no Visual Studio, clique com o botão direito do mouse em **Serviço de objeto acompanhado** no Gerenciador de Soluções e escolha Publicar ![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-2.png)</span><span class="sxs-lookup"><span data-stu-id="6973f-134">Once file loaded in visual studio, Right click over **Tracked object sevice** in solution explorer and select publish ![Bot Framework Composer Home](images/mr-learning-azure/tutorial5-section3-step1-2.png)</span></span>

<span data-ttu-id="6973f-135">O pop-up de publicação será exibido e solicitará a plataforma de destino. Selecione Azure e clique no botão **Avançar**</span><span class="sxs-lookup"><span data-stu-id="6973f-135">The publish pop up will be displayed and ask for target flatform Select azure and click on **Next** button</span></span>

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-3.png)

<span data-ttu-id="6973f-137">No destino específico, selecione **Aplicativo de Funções do Azure (Windows)** e clique no botão **Avançar**</span><span class="sxs-lookup"><span data-stu-id="6973f-137">In specific target select **Azure Function App(Windows)** and click on **Next** button</span></span>

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-4.png)

<span data-ttu-id="6973f-139">Se você não estiver conectado ao Azure, faça logon por meio do Visual Studio. A janela será parecida com esta</span><span class="sxs-lookup"><span data-stu-id="6973f-139">If you are not logged in to azure please login through visual studio and the window look like</span></span>

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-5.png)

<span data-ttu-id="6973f-141">Clique no botão de pulso para criar um Aplicativo de Funções na conta do Azure</span><span class="sxs-lookup"><span data-stu-id="6973f-141">Click on pulse button to create new Function App in azure account</span></span>

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-6.png)

* <span data-ttu-id="6973f-143">Em **Nome**, insira um nome adequado para o serviço, por exemplo, *TrackedObjectsService*</span><span class="sxs-lookup"><span data-stu-id="6973f-143">For **Name**, enter a suitable name for the service, for example, *TrackedObjectsService*</span></span>
* <span data-ttu-id="6973f-144">Em **Tipo de Plano**, escolha consumo</span><span class="sxs-lookup"><span data-stu-id="6973f-144">For **Plan Type**, choose consumption</span></span>
* <span data-ttu-id="6973f-145">Em **Localização**, escolha uma localização próxima à localização física dos usuários do seu aplicativo, por exemplo, *(EUA) Oeste dos EUA*</span><span class="sxs-lookup"><span data-stu-id="6973f-145">For **Location**, choose a location close to your app users' physical location, for example, *(US) West US*</span></span>
* <span data-ttu-id="6973f-146">Em **Grupo de Recursos** e **Armazenamento**, escolha a respectiva conta de armazenamento e o grupo do Azure que foram criados nos capítulos anteriores.</span><span class="sxs-lookup"><span data-stu-id="6973f-146">For **Resource Group** and **Storage**, choose respective azure group and storage account have been created in pervious chapters.</span></span>

<span data-ttu-id="6973f-147">Depois que Aplicativo de Funções for criado, clique no botão **Concluir**</span><span class="sxs-lookup"><span data-stu-id="6973f-147">Once Function App created click on **Finish** button</span></span> 

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-7.png)

<span data-ttu-id="6973f-149">Um pop-up de publicação será aberto após o processo de conclusão. Clique no botão **Publicar** para publicar a função e aguardar a publicação</span><span class="sxs-lookup"><span data-stu-id="6973f-149">A publish pop up will be opened after the finish process, click on **Publish** button to publish the function and wait for publish</span></span>

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section3-step1-8.png)

<span data-ttu-id="6973f-151">Após a conclusão da publicação, clique em **Gerenciar no portal do Azure** na seção Ações. É necessário que você use uma função específica no portal do Azure e clique em **Configuração**, que está na seção *Configurações*.</span><span class="sxs-lookup"><span data-stu-id="6973f-151">Once completion of publish click on **Manage in Azure portal** under Actions section it is take you to specific function in azure portal and click on **Configuration** which is under the *Settings* section.</span></span> <span data-ttu-id="6973f-152">Em **Configurações do Aplicativo**, forneça a *Cadeia de conexão* para o **Armazenamento do Azure** em que os **Objetos Rastreados** são armazenados.</span><span class="sxs-lookup"><span data-stu-id="6973f-152">There on **Application Settings** you need to provide the *Connection string* to the **Azure Storage** where the **Tracked Objects** are stored.</span></span> <span data-ttu-id="6973f-153">Clique em **Configuração de Novo Aplicativo** e use para nome: **AzureStorageConnectionString** e, para Valor, forneça a *Cadeia de conexão* correta.</span><span class="sxs-lookup"><span data-stu-id="6973f-153">Click on **New Application setting** and use for name: **AzureStorageConnectionString** and for value provide the correct *Connection string*.</span></span> <span data-ttu-id="6973f-154">Depois disso, clique em **Salvar** e a **Função do Azure** estará pronta para atender ao *Bot* que será criado em seguida.</span><span class="sxs-lookup"><span data-stu-id="6973f-154">After that click on **Save** and the **Azure Function** is ready to server the *Bot* which you will create next.</span></span>

<span data-ttu-id="6973f-155">Para obter a URL das funções Contar e Localizar, selecione **Funções** localizada na seção *Funções*.</span><span class="sxs-lookup"><span data-stu-id="6973f-155">To get URL of count and Find , select **Functions** which is under the *Functions* section.</span></span> <span data-ttu-id="6973f-156">Aqui, você poderá encontrar as funções Contar e Localizar. Selecione a função Contar no lado superior e você encontrará o botão *Obter URL da Função*.</span><span class="sxs-lookup"><span data-stu-id="6973f-156">here you can find both Count and Find function, select Count function on top side you can find the *Get Function Url* button.</span></span> <span data-ttu-id="6973f-157">Siga o mesmo procedimento para obter a URL da função Localizar.</span><span class="sxs-lookup"><span data-stu-id="6973f-157">Follow the same procedure to get Find function Url.</span></span>

### <a name="creating-a-conversation-bot"></a><span data-ttu-id="6973f-158">Como criar um bot de conversa</span><span class="sxs-lookup"><span data-stu-id="6973f-158">Creating a conversation Bot</span></span>

<span data-ttu-id="6973f-159">Há várias maneiras de desenvolver um bot de conversa baseado no Bot Framework.</span><span class="sxs-lookup"><span data-stu-id="6973f-159">There are several ways to develop a Bot Framework based conversational bot.</span></span> <span data-ttu-id="6973f-160">Nesta lição, você usará o aplicativo da área de trabalho [Bot Framework Composer](https://docs.microsoft.com/composer/), que é um designer visual perfeito para desenvolvimento rápido.</span><span class="sxs-lookup"><span data-stu-id="6973f-160">In this lesson you will use the [Bot Framework Composer](https://docs.microsoft.com/composer/) desktop application which is a visual designer that is perfect for rapid development.</span></span>

<span data-ttu-id="6973f-161">Você pode baixar as versões mais recentes do [repositório do GitHub](https://github.com/microsoft/BotFramework-Composer/releases).</span><span class="sxs-lookup"><span data-stu-id="6973f-161">You can download the latest releases from the [Github repository](https://github.com/microsoft/BotFramework-Composer/releases).</span></span> <span data-ttu-id="6973f-162">Ele está disponível para Windows, Mac e Linux.</span><span class="sxs-lookup"><span data-stu-id="6973f-162">It is available for Windows, Mac, and Linux.</span></span>

<span data-ttu-id="6973f-163">Depois que o **Bot Framework Composer** estiver instalado, inicie o aplicativo e você verá essa interface:</span><span class="sxs-lookup"><span data-stu-id="6973f-163">Once the **Bot Framework Composer** is installed, start the application and you should see this interface:</span></span>

![Página Inicial do Bot Framework Composer](images/mr-learning-azure/tutorial5-section4-step1-1.png)

<span data-ttu-id="6973f-165">Preparamos um projeto do criador de bot que fornece os diálogos e os gatilhos necessários para este tutorial.</span><span class="sxs-lookup"><span data-stu-id="6973f-165">We have prepared a bot composer project which provides the needed dialogues and triggers for this tutorial.</span></span> <span data-ttu-id="6973f-166">Baixe o projeto Bot Framework Composer: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) e o extraia para seu disco rígido.</span><span class="sxs-lookup"><span data-stu-id="6973f-166">Download the Bot Framework Composer project: [BotComposerProject_TrackedObjectsBot.zip](https://github.com/microsoft/MixedRealityLearning/releases/download/azure-cloud-services-v2.4.0/BotComposerProject_TrackedObjectsBot.zip) and extract it to your hard drive.</span></span>

<span data-ttu-id="6973f-167">Na barra superior, clique em **Abrir** e selecione o projeto do Bot Framework que você baixou, que se chama **TrackedObjectsBot**.</span><span class="sxs-lookup"><span data-stu-id="6973f-167">On the top bar click on **Open** and select the Bot Framework project you have downloaded which is named **TrackedObjectsBot**.</span></span> <span data-ttu-id="6973f-168">Depois que o projeto estiver totalmente carregado, você deverá ver o projeto pronto.</span><span class="sxs-lookup"><span data-stu-id="6973f-168">After the project is fully loaded, you should see the project ready.</span></span>

![O Bot Framework Composer com o projeto TrackedObjectsBot aberto](images/mr-learning-azure/tutorial5-section4-step1-2.png)

<span data-ttu-id="6973f-170">Vamos nos concentrar no lado esquerdo, em que é possível ver o **Painel Caixas de Diálogo**.</span><span class="sxs-lookup"><span data-stu-id="6973f-170">Let's focus on the left side where you can see the **Dialogs Panel**.</span></span> <span data-ttu-id="6973f-171">Lá, você tem uma caixa de diálogo chamada **TrackedObjectsBot** sob a qual pode ver vários **Gatilhos**.</span><span class="sxs-lookup"><span data-stu-id="6973f-171">There you have one dialog named **TrackedObjectsBot** under which you can see several **Triggers**.</span></span>

<span data-ttu-id="6973f-172">Saiba mais sobre os [conceitos do Bot Framework](https://docs.microsoft.com/composer/concept-dialog).</span><span class="sxs-lookup"><span data-stu-id="6973f-172">Learn more about [Bot Framework concepts](https://docs.microsoft.com/composer/concept-dialog).</span></span>

<span data-ttu-id="6973f-173">Esses gatilhos fazem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6973f-173">These triggers do the following:</span></span>

#### <a name="greeting"></a><span data-ttu-id="6973f-174">Saudação</span><span class="sxs-lookup"><span data-stu-id="6973f-174">Greeting</span></span>

<span data-ttu-id="6973f-175">Esse é o ponto de entrada do *bot* de chat quando sempre um *usuário* inicia uma conversa.</span><span class="sxs-lookup"><span data-stu-id="6973f-175">This is the entry point of the chat *bot* when ever a *user* initiates a conversation.</span></span>

![Saudação do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-3.png)

#### <a name="askingforcount"></a><span data-ttu-id="6973f-177">AskingForCount</span><span class="sxs-lookup"><span data-stu-id="6973f-177">AskingForCount</span></span>

<span data-ttu-id="6973f-178">Essa caixa de diálogo é disparada quando o *usuário* solicita a contagem de todos os **Objetos Rastreados**.</span><span class="sxs-lookup"><span data-stu-id="6973f-178">This dialog is triggered when the *user* asks for counting all **Tracked Objects**.</span></span>
<span data-ttu-id="6973f-179">Estas são as frases de gatilho:</span><span class="sxs-lookup"><span data-stu-id="6973f-179">These are the trigger phrases:</span></span>

>* <span data-ttu-id="6973f-180">conte tudo para mim</span><span class="sxs-lookup"><span data-stu-id="6973f-180">count me all</span></span>
>* <span data-ttu-id="6973f-181">quantos estão armazenados</span><span class="sxs-lookup"><span data-stu-id="6973f-181">how many are stored</span></span>

![AskForCount do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-4.png)

<span data-ttu-id="6973f-183">Graças ao [LUIS](https://docs.microsoft.com/composer/how-to-use-luis), o *usuário* não precisa perguntar as frases exatamente dessa maneira, o que permite uma conversa natural para o *usuário*.</span><span class="sxs-lookup"><span data-stu-id="6973f-183">Thanks to [LUIS](https://docs.microsoft.com/composer/how-to-use-luis) the *user* does not have to ask the phrases in that exact way which allows a natural conversation for the *user*.</span></span>

<span data-ttu-id="6973f-184">Nesta caixa de diálogo, o *bot* também se comunicará com a Função do Azure de **Contar**. Veja mais sobre isso posteriormente.</span><span class="sxs-lookup"><span data-stu-id="6973f-184">In this dialog the *bot* will also talk to the **Count** Azure Function, more about that later.</span></span>

#### <a name="unknown-intent"></a><span data-ttu-id="6973f-185">Intenção desconhecida</span><span class="sxs-lookup"><span data-stu-id="6973f-185">Unknown Intent</span></span>

<span data-ttu-id="6973f-186">Essa caixa de diálogo será disparada se a entrada do *usuário* não se ajustar a nenhuma outra condição de gatilho e responder ao usuário tentando sua pergunta novamente.</span><span class="sxs-lookup"><span data-stu-id="6973f-186">This dialogue is triggered if the input from the *user* does not fit any other trigger condition and responses the user with trying his question again.</span></span>

![Intenção desconhecida do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-5.png)

#### <a name="findentity"></a><span data-ttu-id="6973f-188">FindEntity</span><span class="sxs-lookup"><span data-stu-id="6973f-188">FindEntity</span></span>

<span data-ttu-id="6973f-189">A última caixa de diálogo é mais complexa, ramificando e armazenando na memória dos *bots*.</span><span class="sxs-lookup"><span data-stu-id="6973f-189">The last dialogue is more complex with branching and storing data in the *bots* memory.</span></span>
<span data-ttu-id="6973f-190">Ele solicita ao usuário o *nome* do **Objeto Rastreado** sobre o qual ele quer saber mais, executa uma consulta para a Função do Azure de **Localizar** e usa a resposta para continuar com a conversa.</span><span class="sxs-lookup"><span data-stu-id="6973f-190">It asks the user for the *name* of the **Tracked Object** it want's to know more information about, performs a query to the **Find** Azure Function, and uses the response to proceed with the conversation.</span></span>

![FindEntity do gatilho da caixa de diálogo do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section4-step1-6.png)

<span data-ttu-id="6973f-192">Se o **Objeto Rastreado** não for encontrado, o usuário será informado e a conversa terminará.</span><span class="sxs-lookup"><span data-stu-id="6973f-192">If the **Tracked Object** is not found, the user is informed and the conversation ends.</span></span> <span data-ttu-id="6973f-193">Quando o **Objeto Rastreado** em questão for encontrado, a inicialização verificará quais propriedades estão disponíveis e relatará sobre elas.</span><span class="sxs-lookup"><span data-stu-id="6973f-193">When the **Tracked Object** in question is found, the boot will check what properties are available and report on them.</span></span>

### <a name="adapting-the-bot"></a><span data-ttu-id="6973f-194">Como adaptar o bot</span><span class="sxs-lookup"><span data-stu-id="6973f-194">Adapting the Bot</span></span>

<span data-ttu-id="6973f-195">O gatilho **AskingForCount** e **FindEntity** precisam se comunicar com o back-end, o que significa que você precisa adicionar a URL correta da **Função do Azure** implantada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="6973f-195">The **AskingForCount** and **FindEntity** trigger need to talk to the backend, this means you have to add the correct URL of the **Azure Function** you deployed previously.</span></span>

<span data-ttu-id="6973f-196">No painel de diálogo, clique em **AskingForCount** e localize a ação *Enviar uma solicitação HTTP*. Aqui, você pode ver o campo **URL** para o qual você precisa alterar a URL correta para o ponto de extremidade da função **Contar**.</span><span class="sxs-lookup"><span data-stu-id="6973f-196">On the dialog panel click on **AskingForCount** and locate the *Send an HTTP request* action, here you can see the field **URL** which you need to change the correct URL for the **Count** function endpoint.</span></span>

![Configuração do ponto de extremidade do gatilho da caixa de diálogo AskingForCount do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-1.png)

<span data-ttu-id="6973f-198">Por fim, procure o gatilho **FindEntity** e localize a ação *Enviar uma solicitação HTTP*; no campo **URL**, altere a URL para o ponto de extremidade da função **Localizar**.</span><span class="sxs-lookup"><span data-stu-id="6973f-198">Finally, look for the **FindEntity** trigger and locate the *Send an HTTP request* action, in the **URL** field change the URL to the **Find** function endpoint.</span></span>

![Configuração do ponto de extremidade do gatilho da caixa de diálogo FindEntity do projeto TrackedObjectsBot](images/mr-learning-azure/tutorial5-section5-step1-2.png)

<span data-ttu-id="6973f-200">Com tudo definido, agora você está pronto para implantar o bot.</span><span class="sxs-lookup"><span data-stu-id="6973f-200">With everything set you are now ready to deploy the Bot.</span></span> <span data-ttu-id="6973f-201">Como você tem o Bot Framework Composer instalado, pode publicá-lo diretamente dele.</span><span class="sxs-lookup"><span data-stu-id="6973f-201">Since you have Bot Framework composer installed, you can publish it directly from there.</span></span>

<span data-ttu-id="6973f-202">Saiba mais sobre [Publicar um bot do Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span><span class="sxs-lookup"><span data-stu-id="6973f-202">Learn more about [Publish a bot from Bot Composer](https://docs.microsoft.com/composer/how-to-publish-bot).</span></span>

> [!TIP]
> <span data-ttu-id="6973f-203">Fique à vontade para explorar o bot adicionando mais frases de gatilho, novas respostas ou ramificação de conversa.</span><span class="sxs-lookup"><span data-stu-id="6973f-203">Feel free playing around with Bot by adding more trigger phrases, new responses or conversation branching.</span></span>

## <a name="part-2---putting-everything-together-in-unity"></a><span data-ttu-id="6973f-204">Parte 2 – Reunindo tudo no Unity</span><span class="sxs-lookup"><span data-stu-id="6973f-204">Part 2 - Putting everything together in Unity</span></span>

### <a name="preparing-the-scene"></a><span data-ttu-id="6973f-205">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="6973f-205">Preparing the scene</span></span>

<span data-ttu-id="6973f-206">Na janela do projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**.</span><span class="sxs-lookup"><span data-stu-id="6973f-206">In the Project window, navigate to **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Janela Projeto do Unity com o pré-fabricado ChatBotManager selecionado](images/mr-learning-azure/tutorial5-section6-step1-1.png)

<span data-ttu-id="6973f-208">Daí, mova o pré-fabricado **ChatBotManager** para a cena Hierarquia.</span><span class="sxs-lookup"><span data-stu-id="6973f-208">From there move the prefab **ChatBotManager** into the scene Hierarchy.</span></span>

<span data-ttu-id="6973f-209">Depois de adicionar o ChatBotManager à cena, clique no componente **Gerenciador de Bot de Chat**.</span><span class="sxs-lookup"><span data-stu-id="6973f-209">Once you add the ChatBotManager to the scene, click on the **Chat Bot Manager** component.</span></span>
<span data-ttu-id="6973f-210">No Inspetor, você verá que há um campo **Chave Secreta da Direct Line** vazio que você precisa preencher.</span><span class="sxs-lookup"><span data-stu-id="6973f-210">In the Inspector you will see that there is an empty **Direct Line Secret Key** field which you need to fill out.</span></span>

> [!TIP]
> <span data-ttu-id="6973f-211">Você pode recuperar a *chave secreta* do portal do Azure procurando o recurso do tipo **Registro de Canais de Bot** que você criou na primeira parte deste tutorial.</span><span class="sxs-lookup"><span data-stu-id="6973f-211">You can retrieve the *secret key* from the Azure portal by looking for the resource of type **Bot Channels Registration** you have created in the first part of this tutorial.</span></span>

![Unity com o pré-fabricado ChatBotManager recém-adicionado ainda selecionado](images/mr-learning-azure/tutorial5-section6-step1-2.png)

<span data-ttu-id="6973f-213">Agora, você conectará o objeto **ChatBotManager** com o componente **ChatBotController** que está anexado ao objeto **ChatBotPanel**.</span><span class="sxs-lookup"><span data-stu-id="6973f-213">Now you will connect the **ChatBotManager** object with the **ChatBotController** component that is attached to the **ChatBotPanel** object.</span></span> <span data-ttu-id="6973f-214">Na hierarquia, selecione o **ChatBotPanel** e você verá um campo **Gerenciador de Bot de Chat** vazio, arraste da Hierarquia o objeto **ChatBotManager** para o campo **Gerenciador de Bot de Chat** vazio.</span><span class="sxs-lookup"><span data-stu-id="6973f-214">In the Hierarchy select the **ChatBotPanel** and you will see an empty **Chat Bot Manager** field, drag from the Hierarchy the **ChatBotManager** object into the empty **Chat Bot Manager** field.</span></span>

![Unity com ChatBotPanel configurado](images/mr-learning-azure/tutorial5-section6-step1-3.png)

<span data-ttu-id="6973f-216">Em seguida, você precisa de uma forma de abrir o **ChatBotPanel** para que o usuário possa interagir com ele.</span><span class="sxs-lookup"><span data-stu-id="6973f-216">Next you need a way to open the **ChatBotPanel** so that the user can interact with it.</span></span> <span data-ttu-id="6973f-217">Na janela de cena, você pode ter notado que há um botão *Bot de Chat* no objeto **MainMenu**. Você o usará para resolver esse problema.</span><span class="sxs-lookup"><span data-stu-id="6973f-217">From the Scene window you may have noticed that there is a *Chat Bot* side button on the **MainMenu** object, you will use it to solve this problem.</span></span>

<span data-ttu-id="6973f-218">Na hierarquia, localize **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** e localize no Inspetor o script *ButtonConfigHelper*.</span><span class="sxs-lookup"><span data-stu-id="6973f-218">In the Hierarchy locate **RootMenu** > **MainMenu** > **SideButtonCollection** > **ButtonChatBot** and locate in the Inspector the *ButtonConfigHelper* script.</span></span> <span data-ttu-id="6973f-219">Lá, você verá um slot vazio no retorno de chamada do evento de **OnClick()** .</span><span class="sxs-lookup"><span data-stu-id="6973f-219">There you will see an empty slot on the **OnClick()** event callback.</span></span> <span data-ttu-id="6973f-220">Arraste e solte o **ChatBotPanel** para o slot de evento, na lista suspensa, navegue para *GameObject* e, em seguida, selecione no submenu *SetActive (bool)* e habilite a caixa de seleção.</span><span class="sxs-lookup"><span data-stu-id="6973f-220">Drag and drop the **ChatBotPanel** to the event slot, from the dropdown list navigate *GameObject*, then select in the sub menu *SetActive (bool)* and enable the checkbox.</span></span>

![Unity com ButtonChatBot configurado](images/mr-learning-azure/tutorial5-section6-step1-4.png)

<span data-ttu-id="6973f-222">Agora, o bot de bate-papo pode ser pausado no menu principal e, com isso, a cena estará pronta para uso.</span><span class="sxs-lookup"><span data-stu-id="6973f-222">Now the chat bot can be stared from the main menu and with that the scene is ready for use.</span></span>

### <a name="putting-the-bot-to-a-test"></a><span data-ttu-id="6973f-223">Como testar o bot</span><span class="sxs-lookup"><span data-stu-id="6973f-223">Putting the bot to a test</span></span>

#### <a name="asking-about-the-quantity-of-tracked-objects"></a><span data-ttu-id="6973f-224">Como perguntar a quantidade de objetos rastreados</span><span class="sxs-lookup"><span data-stu-id="6973f-224">Asking about the quantity of tracked objects</span></span>

<span data-ttu-id="6973f-225">Primeiro, você testa perguntando ao bot quantos **Objetos Rastreados** estão armazenados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6973f-225">First you test asking the bot how many **Tracked Objects** are stored in the database.</span></span>

> [!NOTE]
> <span data-ttu-id="6973f-226">Desta vez, você deve executar o aplicativo do HoloLens 2 porque serviços como *conversão de texto em fala* podem não estar disponíveis no seu sistema.</span><span class="sxs-lookup"><span data-stu-id="6973f-226">This time you must run the application from the HoloLens 2 because services like *text-to-speech* may not be available on your system.</span></span>

<span data-ttu-id="6973f-227">Execute o aplicativo no seu HoloLens 2 e clique no botão *Bot de Chat* ao lado do menu principal.</span><span class="sxs-lookup"><span data-stu-id="6973f-227">Run the application on your HoloLens 2 and click on the *Chat Bot* button next to the main menu.</span></span>
<span data-ttu-id="6973f-228">O bot o saudará, agora pergunte **quantos objetos temos?**</span><span class="sxs-lookup"><span data-stu-id="6973f-228">The bot will be greeting you, now ask **how many objects do we have?**</span></span>
<span data-ttu-id="6973f-229">Ele deverá informar a quantidade e encerrar a conversa.</span><span class="sxs-lookup"><span data-stu-id="6973f-229">It should tell you the quantity and end the conversation.</span></span>

#### <a name="asking-about-a-tracked-object"></a><span data-ttu-id="6973f-230">Como perguntar sobre um objeto acompanhado</span><span class="sxs-lookup"><span data-stu-id="6973f-230">Asking about a tracked object</span></span>

<span data-ttu-id="6973f-231">Agora, execute o aplicativo novamente e, desta vez, peça **encontre um objeto rastreado para mim**, o bot perguntará o nome, e você deverá responder com "carro" ou o nome de outro *Objeto Rastreado* que você saiba que existe no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6973f-231">Now run the application again and this time ask **find me a tracked object**, the bot will be asking you the name to which you should respond with the "car" or the name of an other *Tracked Object* you know exists in the database.</span></span> <span data-ttu-id="6973f-232">O bot informará detalhes como a descrição e se há uma âncora espacial atribuída.</span><span class="sxs-lookup"><span data-stu-id="6973f-232">The bot will tell you details like description and if it has a spatial anchor assigned.</span></span>

> [!TIP]
> <span data-ttu-id="6973f-233">Experimente pedir **Objetos Rastreados** que não existam e ouça como o bot responde.</span><span class="sxs-lookup"><span data-stu-id="6973f-233">Try out asking for an **Tracked Objects** that does not exist and hear how the bot responds.</span></span>

## <a name="congratulations"></a><span data-ttu-id="6973f-234">Parabéns</span><span class="sxs-lookup"><span data-stu-id="6973f-234">Congratulations</span></span>

<span data-ttu-id="6973f-235">Neste tutorial, você aprendeu como o Azure Bot Framework pode ser usado para interagir com o aplicativo por meio de conversa com linguagem natural.</span><span class="sxs-lookup"><span data-stu-id="6973f-235">In this tutorial you learned how Azure Bot Framework can be used to interact with the application via conversation with natural language.</span></span> <span data-ttu-id="6973f-236">Você aprendeu a desenvolver o próprio bot e conheceu todas as partes móveis para executá-lo.</span><span class="sxs-lookup"><span data-stu-id="6973f-236">You learned how to develop your own bot and what all the moving pieces are to get it running,</span></span>

## <a name="conclusion"></a><span data-ttu-id="6973f-237">Conclusão</span><span class="sxs-lookup"><span data-stu-id="6973f-237">Conclusion</span></span>

<span data-ttu-id="6973f-238">No decorrer desta série de tutoriais, você viu como os **Serviços de Nuvem do Azure** trouxeram recursos novos e empolgantes para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6973f-238">Through the course of this tutorial series you experienced how **Azure Cloud services** brought new and exciting features to your application.</span></span>
<span data-ttu-id="6973f-239">Agora você pode armazenar dados e imagens na nuvem com **Armazenamento do Azure**, usar a **Visão Personalizada do Azure** para associar imagens e treinar um modelo, trazer objetos para um contexto local com **Âncoras Espaciais do Azure** e implementar o **Azure Bot Framework desenvolvido com LUIS** para adicionar um bot de conversa para um padrão de interação novo e natural.</span><span class="sxs-lookup"><span data-stu-id="6973f-239">You can now store data and images in the cloud with **Azure Storage**, use **Azure Custom Vision** to associate images and train a model, bring objects to a local context with **Azure Spatial Anchors**, and implement **Azure Bot Framework powered by LUIS** to add a conversational bot for a new and natural interaction pattern.</span></span>
