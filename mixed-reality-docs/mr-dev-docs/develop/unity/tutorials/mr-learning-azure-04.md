---
title: Integrar as Âncoras Espaciais do Azure
description: Conclua este curso para saber como implementar as Âncoras Espaciais do Azure em um aplicativo do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens 2, âncoras espaciais do Azure, serviços de nuvem do azure, visão personalizada do azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: 0837ebd9d34ba12d660098fc765824da3c561d07
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590538"
---
# <a name="4-integrating-azure-spatial-anchors"></a><span data-ttu-id="df573-104">4. Integrar as Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="df573-104">4. Integrating Azure Spatial Anchors</span></span>

<span data-ttu-id="df573-105">Neste tutorial, você aprenderá a usar as **Âncoras Espaciais do Azure**.</span><span class="sxs-lookup"><span data-stu-id="df573-105">In this tutorial, you will learn how to use **Azure Spatial Anchors**.</span></span> <span data-ttu-id="df573-106">Você armazenará o local de um **Objeto Rastreado** como uma Âncora Espacial do Azure.</span><span class="sxs-lookup"><span data-stu-id="df573-106">You will store the location of a **Tracked Object** as an Azure Spatial Anchor.</span></span> <span data-ttu-id="df573-107">Quando você consultar a âncora, uma seta será exibida para guiar você em direção ao local.</span><span class="sxs-lookup"><span data-stu-id="df573-107">Once you query for the anchor, an arrow will appear to guide you toward the location.</span></span>

## <a name="objectives"></a><span data-ttu-id="df573-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="df573-108">Objectives</span></span>

* <span data-ttu-id="df573-109">Aprender os conceitos básicos das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="df573-109">Learn the basics of Azure Spatial Anchors.</span></span>
* <span data-ttu-id="df573-110">Saber como configurar a cena para usar as Âncoras Espaciais do Azure neste projeto.</span><span class="sxs-lookup"><span data-stu-id="df573-110">Learn how to set up the scene to use Azure Spatial Anchors in this project.</span></span>
* <span data-ttu-id="df573-111">Saber como integrar de locais de armazenamento e consulta.</span><span class="sxs-lookup"><span data-stu-id="df573-111">Learn how to integrate storing and querying locations.</span></span>

## <a name="understanding-azure-spatial-anchors"></a><span data-ttu-id="df573-112">Noções básicas sobre Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="df573-112">Understanding Azure Spatial Anchors</span></span>

 <span data-ttu-id="df573-113">As **Âncoras Espaciais do Azure** fazem parte da família de Serviços de Nuvem do Azure e são usadas para salvar locais de âncora.</span><span class="sxs-lookup"><span data-stu-id="df573-113">**Azure Spatial Anchors** is part of the Azure Cloud Services family and is used to save anchor locations.</span></span> <span data-ttu-id="df573-114">Os locais de âncora salvos podem ser recuperados com base na *ID da âncora* na nuvem.</span><span class="sxs-lookup"><span data-stu-id="df573-114">The saved anchor locations can be retrieved based on the *anchor ID* from the cloud.</span></span> <span data-ttu-id="df573-115">Esse local de âncora pode ser compartilhado e acessado por dispositivos de várias plataformas, como dispositivos HoloLens, iOS e Android.</span><span class="sxs-lookup"><span data-stu-id="df573-115">This anchor location can be shared and accessed by multi-platform devices like HoloLens, iOS, and Android devices.</span></span>

<span data-ttu-id="df573-116">Saiba mais sobre as [Âncoras Espaciais do Azure](/azure/spatial-anchors/overview).</span><span class="sxs-lookup"><span data-stu-id="df573-116">Learn more about [Azure Spatial Anchors](/azure/spatial-anchors/overview).</span></span>

## <a name="preparing-azure-spatial-anchors"></a><span data-ttu-id="df573-117">Preparar as Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="df573-117">Preparing Azure Spatial Anchors</span></span>

<span data-ttu-id="df573-118">Para começar, crie um recurso de âncora espacial no portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="df573-118">Before you can start, you have to create a spatial anchor resource in your Azure portal.</span></span>
<span data-ttu-id="df573-119">Saiba como criar um [recurso de âncora espacial](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span><span class="sxs-lookup"><span data-stu-id="df573-119">Learn how to make a [spatial anchor resource](/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource).</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="df573-120">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="df573-120">Preparing the scene</span></span>

<span data-ttu-id="df573-121">Nesta seção, você aprenderá a configurar a cena e a fazer as alterações necessárias.</span><span class="sxs-lookup"><span data-stu-id="df573-121">In this section, you will learn how to configure the scene and make the necessary changes.</span></span>

<span data-ttu-id="df573-122">Na janela Projeto, navegue até **Ativos > MRTK.Tutorials.AzureCloudServices > Pré-fabricados > Gerenciador**</span><span class="sxs-lookup"><span data-stu-id="df573-122">In the Project window, navigate to the **Assets > MRTK.Tutorials.AzureCloudServices > Prefabs > Manager**</span></span>

![Unity com o pré-fabricado AnchorManager selecionado](images/mr-learning-azure/tutorial4-section1-step1-1.png)

<span data-ttu-id="df573-124">Na pasta **Gerenciador**, arraste e solte o pré-fabricadp **Gerenciador de Âncora** na Hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="df573-124">From the **Manager** folder, drag and drop the prefab **Anchor Manager** into the scene Hierarchy.</span></span>

<span data-ttu-id="df573-125">Selecione o GameObject **Gerenciador de Âncora** na Hierarquia e, na seção Inspetor, você encontrará o **Gerenciador de Âncora Espacial** (Script).</span><span class="sxs-lookup"><span data-stu-id="df573-125">Select **Anchor Manager** GameObject in the Hierarchy, and in the Inspector section, you will find **Spatial Anchor Manager** (Script).</span></span> <span data-ttu-id="df573-126">Localize a ID da conta e o campo de chave e adicione as credenciais que você criou no pré-requisito no estágio anterior.</span><span class="sxs-lookup"><span data-stu-id="df573-126">Find account ID and key field and add the credentials which you had created in the prerequisite in the earlier stage.</span></span>

![Unity com o pré-fabricado AnchorManager recém-adicionado ainda selecionado](images/mr-learning-azure/tutorial4-section1-step2-1.png)

<span data-ttu-id="df573-128">Agora, localize o objeto **Controlador de Cena** na Hierarquia de cena e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="df573-128">Now find the **Scene Controller** object in your scene Hierarchy and select it.</span></span> <span data-ttu-id="df573-129">Você verá o Inspetor do **Controlador de Cena**.</span><span class="sxs-lookup"><span data-stu-id="df573-129">You will see the **Scene Controller** Inspector.</span></span>

![Unity com o componente de script de SceneController configurado](images/mr-learning-azure/tutorial4-section1-step3-1.png)

<span data-ttu-id="df573-131">Você observará que o campo do **Gerenciador de Âncora** no componente **Controlador de Cena** está vazio; arraste o **Gerenciador de Âncora** da Hierarquia e solte-o na cena desse campo e salve a cena.</span><span class="sxs-lookup"><span data-stu-id="df573-131">You will observe that the **Anchor Manager** field in the **Scene Controller** component is empty, drag and drop the **Anchor Manager** from the Hierarchy in the scene into that field and save the scene.</span></span>

## <a name="build-and-deploy-the-app-to-your-hololens-2"></a><span data-ttu-id="df573-132">Compilar e Implantar o aplicativo no HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="df573-132">Build and Deploy the app to your HoloLens 2</span></span>

<span data-ttu-id="df573-133">As Âncoras Espaciais do Azure não podem ser executadas no Unity, portanto, para testar a funcionalidade delas, você precisa implantar o projeto em seu dispositivo.</span><span class="sxs-lookup"><span data-stu-id="df573-133">Azure Spatial Anchors can not run in Unity, so to test the Azure Spatial Anchors functionality, you need to deploy the project to your device.</span></span>

> [!TIP]
> <span data-ttu-id="df573-134">Para obter um lembrete sobre como criar e implantar o seu projeto do Unity no HoloLens 2, confira as instruções em [Como criar o aplicativo no seu HoloLens 2](mr-learning-base-02.md#building-and-deploying-to-your-hololens-2).</span><span class="sxs-lookup"><span data-stu-id="df573-134">For a reminder on how to build and deploy your Unity project to HoloLens 2, you can refer to the [Building your application to your HoloLens 2]((mr-learning-base-02.md#building-and-deploying-to-your-hololens-2) instructions.</span></span>

## <a name="run-the-app-on-your-hololens-2-and-follow-the-in-app-instructions"></a><span data-ttu-id="df573-135">Execute o aplicativo no seu HoloLens 2 e siga as instruções no aplicativo</span><span class="sxs-lookup"><span data-stu-id="df573-135">Run the app on your HoloLens 2 and follow the in-app instructions</span></span>

### <a name="create-an-anchor-to-store-a-location"></a><span data-ttu-id="df573-136">Criar uma âncora para armazenar um local</span><span class="sxs-lookup"><span data-stu-id="df573-136">Create an anchor to store a location</span></span>

<span data-ttu-id="df573-137">Nesta seção, você verá como salvar o local do objeto.</span><span class="sxs-lookup"><span data-stu-id="df573-137">In this section you will see how to save the object location.</span></span>

<span data-ttu-id="df573-138">Execute o aplicativo e clique em **Definir Objeto** no menu principal da experiência.</span><span class="sxs-lookup"><span data-stu-id="df573-138">Run the application and click on **Set Object** in the main menu of the experience.</span></span>

<span data-ttu-id="df573-139">Forneça o **nome** do objeto que você deseja salvar e clique em **Definir Objeto** para continuar.</span><span class="sxs-lookup"><span data-stu-id="df573-139">Give the **name** of the object you want to save and click on **Set Object** to continue.</span></span> <span data-ttu-id="df573-140">Para adicionar mais informações sobre o objeto, selecione a **imagem** e descreva o objeto.</span><span class="sxs-lookup"><span data-stu-id="df573-140">To add more information about the object, select the **image**, and describe the object.</span></span>

<span data-ttu-id="df573-141">Para salvar o local, clique em **Salvar Local**</span><span class="sxs-lookup"><span data-stu-id="df573-141">To save the location, click on **Save Location**</span></span>

<span data-ttu-id="df573-142">Você verá um **ponteiro de âncora** que poderá mover e posicionar no local que deseja salvar.</span><span class="sxs-lookup"><span data-stu-id="df573-142">You will see an **anchor pointer** that you can move and place on the location you want to save.</span></span> <span data-ttu-id="df573-143">Depois disso, você verá um pop-up de confirmação.</span><span class="sxs-lookup"><span data-stu-id="df573-143">After that, you will get a confirmation popup.</span></span> <span data-ttu-id="df573-144">Se você quiser confirmar e salvar o local, clique em **Sim**; caso contrário, altere o local clicando em **Não** e selecionando o local novamente.</span><span class="sxs-lookup"><span data-stu-id="df573-144">If you want to confirm and save the location, click on **Yes**; otherwise, you can change the location by clicking on **No** and selecting the location again.</span></span>

<span data-ttu-id="df573-145">Depois de confirmar o local clicando em **Sim**, o local e a ID da Âncora serão salvos no armazenamento em nuvem do Azure.</span><span class="sxs-lookup"><span data-stu-id="df573-145">Once you confirm the location by clicking on **Yes**, the location and the Anchor ID will be saved in the Azure cloud storage.</span></span> <span data-ttu-id="df573-146">Depois de salvar, você verá a **Marca de objeto** na âncora com o nome do objeto.</span><span class="sxs-lookup"><span data-stu-id="df573-146">Once it is saved, you will see the **Object tag**  in the anchor with the object's name.</span></span>

<span data-ttu-id="df573-147">Agora o local do objeto foi salvo com êxito.</span><span class="sxs-lookup"><span data-stu-id="df573-147">Now the object location is saved successfully.</span></span>

### <a name="query-for-finding-an-anchor-location"></a><span data-ttu-id="df573-148">Consultar para localizar um local de âncora</span><span class="sxs-lookup"><span data-stu-id="df573-148">Query for finding an anchor location</span></span>

<span data-ttu-id="df573-149">Depois de salvar com êxito o local de âncora, agora você pode encontrar o local da âncora selecionando **Pesquisar Objeto** no menu principal.</span><span class="sxs-lookup"><span data-stu-id="df573-149">Once after you successfully saved the anchor location, now you can find the anchor location by selecting **Search Object** in the main menu.</span></span>

<span data-ttu-id="df573-150">Depois de clicar em **Pesquisar Objeto**, uma nova janela será exibida, na qual você deverá dar o nome do objeto que deseja pesquisar.</span><span class="sxs-lookup"><span data-stu-id="df573-150">After clicking on **Search Object**, a new window will pop up in which you should give the name of the object you want to search.</span></span>

<span data-ttu-id="df573-151">Insira o nome do objeto e clique em **Pesquisar Objeto**.</span><span class="sxs-lookup"><span data-stu-id="df573-151">Enter the name of the object and click on **Search Object**.</span></span> <span data-ttu-id="df573-152">Se o objeto foi salvo anteriormente e for encontrado no banco de dados, você obterá o cartão de objeto com todos os detalhes do objeto que você salvou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="df573-152">If the object is saved previously and is found in the database, you will get the object card with all the details of the object you would have saved earlier.</span></span>

<span data-ttu-id="df573-153">Agora você pode clicar em **Mostrar Local** para localizar o objeto.</span><span class="sxs-lookup"><span data-stu-id="df573-153">Now you can click on **Show Location** to find the object.</span></span> <span data-ttu-id="df573-154">Ao clicar em **Mostrar Local**, o sistema consultará o endereço do objeto no armazenamento em nuvem.</span><span class="sxs-lookup"><span data-stu-id="df573-154">Once you click on **Show Location**, the system will query the object address from the cloud storage.</span></span>

<span data-ttu-id="df573-155">Depois de recuperar o local com êxito, uma **seta** vai direcioná-lo para o local do objeto.</span><span class="sxs-lookup"><span data-stu-id="df573-155">After successfully retrieving the location, an **arrow** will direct you towards the location of the object.</span></span> <span data-ttu-id="df573-156">Siga a marca de seta até encontrar o local do objeto.</span><span class="sxs-lookup"><span data-stu-id="df573-156">Follow the arrow mark until you find the location of the object.</span></span>

<span data-ttu-id="df573-157">Ao encontrar o objeto, o nome do objeto aparecerá na parte superior e a marca de seta desaparecerá e agora você poderá clicar na **marca de objeto** para ver os detalhes do objeto.</span><span class="sxs-lookup"><span data-stu-id="df573-157">Once you find the object, the object name will appear at the top, and the arrow mark will disappear, and now you can click on the **object tag** to see the details of the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="df573-158">Parabéns</span><span class="sxs-lookup"><span data-stu-id="df573-158">Congratulations</span></span>

<span data-ttu-id="df573-159">Neste tutorial, você aprendeu como as Âncoras Espaciais do Azure podem salvar e recuperar o local do objeto no Hololense 2.</span><span class="sxs-lookup"><span data-stu-id="df573-159">In this tutorial, you learned how Azure Spatial Anchors could save and retrieve the object location on Hololense 2.</span></span>

<span data-ttu-id="df573-160">No tutorial final, você aprenderá a usar o **Serviço de Bot do Azure** para adicionar linguagem natural como um novo método de interação para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="df573-160">In the final tutorial, you will learn how to use the **Azure Bot Service** to add natural language as a new interaction method for our application.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="df573-161">Próximo tutorial: 5. Integrar o Serviço de Bot do Azure com o LUIS</span><span class="sxs-lookup"><span data-stu-id="df573-161">Next tutorial: 5. Integrating Azure Bot Service with LUIS</span></span>](mr-learning-azure-05.md)