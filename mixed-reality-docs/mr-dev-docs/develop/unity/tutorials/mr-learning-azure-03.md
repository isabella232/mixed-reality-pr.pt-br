---
title: Integrar a Visão Personalizada do Azure
description: Conclua este curso para aprender a implementar a Visão Personalizada do Azure em um aplicativo de realidade misturada do HoloLens 2.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, hololens 2, visão personalizada do azure, serviços cognitivos do azure, serviços de nuvem do azure, Windows 10
ms.localizationpriority: high
ms.openlocfilehash: cb391aa2cdb7944234cdeede7dd05825c008d0d8
ms.sourcegitcommit: 68140e9ce84e69a99c2b3d970c7b8f2927a7fc93
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99590568"
---
# <a name="3-integrating-azure-custom-vision"></a><span data-ttu-id="3eae0-104">3. Integrar a Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="3eae0-104">3. Integrating Azure Custom Vision</span></span>

<span data-ttu-id="3eae0-105">Neste tutorial, você aprenderá a usar a **Visão Personalizada do Azure**. Você carregará um conjunto de fotos para associá-lo a um *Objeto Rastreado*, carregá-lo no serviço de **Visão Personalizada** e iniciar o processo de treinamento.</span><span class="sxs-lookup"><span data-stu-id="3eae0-105">In this tutorial, you will learn how to use **Azure Custom Vision**.You will upload a set of photos to associate it with a *Tracked Object*, upload them to the **Custom Vision** service and start the training process.</span></span> <span data-ttu-id="3eae0-106">Em seguida, você usará o serviço para detectar o *Objeto Rastreado* capturando fotos do feed da webcam.</span><span class="sxs-lookup"><span data-stu-id="3eae0-106">Then you will use the service to detect the *Tracked Object* by capturing photos from the webcam feed.</span></span>

## <a name="objectives"></a><span data-ttu-id="3eae0-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="3eae0-107">Objectives</span></span>

* <span data-ttu-id="3eae0-108">Aprender os conceitos básicos sobre a Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="3eae0-108">Learn the basics about Azure Custom Vision</span></span>
* <span data-ttu-id="3eae0-109">Saber como configurar a cena para usar a Visão Personalizada neste projeto</span><span class="sxs-lookup"><span data-stu-id="3eae0-109">Learn how to setup the scene to use Custom Vision in this project</span></span>
* <span data-ttu-id="3eae0-110">Saber como integrar o upload, treinar e detectar imagens</span><span class="sxs-lookup"><span data-stu-id="3eae0-110">Learn how to integrate upload, train and detect images</span></span>

## <a name="understanding-azure-custom-vision"></a><span data-ttu-id="3eae0-111">Compreender a Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="3eae0-111">Understanding Azure Custom Vision</span></span>

<span data-ttu-id="3eae0-112">A **Visão Personalizada do Azure** faz parte da família de **Serviços Cognitivos** e é usada para treinar classificadores de imagem.</span><span class="sxs-lookup"><span data-stu-id="3eae0-112">**Azure Custom Vision** is part of the **Cognitive Services** family and is used to train image classifiers.</span></span> <span data-ttu-id="3eae0-113">O classificador de imagens é um serviço de IA que usa o modelo treinado para aplicar marcas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="3eae0-113">The image classifier is an AI service that uses the trained model to apply matching tags.</span></span> <span data-ttu-id="3eae0-114">Esse recurso de classificação será usado pelo nosso aplicativo para detectar *Objetos Rastreados*.</span><span class="sxs-lookup"><span data-stu-id="3eae0-114">This classification feature will be used by our application to detect *Tracked Objects*.</span></span>

<span data-ttu-id="3eae0-115">Saiba mais sobre a [Visão Personalizada do Azure](/azure/cognitive-services/custom-vision-service/home).</span><span class="sxs-lookup"><span data-stu-id="3eae0-115">Learn more about [Azure Custom Vision](/azure/cognitive-services/custom-vision-service/home).</span></span>

## <a name="preparing-azure-custom-vision"></a><span data-ttu-id="3eae0-116">Como preparar a Visão Personalizada do Azure</span><span class="sxs-lookup"><span data-stu-id="3eae0-116">Preparing Azure Custom Vision</span></span>

<span data-ttu-id="3eae0-117">Para começar, crie um projeto de visão personalizada. A maneira mais rápida é usando o portal da Web.</span><span class="sxs-lookup"><span data-stu-id="3eae0-117">Before you can start, you have to create a custom vision project, the fastest way is by using the web portal.</span></span>

<span data-ttu-id="3eae0-118">Siga este [tutorial de início rápido](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) para configurar a sua conta e o projeto até a seção *Carregar e marcar imagens*.</span><span class="sxs-lookup"><span data-stu-id="3eae0-118">Follow this [quickstart tutorial](/azure/cognitive-services/custom-vision-service/getting-started-build-a-classifier#choose-training-images) to setup your account and project until section *Upload and tag images*.</span></span>

> [!WARNING]
> <span data-ttu-id="3eae0-119">Para treinar um modelo, você precisa ter pelo menos duas marcas e cinco imagens por marca.</span><span class="sxs-lookup"><span data-stu-id="3eae0-119">To train a model you need to have at least 2 tags and 5 images per tag.</span></span> <span data-ttu-id="3eae0-120">Para usar esse aplicativo, você deve criar pelo menos uma marca com cinco imagens, para que o processo de treinamento não falhe posteriormente.</span><span class="sxs-lookup"><span data-stu-id="3eae0-120">To use this application you should at least create one tag with 5 images, so that the training process later won't fail.</span></span>

## <a name="preparing-the-scene"></a><span data-ttu-id="3eae0-121">Preparando a cena</span><span class="sxs-lookup"><span data-stu-id="3eae0-121">Preparing the scene</span></span>

<span data-ttu-id="3eae0-122">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.AzureCloudServices** > **Pré-fabricados** > **Gerenciador**.</span><span class="sxs-lookup"><span data-stu-id="3eae0-122">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.AzureCloudServices** > **Prefabs** > **Manager** folder.</span></span>

![Unity com a janela Projeto mostrando o caminho para o pré-fabricado ObjectDetectionManager](images/mr-learning-azure/tutorial3-section4-step1-1.png)

<span data-ttu-id="3eae0-124">Em seguida, arraste o pré-fabricado **ObjectDetectionManager** para a Hierarquia de cena.</span><span class="sxs-lookup"><span data-stu-id="3eae0-124">From there drag the prefab **ObjectDetectionManager** into the scene Hierarchy.</span></span>

![Unity com os campos de configuração do componente de script de ObjectDetectionManager mostrados no Inspetor](images/mr-learning-azure/tutorial3-section4-step1-2.png)

<span data-ttu-id="3eae0-126">Na janela Hierarquia, localize o objeto **ObjectDetectionManager** e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="3eae0-126">In the Hierarchy window locate the **ObjectDetectionManager** object and select it.</span></span>
<span data-ttu-id="3eae0-127">O pré-fabricado **ObjectDetectionManager** contém o componente **ObjectDetectionManager (script)** e, como você pode ver na janela Inspetor, ele depende das configurações do Azure e de Projeto.</span><span class="sxs-lookup"><span data-stu-id="3eae0-127">The **ObjectDetectionManager** prefab contains the **ObjectDetectionManager (script)** component and as you can see from the Inspector window it depends on Azure settings and Project settings.</span></span>

## <a name="retrieving-azure-api-resource-credentials"></a><span data-ttu-id="3eae0-128">Como recuperar credenciais de recurso da API do Azure</span><span class="sxs-lookup"><span data-stu-id="3eae0-128">Retrieving Azure api resource credentials</span></span>

<span data-ttu-id="3eae0-129">As credenciais necessárias para as configurações **ObjectDetectionManager (script)** podem ser recuperadas no Portal do Azure e no portal da visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="3eae0-129">The necessary credentials for the **ObjectDetectionManager (script)** settings can be retrieve from the Azure Portal and the custom vision portal.</span></span>

### <a name="retrieving-azure-settings-credentials"></a><span data-ttu-id="3eae0-130">Como recuperar as credenciais de configurações do Azure</span><span class="sxs-lookup"><span data-stu-id="3eae0-130">Retrieving Azure Settings credentials</span></span>

<span data-ttu-id="3eae0-131">Localize o recurso de visão personalizada do tipo **Serviços Cognitivos** que você criou na seção *Como preparar a cena* deste tutorial (selecione os nomes dos recursos de visão personalizada seguidos de *-Prediction*).</span><span class="sxs-lookup"><span data-stu-id="3eae0-131">Find and locate the custom vision resource of type **Cognitive Services** you have created in the *Preparing the scene* section of this tutorial (select custom vision resources name followed by *-Prediction* ).</span></span> <span data-ttu-id="3eae0-132">Nele, clique em *Visão geral* ou *Chaves e Ponto de Extremidade* para recuperar as credenciais necessárias.</span><span class="sxs-lookup"><span data-stu-id="3eae0-132">There click on *Overview* or *Keys and Endpoint* to retrieve the necessary credentials.</span></span>

### <a name="retrieving-project-settings-credentials"></a><span data-ttu-id="3eae0-133">Como recuperar as credenciais de configurações do projeto</span><span class="sxs-lookup"><span data-stu-id="3eae0-133">Retrieving Project Settings credentials</span></span>

<span data-ttu-id="3eae0-134">No painel da [visão personalizada](https://www.customvision.ai/projects), abra o projeto que você criou para este tutorial e clique no canto superior direito da página no ícone de engrenagem para abrir a página de configurações.</span><span class="sxs-lookup"><span data-stu-id="3eae0-134">In the [custom vision](https://www.customvision.ai/projects) dashboard, open the project you have created for this tutorial and click on the top right corner of the page on the gear icon to open the settings page.</span></span> <span data-ttu-id="3eae0-135">Aqui, na seção *Recursos* à direita, você encontrará as credenciais necessárias.</span><span class="sxs-lookup"><span data-stu-id="3eae0-135">Here on the right hand *Resources* section you will find the necessary credentials.</span></span>

<span data-ttu-id="3eae0-136">Agora, com o **ObjectDetectionManager (script)** configurado corretamente, localize o objeto **SceneController** na sua Hierarquia de cena e selecione-o.</span><span class="sxs-lookup"><span data-stu-id="3eae0-136">Now with the **ObjectDetectionManager (script)** setup correctly, find the **SceneController** object in your scene Hierarchy and select it.</span></span>

![Unity com os campos de configuração do componente de script de SceneController mostrados no Inspetor](images/mr-learning-azure/tutorial3-section4-step1-3.png)

<span data-ttu-id="3eae0-138">Veja se o campo *Gerenciador de Detecção de Objetos* no componente **SceneController** está vazio, arraste o **ObjectDetectionManager** da Hierarquia para esse campo e salve a cena.</span><span class="sxs-lookup"><span data-stu-id="3eae0-138">You see *Object Detection Manager* field in the **SceneController** component is empty, drag the **ObjectDetectionManager** from the Hierarchy into that field and save the scene.</span></span>

![Unity com o componente de script de SceneController configurado](images/mr-learning-azure/tutorial3-section4-step1-4.png)

## <a name="take-and-upload-images"></a><span data-ttu-id="3eae0-140">Criar e carregar imagens</span><span class="sxs-lookup"><span data-stu-id="3eae0-140">Take and upload images</span></span>

<span data-ttu-id="3eae0-141">Execute a cena, clique em **Definir Objeto** e digite o nome de um dos **Objetos Rastreados** que você criou na [lição anterior](mr-learning-azure-02.md).</span><span class="sxs-lookup"><span data-stu-id="3eae0-141">Run the scene and click on **Set Object**, type in the name for one of the **Tracked Objects** you have created in the [previous lesson](mr-learning-azure-02.md).</span></span> <span data-ttu-id="3eae0-142">Agora, clique no botão **Pesquisa Visual Computacional** que está na parte inferior do **Cartão do Objeto**.</span><span class="sxs-lookup"><span data-stu-id="3eae0-142">Now click on **Computer Vision** button you can find at the bottom of the **Object Card**.</span></span>

<span data-ttu-id="3eae0-143">Uma nova janela será aberta, na qual você precisará tirar seis fotos para treinar o modelo de reconhecimento de imagem.</span><span class="sxs-lookup"><span data-stu-id="3eae0-143">A new window will open where you have to take six photos to train the model for image recognition.</span></span> <span data-ttu-id="3eae0-144">Clique no botão **Câmera** e execute um AirTap ao examinar o objeto que você deseja rastrear. Faça isso seis vezes.</span><span class="sxs-lookup"><span data-stu-id="3eae0-144">Click on the **Camera** button and perform an AirTap when you look on the object you like to track, do this six times.</span></span>

> [!TIP]
> <span data-ttu-id="3eae0-145">Para melhorar o treinamento do modelo, tente usar cada imagem de diferentes ângulos e condições de iluminação.</span><span class="sxs-lookup"><span data-stu-id="3eae0-145">To improve the model training try to take each image from different angles and lighting conditions.</span></span>

<span data-ttu-id="3eae0-146">Quando tiver imagens suficientes, clique no botão **Treinar** para iniciar o processo de treinamento de modelo na nuvem.</span><span class="sxs-lookup"><span data-stu-id="3eae0-146">Once you have enough images click on the **Train** button to start the model training process in the cloud.</span></span> <span data-ttu-id="3eae0-147">A ativação do treinamento carregará todas as imagens e, em seguida, iniciará o treinamento. Isso pode levar até um minuto ou mais.</span><span class="sxs-lookup"><span data-stu-id="3eae0-147">Activating the training will upload all images and then start the training, this can take up to a minute or more.</span></span> <span data-ttu-id="3eae0-148">Uma mensagem no menu indica o progresso atual e, quando ela indicar a conclusão, você poderá interromper o aplicativo</span><span class="sxs-lookup"><span data-stu-id="3eae0-148">A message inside the menu indicates the current progress and once it indicates the completion you can stop the application</span></span>

> [!TIP]
> <span data-ttu-id="3eae0-149">O **ObjectDetectionManager (script)** carrega diretamente as imagens feitas no serviço de Visão Personalizada.</span><span class="sxs-lookup"><span data-stu-id="3eae0-149">The **ObjectDetectionManager (script)** directly uploads taken images into the Custom Vision service.</span></span> <span data-ttu-id="3eae0-150">Como alternativa, a API da visão personalizada aceita URLs para as imagens. Como um exercício, você pode modificar o **ObjectDetectionManager (script)** para carregar as imagens para um Armazenamento de blobs.</span><span class="sxs-lookup"><span data-stu-id="3eae0-150">As an alternative the custom vision API accepts URLs to the images, as an exercise you can modify the **ObjectDetectionManager (script)** to upload the images to a Blob storage instead.</span></span>

## <a name="detect-objects"></a><span data-ttu-id="3eae0-151">Detectar objetos</span><span class="sxs-lookup"><span data-stu-id="3eae0-151">Detect objects</span></span>

<span data-ttu-id="3eae0-152">Antes de detectar os objetos, precisamos alterar a chave de API presente em **ObjectDetectionManager (script)** nas configurações de projeto que já foram atribuídas com a chave de visão personalizada.</span><span class="sxs-lookup"><span data-stu-id="3eae0-152">Before detecting the objects we have to change the Api key present in  **ObjectDetectionManager (script)** under project settings that already assign with custom vision key.</span></span>

<span data-ttu-id="3eae0-153">Localize o recurso de visão personalizada no portal do Azure. Nele, clique em *Chaves e Ponto de Extremidade* para recuperar a chave de API e substitua a chave de API antiga por essa nas configurações de projeto.</span><span class="sxs-lookup"><span data-stu-id="3eae0-153">Find and locate the custom vision resource in Azure portal.There click on *Keys and Endpoint* to retrieve the Api key and replace with old Api key under project settings.</span></span>

<span data-ttu-id="3eae0-154">Agora você pode testar o modelo treinado, executar o aplicativo e, no *menu principal* clicar em **Pesquisar Objeto** e digitar o nome do **Objeto Rastreado** em questão.</span><span class="sxs-lookup"><span data-stu-id="3eae0-154">You can now put the trained model to the test, run the application and from the *main menu* click on **Search Object** and type the name of the **Tracked Object** in question.</span></span> <span data-ttu-id="3eae0-155">O **Cartão de Objeto** aparecerá; clique no botão **Visão Personalizada**.</span><span class="sxs-lookup"><span data-stu-id="3eae0-155">The **Object Card** will appear and click on the **Custom Vision** button.</span></span> <span data-ttu-id="3eae0-156">A partir daqui, o **ObjectDetectionManager** começará a fazer capturas de imagem em segundo plano da câmera e o progresso será indicado no menu.</span><span class="sxs-lookup"><span data-stu-id="3eae0-156">From here the **ObjectDetectionManager** will start taking image captures in the background from the camera and the progress will be indicated on the menu.</span></span> <span data-ttu-id="3eae0-157">Aponte a câmera para o objeto usado para treinar o modelo e você verá que, após um curto período, ele detectará o objeto.</span><span class="sxs-lookup"><span data-stu-id="3eae0-157">Point the camera to the object you used to train the model and you will see that after a short while it will detect the object.</span></span>

## <a name="congratulations"></a><span data-ttu-id="3eae0-158">Parabéns</span><span class="sxs-lookup"><span data-stu-id="3eae0-158">Congratulations</span></span>

<span data-ttu-id="3eae0-159">Neste tutorial, você aprendeu como a Visão Personalizada do Azure pode ser usada para treinar imagens e usar o serviço de classificação para detectar imagens que correspondem ao **Objeto Rastreado** associado.</span><span class="sxs-lookup"><span data-stu-id="3eae0-159">In this tutorial you learned how Azure Custom Vision can be used to train images and use the classification service to detect images that match the associated **Tracked Object**.</span></span>

<span data-ttu-id="3eae0-160">No próximo tutorial, você aprenderá a usar as Âncoras Espaciais do Azure para vincular um *Objeto Rastreado* a uma localização no mundo físico e como exibir uma seta que orientará o usuário para a localização vinculada do Objeto Rastreado.</span><span class="sxs-lookup"><span data-stu-id="3eae0-160">In the next tutorial you will learn how to use Azure Spatial Anchors to link a *Tracked Object* with a location in the physical world and how to display an arrow that will guide the user back to the Tracked Object's linked location.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3eae0-161">Próximo tutorial: 4. Integrar as Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="3eae0-161">Next tutorial: 4. Integrating Azure Spatial Anchors</span></span>](mr-learning-azure-04.md)