---
title: MR e Azure 302 – Pesquisa Visual Computacional
description: Conclua este curso para aprender a reconhecer o conteúdo visual dentro de uma imagem fornecida, usando o Azure Pesquisa Visual Computacional em um aplicativo de realidade misturada.
author: drneil
ms.author: jemccull
ms.date: 07/04/2018
ms.topic: article
keywords: Azure, realidade misturada, Academia, Unity, tutorial, API, pesquisa Visual computacional, hololens, imersão, VR, Windows 10, Visual Studio
ms.openlocfilehash: 2ba5f01b0b14c655f8639f74590a511629350fbb
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583286"
---
# <a name="mr-and-azure-302-computer-vision"></a><span data-ttu-id="dbbcb-104">MR e Azure 302: Pesquisa Visual Computacional</span><span class="sxs-lookup"><span data-stu-id="dbbcb-104">MR and Azure 302: Computer vision</span></span>

<br>

>[!NOTE]
><span data-ttu-id="dbbcb-105">Os tutoriais do Mixed Reality Academy foram projetados com o HoloLens (1ª geração) e os headsets imersivos de realidade misturada em mente.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-105">The Mixed Reality Academy tutorials were designed with HoloLens (1st gen) and Mixed Reality Immersive Headsets in mind.</span></span>  <span data-ttu-id="dbbcb-106">Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-106">As such, we feel it is important to leave these tutorials in place for developers who are still looking for guidance in developing for those devices.</span></span>  <span data-ttu-id="dbbcb-107">Esses tutoriais **_não_** serão atualizados com os conjuntos de ferramentas mais recentes nem com as interações usadas para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-107">These tutorials will **_not_** be updated with the latest toolsets or interactions being used for HoloLens 2.</span></span>  <span data-ttu-id="dbbcb-108">Eles serão mantidos para continuar funcionando nos dispositivos compatíveis.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-108">They will be maintained to continue working on the supported devices.</span></span> <span data-ttu-id="dbbcb-109">Haverá uma nova série de tutoriais que serão publicados no futuro, que demonstrarão como desenvolver para o HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-109">There will be a new series of tutorials that will be posted in the future that will demonstrate how to develop for HoloLens 2.</span></span>  <span data-ttu-id="dbbcb-110">Esse aviso será atualizado com um link para esses tutoriais quando eles forem postados.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-110">This notice will be updated with a link to those tutorials when they are posted.</span></span>

<br>

<span data-ttu-id="dbbcb-111">Neste curso, você aprenderá a reconhecer o conteúdo visual dentro de uma imagem fornecida, usando os recursos de Pesquisa Visual Computacional do Azure em um aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-111">In this course, you will learn how to recognize visual content within a provided image, using Azure Computer Vision capabilities in a mixed reality application.</span></span>

<span data-ttu-id="dbbcb-112">Os resultados de reconhecimento serão exibidos como marcas descritivas.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-112">Recognition results will be displayed as descriptive tags.</span></span> <span data-ttu-id="dbbcb-113">Você pode usar esse serviço sem a necessidade de treinar um modelo de aprendizado de máquina.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-113">You can use this service without needing to train a machine learning model.</span></span> <span data-ttu-id="dbbcb-114">Se sua implementação exigir treinamento de um modelo de aprendizado de máquina, consulte [Mr e Azure 302b](mr-azure-302b.md).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-114">If your implementation requires training a machine learning model, see [MR and Azure 302b](mr-azure-302b.md).</span></span>

![resultado do laboratório](images/AzureLabs-Lab2-000.png)

<span data-ttu-id="dbbcb-116">O Microsoft Pesquisa Visual Computacional é um conjunto de APIs projetado para fornecer aos desenvolvedores o processamento e a análise de imagens (com informações de retorno), usando algoritmos avançados, tudo da nuvem.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-116">The Microsoft Computer Vision is a set of APIs designed to provide developers with image processing and analysis (with return information), using advanced algorithms, all from the cloud.</span></span> <span data-ttu-id="dbbcb-117">Os desenvolvedores carregam uma URL de imagem ou imagem, e os algoritmos de API da Pesquisa Visual Computacional da Microsoft analisam o conteúdo visual, com base nas entradas escolhidas pelo usuário, que podem retornar informações, incluindo, identificar o tipo e a qualidade de uma imagem, detectar faces humanas (retornando suas coordenadas) e marcando ou categorizando imagens.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-117">Developers upload an image or image URL, and the Microsoft Computer Vision API algorithms analyze the visual content, based upon inputs chosen the user, which then can return information, including, identifying the type and quality of an image, detect human faces (returning their coordinates), and tagging, or categorizing images.</span></span> <span data-ttu-id="dbbcb-118">Para obter mais informações, visite a [página de API da pesquisa Visual computacional do Azure](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-118">For more information, visit the [Azure Computer Vision API page](https://azure.microsoft.com/services/cognitive-services/computer-vision/).</span></span>

<span data-ttu-id="dbbcb-119">Após a conclusão deste curso, você terá um aplicativo de HoloLens de realidade misturada, que poderá fazer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-119">Having completed this course, you will have a mixed reality HoloLens application, which will be able to do the following:</span></span>

1.  <span data-ttu-id="dbbcb-120">Usando o gesto de toque, a câmera do HoloLens capturará uma imagem.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-120">Using the Tap gesture, the camera of the HoloLens will capture an image.</span></span>
2.  <span data-ttu-id="dbbcb-121">A imagem será enviada para o serviço de API da Pesquisa Visual Computacional do Azure.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-121">The image will be sent to the Azure Computer Vision API Service.</span></span> 
3.  <span data-ttu-id="dbbcb-122">Os objetos reconhecidos serão listados em um grupo de interface do usuário simples posicionado na cena do Unity.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-122">The objects recognized will be listed in a simple UI group positioned in the Unity Scene.</span></span>

<span data-ttu-id="dbbcb-123">Em seu aplicativo, cabe a você como você integrará os resultados com seu design.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-123">In your application, it is up to you as to how you will integrate the results with your design.</span></span> <span data-ttu-id="dbbcb-124">Este curso foi projetado para ensinar a você como integrar um serviço do Azure com seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-124">This course is designed to teach you how to integrate an Azure Service with your Unity project.</span></span> <span data-ttu-id="dbbcb-125">É seu trabalho usar o conhecimento obtido deste curso para aprimorar seu aplicativo de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-125">It is your job to use the knowledge you gain from this course to enhance your mixed reality application.</span></span>

## <a name="device-support"></a><span data-ttu-id="dbbcb-126">Suporte a dispositivos</span><span class="sxs-lookup"><span data-stu-id="dbbcb-126">Device support</span></span>

<table>
<tr>
<th><span data-ttu-id="dbbcb-127">Curso</span><span class="sxs-lookup"><span data-stu-id="dbbcb-127">Course</span></span></th><th style="width:150px"> <span data-ttu-id="dbbcb-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span><span class="sxs-lookup"><span data-stu-id="dbbcb-128"><a href="/hololens/hololens1-hardware">HoloLens</a></span></span></th><th style="width:150px"> <span data-ttu-id="dbbcb-129"><a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></span><span class="sxs-lookup"><span data-stu-id="dbbcb-129"><a href="../../../discover/immersive-headset-hardware-details.md">Immersive headsets</a></span></span></th>
</tr><tr>
<td> <span data-ttu-id="dbbcb-130">MR e Azure 302: Pesquisa Visual Computacional</span><span class="sxs-lookup"><span data-stu-id="dbbcb-130">MR and Azure 302: Computer vision</span></span></td><td style="text-align: center;"> <span data-ttu-id="dbbcb-131">✔️</span><span class="sxs-lookup"><span data-stu-id="dbbcb-131">✔️</span></span></td><td style="text-align: center;"> <span data-ttu-id="dbbcb-132">✔️</span><span class="sxs-lookup"><span data-stu-id="dbbcb-132">✔️</span></span></td>
</tr>
</table>

> [!NOTE]
> <span data-ttu-id="dbbcb-133">Embora este curso se concentre principalmente no HoloLens, você também pode aplicar o que aprende neste curso a fones de ouvido (VR) de realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-133">While this course primarily focuses on HoloLens, you can also apply what you learn in this course to Windows Mixed Reality immersive (VR) headsets.</span></span> <span data-ttu-id="dbbcb-134">Como os headsets de imersão (VR) não têm câmeras acessíveis, você precisará de uma câmera externa conectada ao seu PC.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-134">Because immersive (VR) headsets do not have accessible cameras, you will need an external camera connected to your PC.</span></span> <span data-ttu-id="dbbcb-135">Ao acompanhar o curso, você verá observações sobre as alterações que talvez precise empregar para dar suporte a headsets de imersão (VR).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-135">As you follow along with the course, you will see notes on any changes you might need to employ to support immersive (VR) headsets.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dbbcb-136">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="dbbcb-136">Prerequisites</span></span>

> [!NOTE]
> <span data-ttu-id="dbbcb-137">Este tutorial foi projetado para desenvolvedores que têm experiência básica com o Unity e o C#.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-137">This tutorial is designed for developers who have basic experience with Unity and C#.</span></span> <span data-ttu-id="dbbcb-138">Além disso, lembre-se de que os pré-requisitos e as instruções escritas neste documento representam o que foi testado e verificado no momento da gravação (maio de 2018).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-138">Please also be aware that the prerequisites and written instructions within this document represent what has been tested and verified at the time of writing (May 2018).</span></span> <span data-ttu-id="dbbcb-139">Você está livre para usar o software mais recente, conforme listado no artigo [instalar as ferramentas](../../install-the-tools.md) , embora não seja recomendável que as informações neste curso irão se adequar perfeitamente ao que você encontrará em softwares mais recentes do que as listadas abaixo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-139">You are free to use the latest software, as listed within the [install the tools](../../install-the-tools.md) article, though it should not be assumed that the information in this course will perfectly match what you'll find in newer software than what's listed below.</span></span>

<span data-ttu-id="dbbcb-140">Recomendamos o seguinte hardware e software para este curso:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-140">We recommend the following hardware and software for this course:</span></span>

- <span data-ttu-id="dbbcb-141">Um PC de desenvolvimento, [compatível com o Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) para desenvolvimento de headsets de imersão (VR)</span><span class="sxs-lookup"><span data-stu-id="dbbcb-141">A development PC, [compatible with Windows Mixed Reality](https://support.microsoft.com/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) for immersive (VR) headset development</span></span>
- [<span data-ttu-id="dbbcb-142">Atualização dos criadores de outono do Windows 10 (ou posterior) com o modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="dbbcb-142">Windows 10 Fall Creators Update (or later) with Developer mode enabled</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dbbcb-143">O SDK do Windows 10 mais recente</span><span class="sxs-lookup"><span data-stu-id="dbbcb-143">The latest Windows 10 SDK</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dbbcb-144">Unity 2017,4</span><span class="sxs-lookup"><span data-stu-id="dbbcb-144">Unity 2017.4</span></span>](../../install-the-tools.md#installation-checklist)
- [<span data-ttu-id="dbbcb-145">Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="dbbcb-145">Visual Studio 2017</span></span>](../../install-the-tools.md#installation-checklist)
- <span data-ttu-id="dbbcb-146">Um [fone de ouvido (VR) de realidade mista do Windows](../../../discover/immersive-headset-hardware-details.md) ou [Microsoft HoloLens com o](/hololens/hololens1-hardware) modo de desenvolvedor habilitado</span><span class="sxs-lookup"><span data-stu-id="dbbcb-146">A [Windows Mixed Reality immersive (VR) headset](../../../discover/immersive-headset-hardware-details.md) or [Microsoft HoloLens](/hololens/hololens1-hardware) with Developer mode enabled</span></span>
- <span data-ttu-id="dbbcb-147">Uma câmera conectada ao seu PC (para desenvolvimento de headsets de imersão)</span><span class="sxs-lookup"><span data-stu-id="dbbcb-147">A camera connected to your PC (for immersive headset development)</span></span>
- <span data-ttu-id="dbbcb-148">Acesso à Internet para a instalação do Azure e recuperação de API da Pesquisa Visual Computacional</span><span class="sxs-lookup"><span data-stu-id="dbbcb-148">Internet access for Azure setup and Computer Vision API retrieval</span></span>

## <a name="before-you-start"></a><span data-ttu-id="dbbcb-149">Antes de começar</span><span class="sxs-lookup"><span data-stu-id="dbbcb-149">Before you start</span></span>

1.  <span data-ttu-id="dbbcb-150">Para evitar problemas de criação desse projeto, é altamente recomendável que você crie o projeto mencionado neste tutorial em uma pasta raiz ou quase raiz (caminhos de pasta longos podem causar problemas em tempo de compilação).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-150">To avoid encountering issues building this project, it is strongly suggested that you create the project mentioned in this tutorial in a root or near-root folder (long folder paths can cause issues at build-time).</span></span>
2.  <span data-ttu-id="dbbcb-151">Configure e teste seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-151">Set up and test your HoloLens.</span></span> <span data-ttu-id="dbbcb-152">Se você precisar de suporte para configurar seu HoloLens, [visite o artigo configuração do hololens](/hololens/hololens-setup).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-152">If you need support setting up your HoloLens, [make sure to visit the HoloLens setup article](/hololens/hololens-setup).</span></span> 
3.  <span data-ttu-id="dbbcb-153">É uma boa ideia executar a calibragem e o ajuste do sensor ao começar a desenvolver um novo aplicativo do HoloLens (às vezes, ele pode ajudar a executar essas tarefas para cada usuário).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-153">It is a good idea to perform Calibration and Sensor Tuning when beginning developing a new HoloLens App (sometimes it can help to perform those tasks for each user).</span></span> 

<span data-ttu-id="dbbcb-154">Para obter ajuda sobre calibragem, siga este [link para o artigo Calibration do HoloLens](/hololens/hololens-calibration#hololens-2).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-154">For help on Calibration, please follow this [link to the HoloLens Calibration article](/hololens/hololens-calibration#hololens-2).</span></span>

<span data-ttu-id="dbbcb-155">Para obter ajuda sobre o ajuste do sensor, siga este [link para o artigo de ajuste do sensor do HoloLens](/hololens/hololens-updates).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-155">For help on Sensor Tuning, please follow this [link to the HoloLens Sensor Tuning article](/hololens/hololens-updates).</span></span>

## <a name="chapter-1--the-azure-portal"></a><span data-ttu-id="dbbcb-156">Capítulo 1 – o portal do Azure</span><span class="sxs-lookup"><span data-stu-id="dbbcb-156">Chapter 1 – The Azure Portal</span></span>

<span data-ttu-id="dbbcb-157">Para usar o serviço de *API da pesquisa Visual computacional* no Azure, você precisará configurar uma instância do serviço a ser disponibilizada para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-157">To use the *Computer Vision API* service in Azure, you will need to configure an instance of the service to be made available to your application.</span></span>

1.  <span data-ttu-id="dbbcb-158">Primeiro, faça logon no [portal do Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-158">First, log in to the [Azure Portal](https://portal.azure.com).</span></span> 

    > [!NOTE]
    > <span data-ttu-id="dbbcb-159">Se você ainda não tiver uma conta do Azure, será necessário criar uma.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-159">If you do not already have an Azure account, you will need to create one.</span></span> <span data-ttu-id="dbbcb-160">Se você estiver seguindo este tutorial em uma situação de sala de aula ou laboratório, peça ao instrutor ou a uma das proctors para obter ajuda para configurar sua nova conta.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-160">If you are following this tutorial in a classroom or lab situation, ask your instructor or one of the proctors for help setting up your new account.</span></span>

2.  <span data-ttu-id="dbbcb-161">Depois de fazer logon, clique em **novo** no canto superior esquerdo e procure *API da pesquisa Visual computacional* e clique em **Enter**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-161">Once you are logged in, click on **New** in the top left corner, and search for *Computer Vision API*, and click **Enter**.</span></span>

    ![Criar um novo recurso no Azure](images/AzureLabs-Lab2-00.png)

    > [!NOTE]
    > <span data-ttu-id="dbbcb-163">A palavra **novo** pode ter sido substituída por **criar um recurso**, em portais mais recentes.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-163">The word **New** may have been replaced with **Create a resource**, in newer portals.</span></span>
 
3.  <span data-ttu-id="dbbcb-164">A nova página fornecerá uma descrição do serviço *API da pesquisa Visual computacional* .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-164">The new page will provide a description of the *Computer Vision API* service.</span></span> <span data-ttu-id="dbbcb-165">Na parte inferior esquerda desta página, selecione o botão **criar** para criar uma associação com esse serviço.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-165">At the bottom left of this page, select the **Create** button, to create an association with this service.</span></span>

    ![Sobre o serviço de API da pesquisa Visual computacional](images/AzureLabs-Lab2-01.png)
 
4.  <span data-ttu-id="dbbcb-167">Depois de clicar em **criar**:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-167">Once you have clicked on **Create**:</span></span>

    1. <span data-ttu-id="dbbcb-168">Insira o **nome** desejado para esta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-168">Insert your desired **Name** for this service instance.</span></span>
    2. <span data-ttu-id="dbbcb-169">Selecione uma **Assinatura**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-169">Select a **Subscription**.</span></span>
    3. <span data-ttu-id="dbbcb-170">Selecione o **tipo de preço** apropriado para você, se esta for a primeira vez que criar um serviço de *API da pesquisa Visual computacional* , uma camada gratuita (chamada F0) deverá estar disponível para você.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-170">Select the **Pricing Tier** appropriate for you, if this is the first time creating a *Computer Vision API* Service, a free tier (named F0) should be available to you.</span></span>
    4. <span data-ttu-id="dbbcb-171">Escolha um **grupo de recursos** ou crie um novo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-171">Choose a **Resource Group** or create a new one.</span></span> <span data-ttu-id="dbbcb-172">Um grupo de recursos fornece uma maneira de monitorar, controlar o acesso, provisionar e gerenciar a cobrança de uma coleção de ativos do Azure.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-172">A resource group provides a way to monitor, control access, provision and manage billing for a collection of Azure assets.</span></span> <span data-ttu-id="dbbcb-173">É recomendável manter todos os serviços do Azure associados a um único projeto (por exemplo, esses laboratórios) em um grupo de recursos comum).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-173">It is recommended to keep all the Azure services associated with a single project (e.g. such as these labs) under a common resource group).</span></span> 

        > <span data-ttu-id="dbbcb-174">Se você quiser ler mais sobre grupos de recursos do Azure, [visite o artigo grupo de recursos](/azure/azure-resource-manager/resource-group-portal).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-174">If you wish to read more about Azure Resource Groups, please [visit the resource group article](/azure/azure-resource-manager/resource-group-portal).</span></span>

    5. <span data-ttu-id="dbbcb-175">Determine o local do seu grupo de recursos (se você estiver criando um novo grupo de recursos).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-175">Determine the Location for your resource group (if you are creating a new Resource Group).</span></span> <span data-ttu-id="dbbcb-176">O local ideal seria na região em que o aplicativo seria executado.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-176">The location would ideally be in the region where the application would run.</span></span> <span data-ttu-id="dbbcb-177">Alguns ativos do Azure só estão disponíveis em determinadas regiões.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-177">Some Azure assets are only available in certain regions.</span></span>

    6. <span data-ttu-id="dbbcb-178">Você também precisará confirmar que entendeu os termos e condições aplicados a esse serviço.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-178">You will also need to confirm that you have understood the Terms and Conditions applied to this Service.</span></span>
    7. <span data-ttu-id="dbbcb-179">Clique em Criar.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-179">Click Create.</span></span>

        ![Informações de criação de serviço](images/AzureLabs-Lab2-02.png)

5.  <span data-ttu-id="dbbcb-181">Depois de clicar em **criar**, você precisará aguardar até que o serviço seja criado, isso pode levar um minuto.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-181">Once you have clicked on **Create**, you will have to wait for the service to be created, this might take a minute.</span></span>
6.  <span data-ttu-id="dbbcb-182">Uma notificação será exibida no portal assim que a instância do serviço for criada.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-182">A notification will appear in the portal once the Service instance is created.</span></span>

    ![Consulte a nova notificação para seu novo serviço](images/AzureLabs-Lab2-03.png) 
 
7.  <span data-ttu-id="dbbcb-184">Clique na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-184">Click on the notification to explore your new Service instance.</span></span> 

    ![Selecione o botão ir para o recurso.](images/AzureLabs-Lab2-04.png)
 
8. <span data-ttu-id="dbbcb-186">Clique no botão **ir para recurso** na notificação para explorar sua nova instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-186">Click the **Go to resource** button in the notification to explore your new Service instance.</span></span> <span data-ttu-id="dbbcb-187">Você será levado para sua nova instância do serviço API da Pesquisa Visual Computacional.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-187">You will be taken to your new Computer Vision API service instance.</span></span> 

    ![Sua nova imagem do serviço API da Pesquisa Visual Computacional](images/AzureLabs-Lab2-05.png)
 
9.  <span data-ttu-id="dbbcb-189">Neste tutorial, seu aplicativo precisará fazer chamadas para seu serviço, o que é feito por meio do uso da chave de assinatura do serviço.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-189">Within this tutorial, your application will need to make calls to your service, which is done through using your service’s Subscription Key.</span></span>
10. <span data-ttu-id="dbbcb-190">Na página *início rápido* , do seu serviço de *API da pesquisa Visual computacional* , navegue até a primeira etapa, *pegue as chaves* e clique em **chaves** (você também pode conseguir isso clicando nas teclas de hiperlink azul, localizadas no menu de navegação serviços, indicado pelo ícone de chave).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-190">From the *Quick start* page, of your *Computer Vision API* service, navigate to the first step, *Grab your keys*, and click **Keys** (you can also achieve this by clicking the blue hyperlink Keys, located in the services navigation menu, denoted by the key icon).</span></span> <span data-ttu-id="dbbcb-191">Isso revelará suas *chaves* de serviço.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-191">This will reveal your service *Keys*.</span></span>
11. <span data-ttu-id="dbbcb-192">Faça uma cópia de uma das chaves exibidas, pois você precisará dela posteriormente em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-192">Take a copy of one of the displayed keys, as you will need this later in your project.</span></span> 

12. <span data-ttu-id="dbbcb-193">Volte para a página *início rápido* e, a partir daí, busque seu ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-193">Go back to the *Quick start* page, and from there, fetch your endpoint.</span></span> <span data-ttu-id="dbbcb-194">Lembre-se de que seu pode ser diferente, dependendo de sua região (que, se for, você precisará fazer uma alteração no código posteriormente).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-194">Be aware yours may be different, depending on your region (which if it is, you will need to make a change to your code later).</span></span> <span data-ttu-id="dbbcb-195">Faça uma cópia deste ponto de extremidade para uso posterior:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-195">Take a copy of this endpoint for use later:</span></span>

    ![Seu novo serviço de API da Pesquisa Visual Computacional](images/AzureLabs-Lab2-05-5.png)

    > [!TIP]
    > <span data-ttu-id="dbbcb-197">Você pode verificar quais são os vários pontos de extremidade [aqui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-197">You can check what the various endpoints are [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span> 

## <a name="chapter-2--set-up-the-unity-project"></a><span data-ttu-id="dbbcb-198">Capítulo 2 – configurar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="dbbcb-198">Chapter 2 – Set up the Unity project</span></span>

<span data-ttu-id="dbbcb-199">A seguir está uma configuração típica para o desenvolvimento com realidade misturada e, como tal, é um bom modelo para outros projetos.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-199">The following is a typical set up for developing with mixed reality, and as such, is a good template for other projects.</span></span>

1.  <span data-ttu-id="dbbcb-200">Abra o *Unity* e clique em **novo**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-200">Open *Unity* and click **New**.</span></span> 

    ![Inicie o novo projeto do Unity.](images/AzureLabs-Lab2-06.png)

2.  <span data-ttu-id="dbbcb-202">Agora, você precisará fornecer um nome de projeto de Unity.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-202">You will now need to provide a Unity Project name.</span></span> <span data-ttu-id="dbbcb-203">Inserir **MR_ComputerVision**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-203">Insert **MR_ComputerVision**.</span></span> <span data-ttu-id="dbbcb-204">Verifique se o tipo de projeto está definido como **3D**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-204">Make sure the project type is set to **3D**.</span></span> <span data-ttu-id="dbbcb-205">Defina o **local** como algum lugar apropriado para você (Lembre-se de que, mais próximo de diretórios raiz é melhor).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-205">Set the **Location** to somewhere appropriate for you (remember, closer to root directories is better).</span></span> <span data-ttu-id="dbbcb-206">Em seguida, clique em **criar projeto**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-206">Then, click **Create project**.</span></span>

    ![Forneça detalhes para o novo projeto do Unity.](images/AzureLabs-Lab2-07.png)

3.  <span data-ttu-id="dbbcb-208">Com o Unity Open, vale a pena verificar se o **Editor de script** padrão está definido como **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-208">With Unity open, it is worth checking the default **Script Editor** is set to **Visual Studio**.</span></span> <span data-ttu-id="dbbcb-209">Vá para **Editar preferências de >** e, em seguida, na nova janela, navegue até **Ferramentas externas**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-209">Go to **Edit > Preferences** and then from the new window, navigate to **External Tools**.</span></span> <span data-ttu-id="dbbcb-210">Altere o **Editor de script externo** para o **Visual Studio 2017**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-210">Change **External Script Editor** to **Visual Studio 2017**.</span></span> <span data-ttu-id="dbbcb-211">Feche a janela **preferências** .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-211">Close the **Preferences** window.</span></span>

    ![Atualize a preferência do editor de script.](images/AzureLabs-Lab2-08.png)

4.  <span data-ttu-id="dbbcb-213">Em seguida, vá para **arquivo > configurações de Build** e selecione **plataforma universal do Windows** e, em seguida, clique no botão **alternar plataforma** para aplicar sua seleção.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-213">Next, go to **File > Build Settings** and select **Universal Windows Platform**, then click on the **Switch Platform** button to apply your selection.</span></span>

    ![Janela de configurações de compilação, alterne a plataforma para UWP.](images/AzureLabs-Lab2-10.png)

5.  <span data-ttu-id="dbbcb-215">Ainda no **arquivo > configurações de compilação** e certifique-se de que:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-215">While still in **File > Build Settings** and make sure that:</span></span>

    1. <span data-ttu-id="dbbcb-216">O **dispositivo de destino** está definido como **HoloLens**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-216">**Target Device** is set to **HoloLens**</span></span>

        > <span data-ttu-id="dbbcb-217">Para os headsets de imersão, defina **dispositivo de destino** para *qualquer dispositivo*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-217">For the immersive headsets, set **Target Device** to *Any Device*.</span></span>

    2. <span data-ttu-id="dbbcb-218">O **tipo de compilação** está definido como **D3D**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-218">**Build Type** is set to **D3D**</span></span>
    3. <span data-ttu-id="dbbcb-219">O **SDK** está definido para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-219">**SDK** is set to **Latest installed**</span></span>
    4. <span data-ttu-id="dbbcb-220">A **versão do Visual Studio** está definida para o **mais recente instalado**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-220">**Visual Studio Version** is set to **Latest installed**</span></span>
    5. <span data-ttu-id="dbbcb-221">**Compilar e executar** é definido como **computador local**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-221">**Build and Run** is set to **Local Machine**</span></span>
    6. <span data-ttu-id="dbbcb-222">Salve a cena e adicione-a à compilação.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-222">Save the scene and add it to the build.</span></span>

        1. <span data-ttu-id="dbbcb-223">Faça isso selecionando **Adicionar abrir cenas**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-223">Do this by selecting **Add Open Scenes**.</span></span> <span data-ttu-id="dbbcb-224">Uma janela salvar será exibida.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-224">A save window will appear.</span></span>
        
            ![Clique no botão Adicionar cenas abertas](images/AzureLabs-Lab2-11.png)

        2. <span data-ttu-id="dbbcb-226">Crie uma nova pasta para isso e qualquer cena futura, em seguida, selecione o botão **nova pasta** , para criar uma nova pasta, nomeie-a como **cenas**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-226">Create a new folder for this, and any future, scene, then select the **New folder** button, to create a new folder, name it **Scenes**.</span></span>

            ![Criar nova pasta de scripts](images/AzureLabs-Lab2-12.png)

        3. <span data-ttu-id="dbbcb-228">Abra sua pasta de **cenas** recém-criada e, no campo *nome do arquivo*:, digite **MR_ComputerVisionScene** e clique em **salvar**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-228">Open your newly created **Scenes** folder, and then in the *File name*: text field, type **MR_ComputerVisionScene**, then click **Save**.</span></span>

            ![Dê um nome à nova cena.](images/AzureLabs-Lab2-13.png)

            > <span data-ttu-id="dbbcb-230">Lembre-se de que você deve salvar as cenas do Unity na pasta *ativos* , pois elas devem ser associadas ao projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-230">Be aware, you must save your Unity scenes within the *Assets* folder, as they must be associated with the Unity Project.</span></span> <span data-ttu-id="dbbcb-231">Criar a pasta de cenas (e outras pastas semelhantes) é uma maneira típica de estruturar um projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-231">Creating the scenes folder (and other similar folders) is a typical way of structuring a Unity project.</span></span>

    7. <span data-ttu-id="dbbcb-232">As configurações restantes, em *configurações de compilação*, devem ser deixadas como padrão por enquanto.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-232">The remaining settings, in *Build Settings*, should be left as default for now.</span></span>

6. <span data-ttu-id="dbbcb-233">Na janela *configurações de compilação* , clique no botão **configurações do Player** , isso abrirá o painel relacionado no espaço onde o *Inspetor* está localizado.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-233">In the *Build Settings* window, click on the **Player Settings** button, this will open the related panel in the space where the *Inspector* is located.</span></span> 

    ![Abra as configurações do Player.](images/AzureLabs-Lab2-14.png)

7. <span data-ttu-id="dbbcb-235">Nesse painel, algumas configurações precisam ser verificadas:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-235">In this panel, a few settings need to be verified:</span></span>

    1. <span data-ttu-id="dbbcb-236">Na guia **outras configurações** :</span><span class="sxs-lookup"><span data-stu-id="dbbcb-236">In the **Other Settings** tab:</span></span>

        1. <span data-ttu-id="dbbcb-237">A **versão de tempo de execução de script** deve ser **estável** (.net 3,5 equivalente).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-237">**Scripting Runtime Version** should be **Stable** (.NET 3.5 Equivalent).</span></span>
        2. <span data-ttu-id="dbbcb-238">O **back-end de script** deve ser **.net**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-238">**Scripting Backend** should be **.NET**</span></span>
        3. <span data-ttu-id="dbbcb-239">O **nível de compatibilidade da API** deve ser **.NET 4,6**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-239">**API Compatibility Level** should be **.NET 4.6**</span></span>

            ![Atualize outras configurações.](images/AzureLabs-Lab2-15.png)
      
    2. <span data-ttu-id="dbbcb-241">Na guia **configurações de publicação** , em **recursos**, marque:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-241">Within the **Publishing Settings** tab, under **Capabilities**, check:</span></span>

        1. <span data-ttu-id="dbbcb-242">**InternetClient**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-242">**InternetClient**</span></span>
        2. <span data-ttu-id="dbbcb-243">**Webcam**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-243">**Webcam**</span></span>

            ![Atualizando configurações de publicação.](images/AzureLabs-Lab2-16.png)

    3. <span data-ttu-id="dbbcb-245">Mais adiante no painel, em **configurações de XR** (encontradas abaixo de **configurações de publicação**), **suporte à realidade virtual** em escala, verifique se o **SDK do Windows Mixed Reality** foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-245">Further down the panel, in **XR Settings** (found below **Publish Settings**), tick **Virtual Reality Supported**, make sure the **Windows Mixed Reality SDK** is added.</span></span>

        ![Atualize as configurações de X R.](images/AzureLabs-Lab2-17.png)

8.  <span data-ttu-id="dbbcb-247">De volta nas *configurações de Build* , projetos do _Unity C#_ não estão mais esmaecidos; Marque a caixa de seleção ao lado deste.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-247">Back in *Build Settings* _Unity C#_ Projects is no longer greyed out; tick the checkbox next to this.</span></span> 
9.  <span data-ttu-id="dbbcb-248">Feche a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-248">Close the Build Settings window.</span></span>
10. <span data-ttu-id="dbbcb-249">Salve sua cena e projeto (**arquivo > salvar cena/arquivo > salvar projeto**).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-249">Save your Scene and Project (**FILE > SAVE SCENE / FILE > SAVE PROJECT**).</span></span>

## <a name="chapter-3--main-camera-setup"></a><span data-ttu-id="dbbcb-250">Capítulo 3 – configuração principal da câmera</span><span class="sxs-lookup"><span data-stu-id="dbbcb-250">Chapter 3 – Main Camera setup</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dbbcb-251">Se você quiser ignorar o componente *de configuração do Unity* deste curso e continuar diretamente no código, fique à vontade para baixar esse [. unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), importe-o para seu projeto como um [pacote personalizado](https://docs.unity3d.com/Manual/AssetPackages.html)e, em seguida, continue no [capítulo 5](#chapter-5--create-the-resultslabel-class).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-251">If you wish to skip the *Unity Set up* component of this course, and continue straight into code, feel free to download this [.unitypackage](https://github.com/Microsoft/HolographicAcademy/raw/Azure-MixedReality-Labs/Azure%20Mixed%20Reality%20Labs/MR%20and%20Azure%20302%20-%20Computer%20vision/Azure-MR-302.unitypackage), import it into your project as a [Custom Package](https://docs.unity3d.com/Manual/AssetPackages.html), and then continue from [Chapter 5](#chapter-5--create-the-resultslabel-class).</span></span>

1.  <span data-ttu-id="dbbcb-252">No *painel hierarquia*, selecione a **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-252">In the *Hierarchy Panel*, select the **Main Camera**.</span></span> 
2.  <span data-ttu-id="dbbcb-253">Depois de selecionado, você poderá ver todos os componentes da **câmera principal** no *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-253">Once selected, you will be able to see all the components of the **Main Camera** in the *Inspector Panel*.</span></span>

    1. <span data-ttu-id="dbbcb-254">O **objeto de câmera** deve ser nomeado como a **câmera principal** (Observe a grafia!)</span><span class="sxs-lookup"><span data-stu-id="dbbcb-254">The **Camera object** must be named **Main Camera** (note the spelling!)</span></span>
    2. <span data-ttu-id="dbbcb-255">A **marca** da câmera principal deve ser definida como **MainCamera** (Observe a ortografia!)</span><span class="sxs-lookup"><span data-stu-id="dbbcb-255">The Main Camera **Tag** must be set to **MainCamera** (note the spelling!)</span></span>
    3. <span data-ttu-id="dbbcb-256">Verifique se a **posição de transformação** está definida como **0, 0,** 0</span><span class="sxs-lookup"><span data-stu-id="dbbcb-256">Make sure the **Transform Position** is set to **0, 0, 0**</span></span>
    4. <span data-ttu-id="dbbcb-257">Defina **limpar sinalizadores** como **cor sólida** (ignore isto para fone de ouvido de imersão).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-257">Set **Clear Flags** to **Solid Color** (ignore this for immersive headset).</span></span>
    5. <span data-ttu-id="dbbcb-258">Defina a cor do **plano de fundo** do componente da câmera como **preto, alfa 0 (código hex: #00000000)** (ignorar isso para headsets de imersão).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-258">Set the **Background** Color of the Camera Component to **Black, Alpha 0 (Hex Code: #00000000)** (ignore this for immersive headset).</span></span>

        ![Atualize os componentes da câmera.](images/AzureLabs-Lab2-18.png)
 
3.  <span data-ttu-id="dbbcb-260">Em seguida, você precisará criar um objeto "cursor" simples anexado à **câmera principal**, o que ajudará a posicionar a saída da análise de imagem quando o aplicativo estiver em execução.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-260">Next, you will have to create a simple “Cursor” object attached to the **Main Camera**, which will help you position the image analysis output when the application is running.</span></span> <span data-ttu-id="dbbcb-261">Esse cursor determinará o ponto central do foco da câmera.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-261">This Cursor will determine the center point of the camera focus.</span></span>

<span data-ttu-id="dbbcb-262">Para criar o cursor:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-262">To create the Cursor:</span></span>

1.  <span data-ttu-id="dbbcb-263">No *painel hierarquia*, clique com o botão direito do mouse na **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-263">In the *Hierarchy Panel*, right-click on the **Main Camera**.</span></span> <span data-ttu-id="dbbcb-264">Em **objeto 3D**, clique em **esfera**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-264">Under **3D Object**, click on **Sphere**.</span></span>

    ![Selecione o objeto de cursor.](images/AzureLabs-Lab2-19.png)
 
2.  <span data-ttu-id="dbbcb-266">Renomeie a **esfera** para **cursor** (clique duas vezes no objeto de cursor ou pressione o botão de teclado "F2" com o objeto selecionado) e verifique se ele está localizado como filho da **câmera principal**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-266">Rename the **Sphere** to **Cursor** (double click the Cursor object or press the ‘F2’ keyboard button with the object selected), and make sure it is located as child of the **Main Camera**.</span></span>

3.  <span data-ttu-id="dbbcb-267">No *painel hierarquia*, clique com o botão esquerdo do **cursor**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-267">In the *Hierarchy Panel*, left click on the **Cursor**.</span></span> <span data-ttu-id="dbbcb-268">Com o cursor selecionado, ajuste as seguintes variáveis no *painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-268">With the Cursor selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="dbbcb-269">Defina a *posição de transformação* como **0, 0, 5**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-269">Set the *Transform Position* to **0, 0, 5**</span></span>
    2. <span data-ttu-id="dbbcb-270">Defina a *escala* como **0, 2, 0, 2, 0, 2**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-270">Set the *Scale* to **0.02, 0.02, 0.02**</span></span>

        ![Atualize a posição e a escala de transformação.](images/AzureLabs-Lab2-20.png)
  
## <a name="chapter-4--setup-the-label-system"></a><span data-ttu-id="dbbcb-272">Capítulo 4 – configurar o sistema de etiquetas</span><span class="sxs-lookup"><span data-stu-id="dbbcb-272">Chapter 4 – Setup the Label system</span></span>

<span data-ttu-id="dbbcb-273">Depois de capturar uma imagem com a câmera do HoloLens, essa imagem será enviada para a instância do serviço de *API da pesquisa Visual computacional do Azure* para análise.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-273">Once you have captured an image with the HoloLens’ camera, that image will be sent to your *Azure Computer Vision API* Service instance for analysis.</span></span> 

<span data-ttu-id="dbbcb-274">Os resultados dessa análise serão uma lista de objetos reconhecidos chamados **marcas**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-274">The results of that analysis will be a list of recognized objects called **Tags**.</span></span> 

<span data-ttu-id="dbbcb-275">Você usará rótulos (como um texto 3D no espaço de mundo) para exibir essas marcas no local em que a foto foi tirada.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-275">You will use Labels (as a 3D text in world space) to display these Tags at the location the photo was taken.</span></span>

<span data-ttu-id="dbbcb-276">As etapas a seguir mostrarão como configurar o objeto **Label** .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-276">The following steps will show how to setup the **Label** object.</span></span>

1.  <span data-ttu-id="dbbcb-277">Clique com o botão direito do mouse em qualquer lugar no painel hierarquia (o local não importa nesse ponto), em **objeto 3D**, adicione um **texto 3D**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-277">Right-click anywhere in the Hierarchy Panel (the location does not matter at this point), under **3D Object**, add a **3D Text**.</span></span> <span data-ttu-id="dbbcb-278">Nomeie-o como **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-278">Name it **LabelText**.</span></span>

    ![Criar objeto de texto 3D.](images/AzureLabs-Lab2-21.png)
 
2.  <span data-ttu-id="dbbcb-280">No *painel hierarquia*, clique no botão esquerdo do **LabelText**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-280">In the *Hierarchy Panel*, left click on the **LabelText**.</span></span> <span data-ttu-id="dbbcb-281">Com o **LabelText** selecionado, ajuste as seguintes variáveis no *painel Inspetor*:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-281">With the **LabelText** selected, adjust the following variables in the *Inspector Panel*:</span></span>

    1. <span data-ttu-id="dbbcb-282">Defina a **posição** como **0, 0, 0**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-282">Set the **Position** to **0,0,0**</span></span>
    2. <span data-ttu-id="dbbcb-283">Defina a **escala** como **0, 1, 0, 1, 0, 1**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-283">Set the **Scale** to **0.01, 0.01, 0.01**</span></span>
    3. <span data-ttu-id="dbbcb-284">Na malha de **texto** do componente:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-284">In the component **Text Mesh**:</span></span>
    4. <span data-ttu-id="dbbcb-285">Substituir todo o texto no **texto**, por "..."</span><span class="sxs-lookup"><span data-stu-id="dbbcb-285">Replace all the text within **Text**, with "..."</span></span>        
    5. <span data-ttu-id="dbbcb-286">Definir a **âncora** para o **Centro central**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-286">Set the **Anchor** to **Middle Center**</span></span>
    6. <span data-ttu-id="dbbcb-287">Definir o **alinhamento** como **centralizado**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-287">Set the **Alignment** to **Center**</span></span>
    7. <span data-ttu-id="dbbcb-288">Defina o **tamanho da guia** como **4**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-288">Set the **Tab Size** to **4**</span></span>
    8. <span data-ttu-id="dbbcb-289">Defina o **tamanho da fonte** como **50**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-289">Set the **Font Size** to **50**</span></span>
    9. <span data-ttu-id="dbbcb-290">Defina a **cor** como **#FFFFFFFF**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-290">Set the **Color** to **#FFFFFFFF**</span></span>

    ![Componente de texto](images/AzureLabs-Lab2-21-5.png)

3.  <span data-ttu-id="dbbcb-292">Arraste o **LabelText** do *painel hierarquia* para a *pasta ativo*, dentro do *painel Projeto*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-292">Drag the **LabelText** from the *Hierarchy Panel*, into the *Asset Folder*, within in the *Project Panel*.</span></span> <span data-ttu-id="dbbcb-293">Isso fará com que o **LabelText** um pré-fabricado, para que possa ser instanciado no código.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-293">This will make the **LabelText** a Prefab, so that it can be instantiated in code.</span></span>

    ![Crie um pré-fabricado do objeto LabelText.](images/AzureLabs-Lab2-22.png)
 
4.  <span data-ttu-id="dbbcb-295">Você deve excluir o **LabelText** do *painel hierarquia*, de modo que ele não será exibido na cena de abertura.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-295">You should delete the **LabelText** from the *Hierarchy Panel*, so that it will not be displayed in the opening scene.</span></span> <span data-ttu-id="dbbcb-296">Como agora é um pré-fabricado, que você chamará para instâncias individuais da sua pasta de ativos, não há necessidade de mantê-la dentro da cena.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-296">As it is now a prefab, which you will call on for individual instances from your Assets folder, there is no need to keep it within the scene.</span></span> 
5.  <span data-ttu-id="dbbcb-297">A estrutura final do objeto no *painel hierarquia* deve ser parecida com a mostrada na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-297">The final object structure in the *Hierarchy Panel* should be like the one shown in the image below:</span></span>

    ![Estrutura final do painel de hierarquia.](images/AzureLabs-Lab2-23.png)

## <a name="chapter-5--create-the-resultslabel-class"></a><span data-ttu-id="dbbcb-299">Capítulo 5 – criar a classe ResultsLabel</span><span class="sxs-lookup"><span data-stu-id="dbbcb-299">Chapter 5 – Create the ResultsLabel class</span></span>

<span data-ttu-id="dbbcb-300">O primeiro script que você precisa criar é a classe *ResultsLabel* , que é responsável pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-300">The first script you need to create is the *ResultsLabel* class, which is responsible for the following:</span></span> 

- <span data-ttu-id="dbbcb-301">Criando os rótulos no espaço do mundo apropriado, em relação à posição da câmera.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-301">Creating the Labels in the appropriate world space, relative to the position of the Camera.</span></span>
- <span data-ttu-id="dbbcb-302">Exibindo as marcas da imagem Analysis.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-302">Displaying the Tags from the Image Anaysis.</span></span>

<span data-ttu-id="dbbcb-303">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-303">To create this class:</span></span> 

1.  <span data-ttu-id="dbbcb-304">Clique com o botão direito do mouse no *painel Projeto* e **crie > pasta**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-304">Right-click in the *Project Panel*, then **Create > Folder**.</span></span> <span data-ttu-id="dbbcb-305">Nomeie a pasta **scripts**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-305">Name the folder **Scripts**.</span></span> 

    ![Criar pasta de scripts.](images/AzureLabs-Lab2-24.png)

2.  <span data-ttu-id="dbbcb-307">Com a pasta **scripts** Create, clique duas vezes nela para abrir.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-307">With the **Scripts** folder create, double click it to open.</span></span> <span data-ttu-id="dbbcb-308">Em seguida, dentro dessa pasta, clique com o botão direito do mouse e selecione **criar >** em seguida **script C#**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-308">Then within that folder, right-click, and select **Create >** then **C# Script**.</span></span> <span data-ttu-id="dbbcb-309">Nomeie o script *ResultsLabel*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-309">Name the script *ResultsLabel*.</span></span> 

3.  <span data-ttu-id="dbbcb-310">Clique duas vezes no novo script *ResultsLabel* para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-310">Double click on the new *ResultsLabel* script to open it with **Visual Studio**.</span></span>

4.  <span data-ttu-id="dbbcb-311">Dentro da classe, insira o seguinte código na classe *ResultsLabel* :</span><span class="sxs-lookup"><span data-stu-id="dbbcb-311">Inside the Class insert the following code in the *ResultsLabel* class:</span></span>

    ```csharp
        using System.Collections.Generic;
        using UnityEngine;

        public class ResultsLabel : MonoBehaviour
        {   
            public static ResultsLabel instance;

            public GameObject cursor;

            public Transform labelPrefab;

            [HideInInspector]
            public Transform lastLabelPlaced;

            [HideInInspector]
            public TextMesh lastLabelPlacedText;

            private void Awake()
            {
                // allows this instance to behave like a singleton
                instance = this;
            }

            /// <summary>
            /// Instantiate a Label in the appropriate location relative to the Main Camera.
            /// </summary>
            public void CreateLabel()
            {
                lastLabelPlaced = Instantiate(labelPrefab, cursor.transform.position, transform.rotation);

                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // Change the text of the label to show that has been placed
                // The final text will be set at a later stage
                lastLabelPlacedText.text = "Analysing...";
            }

            /// <summary>
            /// Set the Tags as Text of the last Label created. 
            /// </summary>
            public void SetTagsToLastLabel(Dictionary<string, float> tagsDictionary)
            {
                lastLabelPlacedText = lastLabelPlaced.GetComponent<TextMesh>();

                // At this point we go through all the tags received and set them as text of the label
                lastLabelPlacedText.text = "I see: \n";

                foreach (KeyValuePair<string, float> tag in tagsDictionary)
                {
                    lastLabelPlacedText.text += tag.Key + ", Confidence: " + tag.Value.ToString("0.00 \n");
                }    
            }
        }
    ```

6.  <span data-ttu-id="dbbcb-312">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-312">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
7.  <span data-ttu-id="dbbcb-313">De volta ao *Editor do Unity*, clique e arraste a classe *ResultsLabel* da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-313">Back in the *Unity Editor*, click and drag the *ResultsLabel* class from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span>
8.  <span data-ttu-id="dbbcb-314">Clique na **câmera principal** e examine o *painel Inspetor*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-314">Click on the **Main Camera** and look at the *Inspector Panel*.</span></span>

<span data-ttu-id="dbbcb-315">Você observará que, a partir do script que acabou de arrastar para a câmera, há dois campos: **cursor** e **Label pré-fabricado**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-315">You will notice that from the script you just dragged into the Camera, there are two fields: **Cursor** and **Label Prefab**.</span></span>

9.  <span data-ttu-id="dbbcb-316">Arraste o objeto chamado **cursor** do *painel hierarquia* para o slot chamado **cursor**, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-316">Drag the object called **Cursor** from the *Hierarchy Panel* to the slot named **Cursor**, as shown in the image below.</span></span>
10. <span data-ttu-id="dbbcb-317">Arraste o objeto chamado **LabelText** da *pasta ativos* no *painel Projeto* para o slot chamado **rótulo pré-fabricado**, conforme mostrado na imagem abaixo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-317">Drag the object called **LabelText** from the *Assets Folder* in the *Project Panel* to the slot named **Label Prefab**, as shown in the image below.</span></span> 

    ![Defina os destinos de referência no Unity.](images/AzureLabs-Lab2-25.png)

## <a name="chapter-6--create-the-imagecapture-class"></a><span data-ttu-id="dbbcb-319">Capítulo 6 – criar a classe ImageCapture</span><span class="sxs-lookup"><span data-stu-id="dbbcb-319">Chapter 6 – Create the ImageCapture class</span></span>

<span data-ttu-id="dbbcb-320">A próxima classe que você vai criar é a classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-320">The next class you are going to create is the *ImageCapture* class.</span></span> <span data-ttu-id="dbbcb-321">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-321">This class is responsible for:</span></span>

-   <span data-ttu-id="dbbcb-322">Capturando uma imagem usando a câmera do HoloLens e armazenando-a na pasta do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-322">Capturing an Image using the HoloLens Camera and storing it in the App Folder.</span></span>
-   <span data-ttu-id="dbbcb-323">Capturando gestos de toque do usuário.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-323">Capturing Tap gestures from the user.</span></span>

<span data-ttu-id="dbbcb-324">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-324">To create this class:</span></span> 

1.  <span data-ttu-id="dbbcb-325">Vá para a pasta **scripts** que você criou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-325">Go to the **Scripts** folder you created previously.</span></span> 
2.  <span data-ttu-id="dbbcb-326">Clique com o botão direito do mouse dentro da pasta, **crie > script C#**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-326">Right-click inside the folder, **Create > C# Script**.</span></span> <span data-ttu-id="dbbcb-327">Chame o script *ImageCapture*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-327">Call the script *ImageCapture*.</span></span> 
3.  <span data-ttu-id="dbbcb-328">Clique duas vezes no novo script *ImageCapture* para abri-lo com o **Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-328">Double click on the new *ImageCapture* script to open it with **Visual Studio**.</span></span>
4.  <span data-ttu-id="dbbcb-329">Adicione os seguintes namespaces à parte superior do arquivo:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-329">Add the following namespaces to the top of the file:</span></span>

    ```csharp
        using System.IO;
        using System.Linq;
        using UnityEngine;
        using UnityEngine.XR.WSA.Input;
        using UnityEngine.XR.WSA.WebCam;
    ```

5.  <span data-ttu-id="dbbcb-330">Em seguida, adicione as seguintes variáveis dentro da classe *ImageCapture* , acima do método *Start ()* :</span><span class="sxs-lookup"><span data-stu-id="dbbcb-330">Then add the following variables inside the *ImageCapture* class, above the *Start()* method:</span></span>

    ```csharp
        public static ImageCapture instance; 
        public int tapsCount;
        private PhotoCapture photoCaptureObject = null;
        private GestureRecognizer recognizer;
        private bool currentlyCapturing = false;
    ```
 
<span data-ttu-id="dbbcb-331">A variável **tapsCount** armazenará o número de gestos de toque capturados do usuário.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-331">The **tapsCount** variable will store the number of tap gestures captured from the user.</span></span> <span data-ttu-id="dbbcb-332">Esse número é usado na nomenclatura das imagens capturadas.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-332">This number is used in the naming of the images captured.</span></span>

6.  <span data-ttu-id="dbbcb-333">O código para os métodos *ativo ()* e *Iniciar ()* agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-333">Code for *Awake()* and *Start()* methods now needs to be added.</span></span> <span data-ttu-id="dbbcb-334">Eles serão chamados quando a classe for inicializada:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-334">These will be called when the class initializes:</span></span>

    ```csharp
        private void Awake()
        {
            // Allows this instance to behave like a singleton
            instance = this;
        }

        void Start()
        {
            // subscribing to the HoloLens API gesture recognizer to track user gestures
            recognizer = new GestureRecognizer();
            recognizer.SetRecognizableGestures(GestureSettings.Tap);
            recognizer.Tapped += TapHandler;
            recognizer.StartCapturingGestures();
        }
    ```

7.  <span data-ttu-id="dbbcb-335">Implemente um manipulador que será chamado quando ocorrer um gesto de toque.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-335">Implement a handler that will be called when a Tap gesture occurs.</span></span> 

    ```csharp
        /// <summary>
        /// Respond to Tap Input.
        /// </summary>
        private void TapHandler(TappedEventArgs obj)
        {
            // Only allow capturing, if not currently processing a request.
            if(currentlyCapturing == false)
            {
                currentlyCapturing = true;
            
                // increment taps count, used to name images when saving
                tapsCount++;

                // Create a label in world space using the ResultsLabel class
                ResultsLabel.instance.CreateLabel();

                // Begins the image capture and analysis procedure
                ExecuteImageCaptureAndAnalysis();
            }
        }
    ```
 
<span data-ttu-id="dbbcb-336">O método *TapHandler ()* incrementa o número de toques capturados do usuário e usa a posição atual do cursor para determinar onde posicionar um novo rótulo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-336">The *TapHandler()* method increments the number of taps captured from the user and uses the current Cursor position to determine where to position a new Label.</span></span>

<span data-ttu-id="dbbcb-337">Esse método chama o método *ExecuteImageCaptureAndAnalysis ()* para iniciar a funcionalidade principal deste aplicativo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-337">This method then calls the *ExecuteImageCaptureAndAnalysis()* method to begin the core functionality of this application.</span></span>

8.  <span data-ttu-id="dbbcb-338">Depois que uma imagem for capturada e armazenada, os seguintes manipuladores serão chamados.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-338">Once an Image has been captured and stored, the following handlers will be called.</span></span> <span data-ttu-id="dbbcb-339">Se o processo for bem-sucedido, o resultado será passado para o *visionmanager* (que você ainda deseja criar) para análise.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-339">If the process is successful, the result is passed to the *VisionManager* (which you are yet to create) for analysis.</span></span>

    ```csharp
        /// <summary>
        /// Register the full execution of the Photo Capture. If successful, it will begin 
        /// the Image Analysis process.
        /// </summary>
        void OnCapturedPhotoToDisk(PhotoCapture.PhotoCaptureResult result)
        {
            // Call StopPhotoMode once the image has successfully captured
            photoCaptureObject.StopPhotoModeAsync(OnStoppedPhotoMode);
        }

        void OnStoppedPhotoMode(PhotoCapture.PhotoCaptureResult result)
        {
            // Dispose from the object in memory and request the image analysis 
            // to the VisionManager class
            photoCaptureObject.Dispose();
            photoCaptureObject = null;
            StartCoroutine(VisionManager.instance.AnalyseLastImageCaptured()); 
        }
    ```
 
9.  <span data-ttu-id="dbbcb-340">Em seguida, adicione o método que o aplicativo usa para iniciar o processo de captura de imagem e armazenar a imagem.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-340">Then add the method that the application uses to start the Image capture process and store the image.</span></span>

    ```csharp    
        /// <summary>    
        /// Begin process of Image Capturing and send To Azure     
        /// Computer Vision service.   
        /// </summary>    
        private void ExecuteImageCaptureAndAnalysis()  
        {    
            // Set the camera resolution to be the highest possible    
            Resolution cameraResolution = PhotoCapture.SupportedResolutions.OrderByDescending((res) => res.width * res.height).First();    

            Texture2D targetTexture = new Texture2D(cameraResolution.width, cameraResolution.height);
    
            // Begin capture process, set the image format    
            PhotoCapture.CreateAsync(false, delegate (PhotoCapture captureObject)    
            {    
                photoCaptureObject = captureObject;    
                CameraParameters camParameters = new CameraParameters();    
                camParameters.hologramOpacity = 0.0f;    
                camParameters.cameraResolutionWidth = targetTexture.width;    
                camParameters.cameraResolutionHeight = targetTexture.height;    
                camParameters.pixelFormat = CapturePixelFormat.BGRA32;
    
                // Capture the image from the camera and save it in the App internal folder    
                captureObject.StartPhotoModeAsync(camParameters, delegate (PhotoCapture.PhotoCaptureResult result)
                {    
                    string filename = string.Format(@"CapturedImage{0}.jpg", tapsCount);
    
                    string filePath = Path.Combine(Application.persistentDataPath, filename);

                    VisionManager.instance.imagePath = filePath;
    
                    photoCaptureObject.TakePhotoAsync(filePath, PhotoCaptureFileOutputFormat.JPG, OnCapturedPhotoToDisk);

                    currentlyCapturing = false;
                });   
            });    
        }
    ```
 
> [!WARNING] 
> <span data-ttu-id="dbbcb-341">Neste ponto, você observará um erro exibido no *painel de console do editor do Unity*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-341">At this point you will notice an error appearing in the *Unity Editor Console Panel*.</span></span> <span data-ttu-id="dbbcb-342">Isso ocorre porque o código faz referência à classe *visionmanager* que você criará no próximo capítulo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-342">This is because the code references the *VisionManager* class which you will create in the next Chapter.</span></span>

## <a name="chapter-7--call-to-azure-and-image-analysis"></a><span data-ttu-id="dbbcb-343">Capítulo 7 – chamar o Azure e a análise de imagem</span><span class="sxs-lookup"><span data-stu-id="dbbcb-343">Chapter 7 – Call to Azure and Image Analysis</span></span>

<span data-ttu-id="dbbcb-344">O último script que você precisa criar é a classe *visionmanager* .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-344">The last script you need to create is the *VisionManager* class.</span></span> 

<span data-ttu-id="dbbcb-345">Essa classe é responsável por:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-345">This class is responsible for:</span></span>

-   <span data-ttu-id="dbbcb-346">Carregando a imagem mais recente capturada como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-346">Loading the latest image captured as an array of bytes.</span></span>
-   <span data-ttu-id="dbbcb-347">Enviando a matriz de bytes para a instância do serviço de *API da pesquisa Visual computacional do Azure* para análise.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-347">Sending the byte array to your *Azure Computer Vision API* Service instance for analysis.</span></span>
-   <span data-ttu-id="dbbcb-348">Recebendo a resposta como uma cadeia de caracteres JSON.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-348">Receiving the response as a JSON string.</span></span>
-   <span data-ttu-id="dbbcb-349">Desserializar a resposta e passar as marcas resultantes para a classe *ResultsLabel* .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-349">Deserializing the response and passing the resulting Tags to the *ResultsLabel* class.</span></span>
 
<span data-ttu-id="dbbcb-350">Para criar esta classe:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-350">To create this class:</span></span>

1.  <span data-ttu-id="dbbcb-351">Clique duas vezes na pasta **scripts** para abri-la.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-351">Double click on the **Scripts** folder, to open it.</span></span> 
2.  <span data-ttu-id="dbbcb-352">Clique com o botão direito do mouse na pasta **scripts** , clique em **criar > script C#**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-352">Right-click inside the **Scripts** folder, click **Create > C# Script**.</span></span> <span data-ttu-id="dbbcb-353">Nomeie o script *visionmanager*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-353">Name the script *VisionManager*.</span></span> 
3.  <span data-ttu-id="dbbcb-354">Clique duas vezes no novo script para abri-lo com o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-354">Double click on the new script to open it with Visual Studio.</span></span>
4.  <span data-ttu-id="dbbcb-355">Atualize os namespaces para que sejam iguais aos seguintes, na parte superior da classe *visionmanager* :</span><span class="sxs-lookup"><span data-stu-id="dbbcb-355">Update the namespaces to be the same as the following, at the top of the *VisionManager* class:</span></span>

    ```csharp
        using System;
        using System.Collections;
        using System.Collections.Generic;
        using System.IO;
        using UnityEngine;
        using UnityEngine.Networking;
    ```
 
5.  <span data-ttu-id="dbbcb-356">Na parte superior do seu script, *dentro* da classe *visionmanager* (acima do método *Start ()* ), agora você precisa criar duas *classes* que irão representar a resposta JSON desserializada do Azure:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-356">At the top of your script, *inside* the *VisionManager* class (above the *Start()* method), you now need to create two *Classes* that will represent the deserialized JSON response from Azure:</span></span>

    ```csharp
        [System.Serializable]
        public class TagData
        {
            public string name;
            public float confidence;
        }

        [System.Serializable]
        public class AnalysedObject
        {
            public TagData[] tags;
            public string requestId;
            public object metadata;
        }
    ```

    > [!NOTE] 
    > <span data-ttu-id="dbbcb-357">As classes *TagData* e *AnalysedObject* precisam ter o atributo *[System. Serializable]* adicionado antes que a declaração possa ser desserializada com as bibliotecas do Unity.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-357">The *TagData* and *AnalysedObject* classes need to have the *[System.Serializable]* attribute added before the declaration to be able to be deserialized with the Unity libraries.</span></span>

6.  <span data-ttu-id="dbbcb-358">Na classe Visionmanager, você deve adicionar as seguintes variáveis:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-358">In the VisionManager class, you should add the following variables:</span></span>

    ```csharp
        public static VisionManager instance;

        // you must insert your service key here!    
        private string authorizationKey = "- Insert your key here -";    
        private const string ocpApimSubscriptionKeyHeader = "Ocp-Apim-Subscription-Key";
        private string visionAnalysisEndpoint = "https://westus.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags";   // This is where you need to update your endpoint, if you set your location to something other than west-us.
  
        internal byte[] imageBytes;

        internal string imagePath;
    ```

    > [!WARNING] 
    > <span data-ttu-id="dbbcb-359">Certifique-se de inserir sua **chave de autenticação** na variável **authorizationKey** .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-359">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span> <span data-ttu-id="dbbcb-360">Você terá anotado sua **chave de autenticação** no início deste curso, [capítulo 1](#chapter-1--the-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-360">You will have noted your **Auth Key** at the beginning of this course, [Chapter 1](#chapter-1--the-azure-portal).</span></span>

    > [!WARNING] 
    > <span data-ttu-id="dbbcb-361">A variável **visionAnalysisEndpoint** pode ser diferente da especificada neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-361">The **visionAnalysisEndpoint** variable might differ from the one specified in this example.</span></span> <span data-ttu-id="dbbcb-362">O **oeste-US** se refere estritamente a instâncias de serviço criadas para a região oeste dos EUA.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-362">The **west-us** strictly refers to Service instances created for the West US region.</span></span> <span data-ttu-id="dbbcb-363">Atualize isso com a [URL do ponto de extremidade](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); Aqui estão alguns exemplos de como isso pode ser:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-363">Update this with your [endpoint URL](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa); here are some examples of what that might look like:</span></span>
    > - <span data-ttu-id="dbbcb-364">Europa Ocidental: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="dbbcb-364">West Europe: `https://westeurope.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="dbbcb-365">Sudeste da Ásia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="dbbcb-365">Southeast Asia: `https://southeastasia.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>
    > - <span data-ttu-id="dbbcb-366">Leste da Austrália: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span><span class="sxs-lookup"><span data-stu-id="dbbcb-366">Australia East: `https://australiaeast.api.cognitive.microsoft.com/vision/v1.0/analyze?visualFeatures=Tags`</span></span>

7.  <span data-ttu-id="dbbcb-367">O código para ativo agora precisa ser adicionado.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-367">Code for Awake now needs to be added.</span></span> 

    ```csharp
        private void Awake()
        {
            // allows this instance to behave like a singleton
            instance = this;
        }
    ```

8.  <span data-ttu-id="dbbcb-368">Em seguida, adicione a corrotina (com o método de fluxo estático abaixo dela), que obterá os resultados da análise da imagem capturada pela classe *ImageCapture* .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-368">Next, add the coroutine (with the static stream method below it), which will obtain the results of the analysis of the image captured by the *ImageCapture* Class.</span></span> 

    ```csharp
        /// <summary>
        /// Call the Computer Vision Service to submit the image.
        /// </summary>
        public IEnumerator AnalyseLastImageCaptured()
        {
            WWWForm webForm = new WWWForm();
            using (UnityWebRequest unityWebRequest = UnityWebRequest.Post(visionAnalysisEndpoint, webForm))
            {
                // gets a byte array out of the saved image
                imageBytes = GetImageAsByteArray(imagePath);
                unityWebRequest.SetRequestHeader("Content-Type", "application/octet-stream");
                unityWebRequest.SetRequestHeader(ocpApimSubscriptionKeyHeader, authorizationKey);

                // the download handler will help receiving the analysis from Azure
                unityWebRequest.downloadHandler = new DownloadHandlerBuffer();

                // the upload handler will help uploading the byte array with the request
                unityWebRequest.uploadHandler = new UploadHandlerRaw(imageBytes);
                unityWebRequest.uploadHandler.contentType = "application/octet-stream";

                yield return unityWebRequest.SendWebRequest();

                long responseCode = unityWebRequest.responseCode;     

                try
                {
                    string jsonResponse = null;
                    jsonResponse = unityWebRequest.downloadHandler.text;

                    // The response will be in Json format
                    // therefore it needs to be deserialized into the classes AnalysedObject and TagData
                    AnalysedObject analysedObject = new AnalysedObject();
                    analysedObject = JsonUtility.FromJson<AnalysedObject>(jsonResponse);

                    if (analysedObject.tags == null)
                    {
                        Debug.Log("analysedObject.tagData is null");
                    }
                    else
                    {
                        Dictionary<string, float> tagsDictionary = new Dictionary<string, float>();

                        foreach (TagData td in analysedObject.tags)
                        {
                            TagData tag = td as TagData;
                            tagsDictionary.Add(tag.name, tag.confidence);                            
                        }

                        ResultsLabel.instance.SetTagsToLastLabel(tagsDictionary);
                    }
                }
                catch (Exception exception)
                {
                    Debug.Log("Json exception.Message: " + exception.Message);
                }

                yield return null;
            }
        }
    ```

    ```csharp
        /// <summary>
        /// Returns the contents of the specified file as a byte array.
        /// </summary>
        private static byte[] GetImageAsByteArray(string imageFilePath)
        {
            FileStream fileStream = new FileStream(imageFilePath, FileMode.Open, FileAccess.Read);
            BinaryReader binaryReader = new BinaryReader(fileStream);
            return binaryReader.ReadBytes((int)fileStream.Length);
        }  
    ```

9.  <span data-ttu-id="dbbcb-369">Certifique-se de salvar suas alterações no *Visual Studio* antes de retornar ao *Unity*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-369">Be sure to save your changes in *Visual Studio* before returning to *Unity*.</span></span>
10. <span data-ttu-id="dbbcb-370">De volta ao editor do Unity, clique e arraste as classes *visionmanager* e *ImageCapture* da pasta **scripts** para o objeto da **câmera principal** no *painel hierarquia*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-370">Back in the Unity Editor, click and drag the *VisionManager* and *ImageCapture* classes from the **Scripts** folder to the **Main Camera** object in the *Hierarchy Panel*.</span></span> 

## <a name="chapter-8--before-building"></a><span data-ttu-id="dbbcb-371">Capítulo 8 – antes de Compilar</span><span class="sxs-lookup"><span data-stu-id="dbbcb-371">Chapter 8 – Before building</span></span>

<span data-ttu-id="dbbcb-372">Para executar um teste completo de seu aplicativo, você precisará Sideload-lo no seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-372">To perform a thorough test of your application you will need to sideload it onto your HoloLens.</span></span>
<span data-ttu-id="dbbcb-373">Antes de fazer isso, verifique se:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-373">Before you do, ensure that:</span></span>

-   <span data-ttu-id="dbbcb-374">Todas as configurações mencionadas no [capítulo 2](#chapter-2--set-up-the-unity-project) estão definidas corretamente.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-374">All the settings mentioned in [Chapter 2](#chapter-2--set-up-the-unity-project) are set correctly.</span></span> 
-   <span data-ttu-id="dbbcb-375">Todos os scripts são anexados ao objeto da **câmera principal** .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-375">All the scripts are attached to the **Main Camera** object.</span></span> 
-   <span data-ttu-id="dbbcb-376">Todos os campos no *painel principal do Inspetor de câmera* são atribuídos corretamente.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-376">All the fields in the *Main Camera Inspector Panel* are assigned properly.</span></span>
-   <span data-ttu-id="dbbcb-377">Certifique-se de inserir sua **chave de autenticação** na variável **authorizationKey** .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-377">Make sure you insert your **Auth Key** into the **authorizationKey** variable.</span></span>
-   <span data-ttu-id="dbbcb-378">Verifique se você também verificou seu ponto de extremidade em seu script do *visionmanager* e se ele está alinhado à *sua* região (este documento usa o *Oeste-EUA* por padrão).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-378">Ensure that you have also checked your endpoint in your *VisionManager* script, and that it aligns to *your* region (this document uses *west-us* by default).</span></span>

## <a name="chapter-9--build-the-uwp-solution-and-sideload-the-application"></a><span data-ttu-id="dbbcb-379">Capítulo 9 – criar a solução UWP e sideloadr o aplicativo</span><span class="sxs-lookup"><span data-stu-id="dbbcb-379">Chapter 9 – Build the UWP Solution and sideload the application</span></span>
<span data-ttu-id="dbbcb-380">Tudo o que é necessário para a seção do Unity deste projeto foi concluído, portanto, é hora de compilá-lo a partir do Unity.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-380">Everything needed for the Unity section of this project has now been completed, so it is time to build it from Unity.</span></span>

1.  <span data-ttu-id="dbbcb-381">Navegue até *criar configurações*  -  **arquivo > configurações de Build...**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-381">Navigate to *Build Settings* - **File > Build Settings…**</span></span>
2.  <span data-ttu-id="dbbcb-382">Na janela *configurações de compilação* , clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-382">From the *Build Settings* window, click **Build**.</span></span>

    ![Compilando o aplicativo do Unity](images/AzureLabs-Lab2-26.png)

3.  <span data-ttu-id="dbbcb-384">Se ainda não estiver, **projetos do Tick Unity C#**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-384">If not already, tick **Unity C# Projects**.</span></span>
4.  <span data-ttu-id="dbbcb-385">Clique em **Compilar**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-385">Click **Build**.</span></span> <span data-ttu-id="dbbcb-386">O Unity iniciará uma janela *Explorador de arquivos* , onde você precisará criar e, em seguida, selecionar uma pasta na qual o aplicativo será compilado.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-386">Unity will launch a *File Explorer* window, where you need to create and then select a folder to build the app into.</span></span> <span data-ttu-id="dbbcb-387">Crie essa pasta agora e nomeie-a como *aplicativo*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-387">Create that folder now, and name it *App*.</span></span> <span data-ttu-id="dbbcb-388">Em seguida, com a pasta de *aplicativo* selecionada, pressione **Selecionar pasta**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-388">Then with the *App* folder selected, press **Select Folder**.</span></span> 
5.  <span data-ttu-id="dbbcb-389">O Unity começará a criar seu projeto na pasta do *aplicativo* .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-389">Unity will begin building your project to the *App* folder.</span></span> 
6.  <span data-ttu-id="dbbcb-390">Depois que o Unity terminar a compilação (pode levar algum tempo), ele abrirá uma janela do *Explorador de arquivos* no local de sua compilação (verifique sua barra de tarefas, pois ela nem sempre aparecerá acima das janelas, mas o notificará sobre a adição de uma nova janela).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-390">Once Unity has finished building (it might take some time), it will open a *File Explorer* window at the location of your build (check your task bar, as it may not always appear above your windows, but will notify you of the addition of a new window).</span></span>

## <a name="chapter-10--deploy-to-hololens"></a><span data-ttu-id="dbbcb-391">Capítulo 10 – implantar no HoloLens</span><span class="sxs-lookup"><span data-stu-id="dbbcb-391">Chapter 10 – Deploy to HoloLens</span></span>

<span data-ttu-id="dbbcb-392">Para implantar no HoloLens:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-392">To deploy on HoloLens:</span></span>

1.  <span data-ttu-id="dbbcb-393">Você precisará do endereço IP do seu HoloLens (para implantação remota) e para garantir que seu HoloLens esteja no **modo de desenvolvedor**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-393">You will need the IP Address of your HoloLens (for Remote Deploy), and to ensure your HoloLens is in **Developer Mode**.</span></span> <span data-ttu-id="dbbcb-394">Para fazer isso:</span><span class="sxs-lookup"><span data-stu-id="dbbcb-394">To do this:</span></span>

    1. <span data-ttu-id="dbbcb-395">Enquanto estiver desgastando seu HoloLens, abra as **configurações**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-395">Whilst wearing your HoloLens, open the **Settings**.</span></span>
    2. <span data-ttu-id="dbbcb-396">Vá para **rede & Internet > Wi-Fi > opções avançadas**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-396">Go to **Network & Internet > Wi-Fi > Advanced Options**</span></span>
    3. <span data-ttu-id="dbbcb-397">Anote o endereço **IPv4** .</span><span class="sxs-lookup"><span data-stu-id="dbbcb-397">Note the **IPv4** address.</span></span>
    4. <span data-ttu-id="dbbcb-398">Em seguida, navegue de volta para **configurações** e, em seguida, **atualize & > de segurança para desenvolvedores**</span><span class="sxs-lookup"><span data-stu-id="dbbcb-398">Next, navigate back to **Settings**, and then to **Update & Security > For Developers**</span></span> 
    5. <span data-ttu-id="dbbcb-399">Defina o modo de desenvolvedor em.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-399">Set Developer Mode On.</span></span>

2.  <span data-ttu-id="dbbcb-400">Navegue até sua nova compilação do Unity (a pasta do *aplicativo* ) e abra o arquivo de solução com o *Visual Studio*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-400">Navigate to your new Unity build (the *App* folder) and open the solution file with *Visual Studio*.</span></span>
3.  <span data-ttu-id="dbbcb-401">Na configuração da solução, selecione **depurar**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-401">In the Solution Configuration select **Debug**.</span></span>
4.  <span data-ttu-id="dbbcb-402">Na plataforma da solução, selecione **x86**, **computador remoto**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-402">In the Solution Platform, select **x86**, **Remote Machine**.</span></span> 

    ![Implante a solução do Visual Studio.](images/AzureLabs-Lab2-27.png)
 
5.  <span data-ttu-id="dbbcb-404">Vá para o **menu Compilar** e clique em **implantar solução** para Sideload o aplicativo ao seu HoloLens.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-404">Go to the **Build menu** and click on **Deploy Solution**, to sideload the application to your HoloLens.</span></span>
6.  <span data-ttu-id="dbbcb-405">Seu aplicativo agora deve aparecer na lista de aplicativos instalados em seu HoloLens, pronto para ser iniciado!</span><span class="sxs-lookup"><span data-stu-id="dbbcb-405">Your App should now appear in the list of installed apps on your HoloLens, ready to be launched!</span></span>

> [!NOTE]
> <span data-ttu-id="dbbcb-406">Para implantar em headsets de imersão, defina a **plataforma da solução** como *computador local* e defina a **configuração** a ser *depurada*, com *x86* como a **plataforma**.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-406">To deploy to immersive headset, set the **Solution Platform** to *Local Machine*, and set the **Configuration** to *Debug*, with *x86* as the **Platform**.</span></span> <span data-ttu-id="dbbcb-407">Em seguida, implante no computador local, usando o **menu Compilar**, selecionando *implantar solução*.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-407">Then deploy to the local machine, using the **Build menu**, selecting *Deploy Solution*.</span></span> 

## <a name="your-finished-computer-vision-api-application"></a><span data-ttu-id="dbbcb-408">Seu aplicativo API da Pesquisa Visual Computacional concluído</span><span class="sxs-lookup"><span data-stu-id="dbbcb-408">Your finished Computer Vision API application</span></span>

<span data-ttu-id="dbbcb-409">Parabéns, você criou um aplicativo de realidade misturada que aproveita a API da Pesquisa Visual Computacional do Azure para reconhecer objetos do mundo real e exibir a confiança do que foi visto.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-409">Congratulations, you built a mixed reality app that leverages the Azure Computer Vision API to recognize real world objects, and display confidence of what has been seen.</span></span>

![resultado do laboratório](images/AzureLabs-Lab2-000.png)

## <a name="bonus-exercises"></a><span data-ttu-id="dbbcb-411">Exercícios de bônus</span><span class="sxs-lookup"><span data-stu-id="dbbcb-411">Bonus exercises</span></span>

### <a name="exercise-1"></a><span data-ttu-id="dbbcb-412">Exercício 1</span><span class="sxs-lookup"><span data-stu-id="dbbcb-412">Exercise 1</span></span>

<span data-ttu-id="dbbcb-413">Assim como você usou o parâmetro *Tags* (como evidenciado no ponto de *extremidade* usado no *visionmanager*), estenda o aplicativo para detectar outras informações; Veja a quais outros parâmetros você tem acesso [aqui](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span><span class="sxs-lookup"><span data-stu-id="dbbcb-413">Just as you have used the *Tags* parameter (as evidenced within the *endpoint* used within the *VisionManager*), extend the app to detect other information; have a look at what other parameters you have access to [HERE](https://westus.dev.cognitive.microsoft.com/docs/services/56f91f2d778daf23d8ec6739/operations/56f91f2e778daf14a499e1fa).</span></span>

### <a name="exercise-2"></a><span data-ttu-id="dbbcb-414">Exercício 2</span><span class="sxs-lookup"><span data-stu-id="dbbcb-414">Exercise 2</span></span>

<span data-ttu-id="dbbcb-415">Exiba os dados do Azure retornados, de forma mais conversada e legível, talvez ocultando os números.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-415">Display the returned Azure data, in a more conversational, and readable way, perhaps hiding the numbers.</span></span> <span data-ttu-id="dbbcb-416">Embora um bot possa estar falando para o usuário.</span><span class="sxs-lookup"><span data-stu-id="dbbcb-416">As though a bot might be speaking to the user.</span></span>