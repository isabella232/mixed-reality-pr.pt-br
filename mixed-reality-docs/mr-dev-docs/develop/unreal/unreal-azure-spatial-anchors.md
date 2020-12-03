---
title: Âncoras Espaciais do Azure no Unreal
description: Visão geral da criação das Âncoras Espaciais do Azure no Unreal Engine.
author: hferrone
ms.author: v-hferrone
ms.date: 07/01/2020
ms.topic: tutorial
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens 2, azure, desenvolvimento do azure, âncoras espaciais, realidade misturada, desenvolvimento, recursos, novo projeto, emulador, documentação, guias, hologramas, desenvolvimento de jogos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: b464292b606f6c375fe84a50867cac770cd8f001
ms.sourcegitcommit: 09522ab15a9008ca4d022f9e37fcc98f6eaf6093
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/30/2020
ms.locfileid: "96354544"
---
# <a name="azure-spatial-anchors-in-unreal"></a><span data-ttu-id="760c2-104">Âncoras Espaciais do Azure no Unreal</span><span class="sxs-lookup"><span data-stu-id="760c2-104">Azure Spatial Anchors in Unreal</span></span>

## <a name="overview"></a><span data-ttu-id="760c2-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="760c2-105">Overview</span></span>

<span data-ttu-id="760c2-106">As Âncoras Espaciais do Azure são um serviço de Realidade Misturada da Microsoft, permitindo que dispositivos de realidade aumentada descubram, compartilhem e persistam pontos de ancoragem no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="760c2-106">Azure Spatial Anchors is a Microsoft Mixed Reality service, allowing augmented reality devices to discover, share, and persist anchor points in the physical world.</span></span> <span data-ttu-id="760c2-107">A documentação abaixo fornece instruções para integrar o serviço Âncoras Espaciais do Azure a um projeto do Unreal.</span><span class="sxs-lookup"><span data-stu-id="760c2-107">Documentation below provides instructions for integrating the Azure Spatial Anchors service into an Unreal project.</span></span> <span data-ttu-id="760c2-108">Se estiver buscando mais informações, confira o [serviço Âncoras Espaciais do Azure](https://azure.microsoft.com/services/spatial-anchors/).</span><span class="sxs-lookup"><span data-stu-id="760c2-108">If you're looking for more information, check out the [Azure Spatial Anchors service](https://azure.microsoft.com/services/spatial-anchors/).</span></span>

> [!NOTE]
> <span data-ttu-id="760c2-109">O Unreal Engine 4.26 já tem plug-ins para o suporte a ARKit e ARCore caso você esteja direcionando seus projetos para o iOS ou o Android.</span><span class="sxs-lookup"><span data-stu-id="760c2-109">Unreal Engine 4.26 now has plugins for ARKit and ARCore support if you're targeting iOS or Android.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="760c2-110">As âncoras locais são armazenadas no dispositivo, enquanto as Âncoras Espaciais do Azure são armazenadas na nuvem.</span><span class="sxs-lookup"><span data-stu-id="760c2-110">Local anchors are stored on device, while Azure Spatial Anchors are stored in the cloud.</span></span> <span data-ttu-id="760c2-111">Se você está buscando armazenar suas âncoras localmente em um dispositivo, temos um documento [Âncoras Espaciais locais](unreal-spatial-anchors.md) que pode orientar você no processo.</span><span class="sxs-lookup"><span data-stu-id="760c2-111">If you're looking to store your anchors locally on a device, we have a [Local Spatial Anchors](unreal-spatial-anchors.md) document that can walk you through the process.</span></span> <span data-ttu-id="760c2-112">Você pode ter âncoras locais e do Azure no mesmo projeto sem conflitos.</span><span class="sxs-lookup"><span data-stu-id="760c2-112">Note that you can have local and Azure anchors in the same project without conflict.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="760c2-113">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="760c2-113">Prerequisites</span></span>

<span data-ttu-id="760c2-114">Para concluir este guia, verifique se você:</span><span class="sxs-lookup"><span data-stu-id="760c2-114">To complete this guide, make sure you have:</span></span>

- <span data-ttu-id="760c2-115">Instalou o [Unreal versão 4.25](https://www.unrealengine.com/get-now) ou posterior</span><span class="sxs-lookup"><span data-stu-id="760c2-115">Installed [Unreal version 4.25](https://www.unrealengine.com/get-now) or later</span></span>
- <span data-ttu-id="760c2-116">Um [projeto do HoloLens 2](tutorials/unreal-uxt-ch1.md) configurado no Unreal</span><span class="sxs-lookup"><span data-stu-id="760c2-116">A [HoloLens 2 project](tutorials/unreal-uxt-ch1.md) setup in Unreal</span></span> 
- <span data-ttu-id="760c2-117">Leia a [visão geral das Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/overview)</span><span class="sxs-lookup"><span data-stu-id="760c2-117">Read through the [Azure Spatial Anchors overview](https://docs.microsoft.com/azure/spatial-anchors/overview)</span></span>
- <span data-ttu-id="760c2-118">Conhecimento básico de C++ e Unreal</span><span class="sxs-lookup"><span data-stu-id="760c2-118">Basic knowledge on C++ and Unreal</span></span>

## <a name="getting-azure-spatial-anchors-account-info"></a><span data-ttu-id="760c2-119">Como obter informações da conta das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="760c2-119">Getting Azure Spatial Anchors account info</span></span>

<span data-ttu-id="760c2-120">Para usar as Âncoras Espaciais do Azure no seu projeto, você precisará:</span><span class="sxs-lookup"><span data-stu-id="760c2-120">Before using Azure Spatial Anchors in your project, you need to:</span></span>
* <span data-ttu-id="760c2-121">[Criar um recurso de âncoras espaciais](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) e copiar os campos da conta listados abaixo.</span><span class="sxs-lookup"><span data-stu-id="760c2-121">[Create a spatial anchors resource](https://docs.microsoft.com/azure/spatial-anchors/quickstarts/get-started-hololens#create-a-spatial-anchors-resource) and copy the account fields listed below.</span></span> <span data-ttu-id="760c2-122">Esses valores são usados para autenticar os usuários na conta do seu aplicativo:</span><span class="sxs-lookup"><span data-stu-id="760c2-122">These values are used to authenticate users with your application's account:</span></span>
    * <span data-ttu-id="760c2-123">**ID da Conta**</span><span class="sxs-lookup"><span data-stu-id="760c2-123">**Account ID**</span></span>
    * <span data-ttu-id="760c2-124">**Chave de Conta**</span><span class="sxs-lookup"><span data-stu-id="760c2-124">**Account Key**</span></span>

<span data-ttu-id="760c2-125">Confira a documentação [Autenticação das Âncoras Espaciais do Azure](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="760c2-125">Check out the [Azure Spatial Anchors authentication](https://docs.microsoft.com/azure/spatial-anchors/concepts/authentication?tabs=csharp) docs for more information.</span></span>

> [!NOTE]
> <span data-ttu-id="760c2-126">As Âncoras Espaciais do Azure no Unreal 4.25 não dão suporte a tokens de autenticação do Azure AD, mas o suporte para essa funcionalidade será disponibilizado em uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="760c2-126">Azure Spatial Anchors in Unreal 4.25 does not support Azure AD authentication tokens, but support for this functionality will be coming in a later release.</span></span>

## <a name="adding-azure-spatial-anchors-plugins"></a><span data-ttu-id="760c2-127">Como adicionar plug-ins das Âncoras Espaciais do Azure</span><span class="sxs-lookup"><span data-stu-id="760c2-127">Adding Azure Spatial Anchors plugins</span></span>

<span data-ttu-id="760c2-128">Habilite os plug-ins das Âncoras Espaciais do Azure no editor do Unreal:</span><span class="sxs-lookup"><span data-stu-id="760c2-128">Enable the Azure Spatial Anchors plugins in the Unreal editor by:</span></span>
1. <span data-ttu-id="760c2-129">Clicando em **Editar > Plug-ins** e procurando **AzureSpatialAnchors** e **AzureSpatialAnchorsForWMR**.</span><span class="sxs-lookup"><span data-stu-id="760c2-129">Clicking **Edit > Plugins** and searching for **AzureSpatialAnchors** and **AzureSpatialAnchorsForWMR**.</span></span>
2. <span data-ttu-id="760c2-130">Marque a caixa de seleção **Habilitado** nos dois plug-ins para permitir o acesso às bibliotecas de blueprints das Âncoras Espaciais do Azure no seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="760c2-130">Select the **Enabled** checkbox in both plugins to allow access to the Azure Spatial Anchors blueprint libraries in your application.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-01.png)

<span data-ttu-id="760c2-132">Depois disso, reinicie o editor do Unreal para que as alterações do plug-in entrem em vigor.</span><span class="sxs-lookup"><span data-stu-id="760c2-132">Once that's done, restart the Unreal Editor for the plugin changes to take effect.</span></span> <span data-ttu-id="760c2-133">Agora, o projeto está pronto para usar as Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-133">The project is now ready to use Azure Spatial Anchors.</span></span>

## <a name="starting-a-spatial-anchors-session"></a><span data-ttu-id="760c2-134">Como iniciar uma sessão das Âncoras Espaciais</span><span class="sxs-lookup"><span data-stu-id="760c2-134">Starting a Spatial Anchors session</span></span>
<span data-ttu-id="760c2-135">Uma sessão das Âncoras Espaciais do Azure permite que os aplicativos cliente se comuniquem com o serviço Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-135">An Azure Spatial Anchors session allows client applications to communicate with the Azure Spatial Anchors service.</span></span> <span data-ttu-id="760c2-136">Você precisará criar e iniciar uma sessão das Âncoras Espaciais do Azure para criar, persistir e compartilhar as Âncoras Espaciais do Azure:</span><span class="sxs-lookup"><span data-stu-id="760c2-136">You'll need to create and start an Azure Spatial Anchors session to create, persist, and share Azure Spatial Anchors:</span></span>

1. <span data-ttu-id="760c2-137">Abra o blueprint do Peão que você está usando no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="760c2-137">Open the blueprint for the Pawn you're using in the application.</span></span>
2. <span data-ttu-id="760c2-138">Adicione duas variáveis de cadeia de caracteres à **ID da Conta** e à **Chave de Conta** e atribua os valores correspondentes da sua conta das Âncoras Espaciais do Azure para autenticar a sessão.</span><span class="sxs-lookup"><span data-stu-id="760c2-138">Add two string variables for the **Account ID** and **Account Key**, then assign the corresponding values from your Azure Spatial Anchors account to authenticate the session.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-02.png)

<span data-ttu-id="760c2-140">Inicie uma sessão das Âncoras Espaciais do Azure:</span><span class="sxs-lookup"><span data-stu-id="760c2-140">Start an Azure Spatial Anchors session by:</span></span>
1. <span data-ttu-id="760c2-141">Verificando se uma **Sessão de AR** está em execução no aplicativo do HoloLens, pois a sessão das Âncoras Espaciais do Azure não pode ser iniciada até que uma Sessão de AR esteja em execução.</span><span class="sxs-lookup"><span data-stu-id="760c2-141">Checking that an **AR Session** is running in the HoloLens application, as the Azure Spatial Anchors session can't start until an AR Session is running.</span></span> <span data-ttu-id="760c2-142">Se você não tiver uma configuração, [crie um ativo da Sessão de AR](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span><span class="sxs-lookup"><span data-stu-id="760c2-142">If you don't have one setup, [create an AR Session asset](https://docs.microsoft.com/windows/mixed-reality/unreal-uxt-ch3#adding-the-session-asset).</span></span>
2. <span data-ttu-id="760c2-143">Adicionando o evento personalizado **Iniciar Sessão das Âncoras Espaciais do Azure** e configurando-o conforme mostrado na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="760c2-143">Adding the **Start Azure Spatial Anchors Session** custom event and configure it as shown in the screenshot below.</span></span>
    * <span data-ttu-id="760c2-144">A criação de uma sessão não inicia a sessão por padrão, o que permite ao desenvolvedor configurar a sessão para autenticação no serviço Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-144">Creating a session doesn't start the session by default, which allows the developer to configure the session for authentication with the Azure Spatial Anchors service.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-03.png)

3. <span data-ttu-id="760c2-146">Configure a sessão das Âncoras Espaciais do Azure para fornecer a **ID da Conta** e a **Chave de Conta**.</span><span class="sxs-lookup"><span data-stu-id="760c2-146">Configure the Azure Spatial Anchors session to provide the **Account ID** and **Account Key**.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-04.png)

4. <span data-ttu-id="760c2-148">Inicie a sessão das Âncoras Espaciais do Azure, permitindo que o aplicativo crie e localize as Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-148">Start the Azure Spatial Anchors session, allowing the application to create and locate Azure Spatial Anchors.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-05.png)

<span data-ttu-id="760c2-150">Será uma boa prática limpar os recursos das Âncoras Espaciais do Azure no blueprint do Grafo de Eventos quando você não estiver mais usando o serviço:</span><span class="sxs-lookup"><span data-stu-id="760c2-150">It's good practice to clean up Azure Spatial Anchors resources in your Event Graph blueprint when you're no longer using the service:</span></span>

1. <span data-ttu-id="760c2-151">Interrompa a sessão das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-151">Stop the Azure Spatial Anchors session.</span></span> <span data-ttu-id="760c2-152">A sessão não estará mais em execução, mas os respectivos recursos associados ainda existirão no plug-in das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-152">The session will no longer be running, but its associated resources will still exist in the Azure Spatial Anchors plugin.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-06.png)

2. <span data-ttu-id="760c2-154">Destrua a sessão das Âncoras Espaciais do Azure para limpar os recursos da sessão das Âncoras Espaciais do Azure ainda conhecidos pelo plug-in das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-154">Destroy the Azure Spatial Anchors session to clean up any Azure Spatial Anchors session resources still known to the Azure Spatial Anchors plugin.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-07.png)

<span data-ttu-id="760c2-156">O blueprint do Grafo de Eventos será parecido com a captura de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="760c2-156">Your Event Graph blueprint should look like the screenshot below:</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-08.png)


## <a name="creating-an-anchor"></a><span data-ttu-id="760c2-158">Como criar uma âncora</span><span class="sxs-lookup"><span data-stu-id="760c2-158">Creating an anchor</span></span>
<span data-ttu-id="760c2-159">Uma Âncora Espacial do Azure representa uma pose do mundo físico no espaço do aplicativo de realidade aumentada, que bloqueia o conteúdo de realidade aumentada em localizações do mundo físico.</span><span class="sxs-lookup"><span data-stu-id="760c2-159">An Azure Spatial Anchor represents a physical world pose in the augmented reality application space, which locks augmented reality content to locations in the physical world.</span></span> <span data-ttu-id="760c2-160">As Âncoras Espaciais do Azure também podem ser compartilhadas entre diferentes usuários.</span><span class="sxs-lookup"><span data-stu-id="760c2-160">Azure Spatial Anchors can also be shared among different users.</span></span> <span data-ttu-id="760c2-161">Esse compartilhamento permite que o conteúdo de realidade aumentada desenhado em diferentes dispositivos seja posicionado na mesma localização no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="760c2-161">This sharing allows augmented reality content drawn on different devices to be positioned in the same location in the physical world.</span></span> 

<span data-ttu-id="760c2-162">Para criar uma Âncora Espacial do Azure:</span><span class="sxs-lookup"><span data-stu-id="760c2-162">To create a new Azure Spatial Anchor:</span></span>
1. <span data-ttu-id="760c2-163">Verifique se uma sessão das Âncoras Espaciais do Azure está em execução.</span><span class="sxs-lookup"><span data-stu-id="760c2-163">Check that an Azure Spatial Anchors session is running.</span></span> <span data-ttu-id="760c2-164">O aplicativo não pode criar nem manter uma Âncora Espacial do Azure quando não há nenhuma sessão das Âncoras Espaciais do Azure em execução.</span><span class="sxs-lookup"><span data-stu-id="760c2-164">The application can't create or persist an Azure Spatial Anchor when no Azure Spatial Anchors session is running.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-09.png)

2. <span data-ttu-id="760c2-166">Crie ou obtenha um **[Componente de Cena](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** do Unreal que deve ter a localização persistente.</span><span class="sxs-lookup"><span data-stu-id="760c2-166">Create or obtain an Unreal **[Scene Component](https://docs.unrealengine.com/API/Runtime/Engine/Components/USceneComponent/index.html)** that should have its location persisted.</span></span> 
    * <span data-ttu-id="760c2-167">Na imagem abaixo, o componente **Âncora que Precisa de um Componente de Cena** é usado como uma variável.</span><span class="sxs-lookup"><span data-stu-id="760c2-167">In the below image, the **Scene Component Needing Anchor** component is used as a variable.</span></span> <span data-ttu-id="760c2-168">Um Componente de Cena do Unreal é necessário para estabelecer uma transformação do mundo do aplicativo em um [Marcador de AR](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) e uma Âncora Espacial do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-168">An Unreal Scene Component is needed to establish an application world transform for an [AR Pin](https://docs.unrealengine.com/BlueprintAPI/HoloLensAR/ARPin/index.html) and Azure Spatial Anchor.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-10.png)

<span data-ttu-id="760c2-170">Para construir e salvar uma Âncora Espacial do Azure de um Componente de Cena do Unreal:</span><span class="sxs-lookup"><span data-stu-id="760c2-170">To construct and save an Azure Spatial Anchor for an Unreal Scene Component:</span></span>
1. <span data-ttu-id="760c2-171">Chame o [Componente de Marcador](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) para o Componente de Cena do Unreal e especifique a **Transformação do Mundo** do Componente de Cena como a Transformação do Mundo usada para o Marcador de AR.</span><span class="sxs-lookup"><span data-stu-id="760c2-171">Call the [Pin Component](https://docs.unrealengine.com/BlueprintAPI/ARAugmentedReality/Pin/PinComponent/index.html) for the Unreal Scene Component and specify the Scene Component's **World Transform** as the World Transform used for the AR Pin.</span></span>
    * <span data-ttu-id="760c2-172">O Unreal acompanha os pontos de AR no espaço do aplicativo usando Marcadores de AR, que são usados para criar uma Âncora Espacial do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-172">Unreal tracks AR points in the application space using AR Pins, which are used to create an Azure Spatial Anchor.</span></span> <span data-ttu-id="760c2-173">No Unreal, um Marcador de AR é similar a uma SpatialAnchor no HoloLens.</span><span class="sxs-lookup"><span data-stu-id="760c2-173">In Unreal, an AR Pin is analogous to a SpatialAnchor on HoloLens.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-11.png)

2. <span data-ttu-id="760c2-175">Chame **Criar Âncora de Nuvem** usando o Marcador de AR recém-criado.</span><span class="sxs-lookup"><span data-stu-id="760c2-175">Call **Create Cloud Anchor** using the newly created AR Pin.</span></span>
    * <span data-ttu-id="760c2-176">A função Criar Âncora de Nuvem cria uma Âncora Espacial do Azure localmente, mas não no serviço Âncora Espacial do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-176">Create Cloud Anchor creates an Azure Spatial Anchor locally but not in the Azure Spatial Anchor service.</span></span> <span data-ttu-id="760c2-177">Os parâmetros para a Âncora Espacial do Azure, como uma data de validade, podem ser definidos antes da criação da Âncora Espacial do Azure com o serviço.</span><span class="sxs-lookup"><span data-stu-id="760c2-177">Parameters for the Azure Spatial Anchor, such as an expiration date, can be set before creating the Azure Spatial Anchor with the service.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-12.png)

3. <span data-ttu-id="760c2-179">Defina a validade da Âncora Espacial do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-179">Set the Azure Spatial Anchor expiration.</span></span> <span data-ttu-id="760c2-180">O parâmetro Tempo de Vida da função permite que o desenvolvedor especifique, em segundos, quanto tempo a âncora deve ser mantida pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="760c2-180">This function's Lifetime parameter allows the developer to specify in seconds how long the anchor should be maintained by the service.</span></span>
    * <span data-ttu-id="760c2-181">Por exemplo, uma validade de uma semana usará um valor igual a 60 segundos x 60 minutos x 24 horas x sete dias = 604.800 segundos.</span><span class="sxs-lookup"><span data-stu-id="760c2-181">For example, a week long expiration would take a value of 60 seconds x 60 minutes x 24 hours x seven days = 604,800 seconds.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-13.png)

<span data-ttu-id="760c2-183">Depois de definir os parâmetros de âncora, declare a âncora como pronta para ser salva.</span><span class="sxs-lookup"><span data-stu-id="760c2-183">After setting anchor parameters, declare the anchor as ready to save.</span></span> <span data-ttu-id="760c2-184">No exemplo abaixo, a Âncora Espacial recém-criada do Azure é adicionada a um conjunto das Âncoras Espaciais do Azure que precisam ser salvas.</span><span class="sxs-lookup"><span data-stu-id="760c2-184">In the example below, the newly created Azure Spatial Anchor is added to a set of Azure Spatial Anchors needing saving.</span></span> <span data-ttu-id="760c2-185">Esse conjunto é declarado como uma variável do blueprint de Peão.</span><span class="sxs-lookup"><span data-stu-id="760c2-185">This set is declared as a variable for the Pawn blueprint.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-14.png)

## <a name="saving-an-anchor"></a><span data-ttu-id="760c2-187">Como salvar uma âncora</span><span class="sxs-lookup"><span data-stu-id="760c2-187">Saving an Anchor</span></span>

<span data-ttu-id="760c2-188">Depois de configurar a Âncora Espacial do Azure com os parâmetros, chame a função **Salvar Âncora de Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="760c2-188">After configuring the Azure Spatial Anchor with your parameters, call **Save Cloud Anchor**.</span></span> <span data-ttu-id="760c2-189">A função Salvar âncora de Nuvem declara a âncora para o serviço Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-189">Save Cloud Anchor declares the anchor to the Azure Spatial Anchors service.</span></span> <span data-ttu-id="760c2-190">Quando a chamada a Salvar Âncora de Nuvem for realizada com sucesso, a Âncora Espacial do Azure estará disponível para outros usuários do serviço Âncora Espacial do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-190">When the call to Save Cloud Anchor succeeds, the Azure Spatial Anchor is available to other users of the Azure Spatial Anchor service.</span></span>  

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-15.png)

> [!NOTE]
> <span data-ttu-id="760c2-192">A função Salvar Âncora de Nuvem é assíncrona e só pode ser chamada em um evento de thread de jogo, como **EventTick**.</span><span class="sxs-lookup"><span data-stu-id="760c2-192">Save Cloud Anchor is an asynchronous function and can only be called on a game thread event such as **EventTick**.</span></span> <span data-ttu-id="760c2-193">Talvez a função Salvar Âncora de Nuvem não seja exibida como uma função de blueprint disponível nas funções de blueprint personalizadas.</span><span class="sxs-lookup"><span data-stu-id="760c2-193">Save Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="760c2-194">No entanto, ela deve estar disponível no editor de blueprint do Grafo de Eventos do Peão.</span><span class="sxs-lookup"><span data-stu-id="760c2-194">However, it should be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="760c2-195">No exemplo abaixo, a Âncora Espacial do Azure é armazenada em um conjunto durante um retorno de chamada de evento de entrada.</span><span class="sxs-lookup"><span data-stu-id="760c2-195">In the example below, the Azure Spatial Anchor is stored in a set during an input event callback.</span></span> <span data-ttu-id="760c2-196">Em seguida, a âncora é salva no EventTick.</span><span class="sxs-lookup"><span data-stu-id="760c2-196">The anchor is then saved on the EventTick.</span></span> <span data-ttu-id="760c2-197">Para salvar uma Âncora Espacial do Azure, podem ser necessárias várias tentativas dependendo do volume de dados espaciais criado pela sessão das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-197">Saving an Azure Spatial Anchor may take multiple attempts depending on the amount of spatial data that your Azure Spatial Anchors session has created.</span></span> <span data-ttu-id="760c2-198">Por esse motivo, é uma boa ideia verificar se a chamada de salvamento foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="760c2-198">That's why it's a good idea to check whether the save call succeeded.</span></span>

<span data-ttu-id="760c2-199">Se a âncora não for salva, adicione-a novamente ao conjunto de âncoras que ainda precisa ser salvo.</span><span class="sxs-lookup"><span data-stu-id="760c2-199">If the anchor doesn't save, re-add it to the set of anchors still needing to be saved.</span></span> <span data-ttu-id="760c2-200">Os EventTicks futuros tentarão salvar a âncora até que ela seja armazenada com êxito no serviço Âncora Espacial do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-200">Future EventTicks will try to save the anchor until it's successfully stored in the Azure Spatial Anchor service.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-16.png)

<span data-ttu-id="760c2-202">Depois que a âncora for salva, use a transformação de Marcadores de AR como uma transformação de referência para colocar conteúdo no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="760c2-202">Once the anchor saves, you can use the AR Pins' transform as a reference transform for placing content in the application.</span></span> <span data-ttu-id="760c2-203">Outros usuários podem detectar essa âncora e alinhar o conteúdo de AR para diferentes dispositivos no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="760c2-203">Other users can detect this anchor and align AR content for different devices in the physical world.</span></span>

## <a name="deleting-an-anchor"></a><span data-ttu-id="760c2-204">Como excluir uma âncora</span><span class="sxs-lookup"><span data-stu-id="760c2-204">Deleting an Anchor</span></span>

<span data-ttu-id="760c2-205">Exclua âncoras do serviço Âncora Espacial do Azure chamando **Excluir Âncora de Nuvem**.</span><span class="sxs-lookup"><span data-stu-id="760c2-205">You can delete anchors from the Azure Spatial Anchor service by calling **Delete Cloud Anchor**.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-17.png)

> [!NOTE]
> <span data-ttu-id="760c2-207">A função Excluir Âncora de Nuvem é latente e só pode ser chamada em um evento de thread de jogo, como EventTick.</span><span class="sxs-lookup"><span data-stu-id="760c2-207">Delete Cloud Anchor is a latent function and can only be called on a game thread event, such as EventTick.</span></span> <span data-ttu-id="760c2-208">Talvez a função Excluir Âncora de Nuvem não seja exibida como uma função de blueprint disponível nas funções de blueprint personalizadas.</span><span class="sxs-lookup"><span data-stu-id="760c2-208">Delete Cloud Anchor may not appear as an available blueprint function in custom blueprint Functions.</span></span> <span data-ttu-id="760c2-209">No entanto, ela deve estar disponível no editor de blueprint do Grafo de Eventos de Peão.</span><span class="sxs-lookup"><span data-stu-id="760c2-209">It should however be available in the Pawn Event Graph blueprint editor.</span></span>

<span data-ttu-id="760c2-210">No exemplo abaixo, a âncora é sinalizada para exclusão em um evento de entrada personalizado.</span><span class="sxs-lookup"><span data-stu-id="760c2-210">In the example below, the anchor is flagged for deletion on a custom input event.</span></span> <span data-ttu-id="760c2-211">Em seguida, é feita a tentativa de exclusão no EventTick.</span><span class="sxs-lookup"><span data-stu-id="760c2-211">The deletion is then attempted on the EventTick.</span></span> <span data-ttu-id="760c2-212">Se a exclusão da âncora falhar, adicione a Âncora Espacial do Azure ao conjunto de âncoras sinalizadas para exclusão e tente novamente em EventTicks posteriores.</span><span class="sxs-lookup"><span data-stu-id="760c2-212">If the anchor deletion fails, add the Azure Spatial Anchor to the set of anchors flagged for deletion and tries again on later EventTicks.</span></span>

<span data-ttu-id="760c2-213">Agora, o blueprint do Grafo de Eventos será parecido com a captura de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="760c2-213">Your Event Graph blueprint should now look like the screenshot below:</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-18.png)


## <a name="locating-pre-existing-anchors"></a><span data-ttu-id="760c2-215">Como localizar âncoras pré-existentes</span><span class="sxs-lookup"><span data-stu-id="760c2-215">Locating pre-existing anchors</span></span>

<span data-ttu-id="760c2-216">Além de criar Âncoras Espaciais do Azure, você pode detectar âncoras criadas por colegas com o serviço Âncoras Espaciais do Azure:</span><span class="sxs-lookup"><span data-stu-id="760c2-216">In addition to creating Azure Spatial Anchors, you can detect anchors created by peers with the Azure Spatial Anchors service:</span></span>

1. <span data-ttu-id="760c2-217">Obtenha um identificador de Âncora Espacial do Azure da âncora que deseja detectar.</span><span class="sxs-lookup"><span data-stu-id="760c2-217">Obtain an Azure Spatial Anchor identifier for the anchor that you would like to detect.</span></span>
    * <span data-ttu-id="760c2-218">Um identificador de âncora pode ser obtido para uma âncora criada pelo mesmo dispositivo em uma sessão anterior das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-218">An anchor identifier can be obtained for an anchor created by the same device in a previous Azure Spatial Anchors session.</span></span> <span data-ttu-id="760c2-219">Ele também pode ser criado e compartilhado por dispositivos pares que interagem com o serviço Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-219">It can also be created and shared by peer devices interacting with the Azure Spatial Anchors service.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-24.png)

2. <span data-ttu-id="760c2-221">Adicione um componente **AzureSpatialAnchorsEvent** ao blueprint de Peão.</span><span class="sxs-lookup"><span data-stu-id="760c2-221">Add an **AzureSpatialAnchorsEvent** component to your Pawn blueprint.</span></span>
    * <span data-ttu-id="760c2-222">Esse componente permite que você assine vários eventos das Âncoras Espaciais do Azure, como eventos chamados quando as Âncoras Espaciais do Azure são localizadas.</span><span class="sxs-lookup"><span data-stu-id="760c2-222">This component allows you to subscribe to various Azure Spatial Anchors events, such as events called when Azure Spatial Anchors are located.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-19.png)

3. <span data-ttu-id="760c2-224">Assine o **Delegado Localizado de ASAAnchor** para o componente **AzureSpatialAnchorsEvent**.</span><span class="sxs-lookup"><span data-stu-id="760c2-224">Subscribe to the **ASAAnchor Located Delegate** for the **AzureSpatialAnchorsEvent** component.</span></span>
    * <span data-ttu-id="760c2-225">O delegado permite que o aplicativo saiba quando são localizadas novas âncoras associadas à conta das Âncoras Espaciais do Azure.</span><span class="sxs-lookup"><span data-stu-id="760c2-225">The delegate lets the application know when new anchors associated with the Azure Spatial Anchors account have been located.</span></span>
    * <span data-ttu-id="760c2-226">Com o retorno de chamada do evento, as Âncoras Espaciais do Azure criadas pelos colegas que usam a sessão das Âncoras Espaciais do Azure não terão Marcadores de AR criados por padrão.</span><span class="sxs-lookup"><span data-stu-id="760c2-226">With the event callback, Azure Spatial Anchors created by peers using the Azure Spatial Anchors session won't have AR Pins created by default.</span></span> <span data-ttu-id="760c2-227">Para criar um Marcador de AR para a Âncora Espacial do Azure detectada, os desenvolvedores podem chamar a função **Criar Marcador de RA em Torno da Âncora Espacial de Nuvem do Azure**.</span><span class="sxs-lookup"><span data-stu-id="760c2-227">To create an AR Pin for the detected Azure Spatial Anchor, developers can call **Create ARPin Around Azure Cloud Spatial Anchor**.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-20.png)

<span data-ttu-id="760c2-229">Para localizar Âncoras Espaciais do Azure criadas pelos pares usando o serviço Âncora Espacial do Azure, o aplicativo precisará criar um **Observador das Âncoras Espaciais do Azure**:</span><span class="sxs-lookup"><span data-stu-id="760c2-229">In order to locate Azure Spatial Anchors created by peers using the Azure Spatial Anchor service, the application will have to create an **Azure Spatial Anchors Watcher**:</span></span>
1. <span data-ttu-id="760c2-230">Verifique se uma sessão das Âncoras Espaciais do Azure está em execução.</span><span class="sxs-lookup"><span data-stu-id="760c2-230">Check that an Azure Spatial Anchors session is running.</span></span>
2. <span data-ttu-id="760c2-231">Crie um **AzureSpatialAnchorsLocateCriteria**.</span><span class="sxs-lookup"><span data-stu-id="760c2-231">Create an **AzureSpatialAnchorsLocateCriteria**.</span></span>
    * <span data-ttu-id="760c2-232">Você pode especificar vários parâmetros de localização, como distância do usuário ou distância de outra âncora.</span><span class="sxs-lookup"><span data-stu-id="760c2-232">You can specify various location parameters like distance from the user or distance from another anchor.</span></span>
3. <span data-ttu-id="760c2-233">Declare o identificador desejado da Âncora Espacial do Azure em **AzureSpatialAnchorsLocateCriteria**.</span><span class="sxs-lookup"><span data-stu-id="760c2-233">Declare your desired Azure Spatial Anchor identifier in the **AzureSpatialAnchorsLocateCritieria**.</span></span>
4. <span data-ttu-id="760c2-234">Chame **Criar Observador**.</span><span class="sxs-lookup"><span data-stu-id="760c2-234">Call **Create Watcher**.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-21.png)

<span data-ttu-id="760c2-236">Agora, o aplicativo começa a procurar as Âncoras Espaciais do Azure conhecidas pelo serviço Âncoras Espaciais do Azure, o que significa que os usuários podem localizar as Âncoras Espaciais do Azure criadas pelos colegas.</span><span class="sxs-lookup"><span data-stu-id="760c2-236">The application now begins looking for Azure Spatial Anchors known to the Azure Spatial Anchors service, meaning that users can locate Azure Spatial Anchors created by their peers.</span></span>

<span data-ttu-id="760c2-237">Depois de localizar a Âncora Espacial do Azure, chame a função **Parar Observador** para interromper o Observador das Âncoras Espaciais do Azure e limpar os recursos do observador.</span><span class="sxs-lookup"><span data-stu-id="760c2-237">After locating the Azure Spatial Anchor, call **Stop Watcher** to stop the Azure Spatial Anchors Watcher and clean up watcher resources.</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-22.png)

<span data-ttu-id="760c2-239">Agora, o blueprint final do Grafo de Eventos será parecido com a captura de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="760c2-239">Your final Event Graph blueprint should now look like the screenshot below:</span></span>

![Plug-ins das Âncoras Espaciais](images/asa-unreal/unreal-spatial-anchors-img-23.png)

## <a name="next-development-checkpoint"></a><span data-ttu-id="760c2-241">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="760c2-241">Next Development Checkpoint</span></span>

<span data-ttu-id="760c2-242">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unreal, você está no meio da exploração dos principais blocos de construção do MRTK.</span><span class="sxs-lookup"><span data-stu-id="760c2-242">If you're following the Unreal development checkpoint journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="760c2-243">De lá, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="760c2-243">From here, you can proceed to the next building block:</span></span> 

> [!div class="nextstepaction"]
> [<span data-ttu-id="760c2-244">Mapeamento espacial</span><span class="sxs-lookup"><span data-stu-id="760c2-244">Spatial mapping</span></span>](unreal-spatial-mapping.md)

<span data-ttu-id="760c2-245">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="760c2-245">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="760c2-246">Câmera do HoloLens</span><span class="sxs-lookup"><span data-stu-id="760c2-246">HoloLens camera</span></span>](unreal-hololens-camera.md)

<span data-ttu-id="760c2-247">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unreal](unreal-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="760c2-247">You can always go back to the [Unreal development checkpoints](unreal-development-overview.md#2-core-building-blocks) at any time.</span></span>


## <a name="next-steps"></a><span data-ttu-id="760c2-248">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="760c2-248">Next steps</span></span>
* [<span data-ttu-id="760c2-249">Âncoras Espaciais locais</span><span class="sxs-lookup"><span data-stu-id="760c2-249">Local Spatial Anchors</span></span>](unreal-spatial-anchors.md)
* [<span data-ttu-id="760c2-250">Documentação das Âncoras Espaciais</span><span class="sxs-lookup"><span data-stu-id="760c2-250">Spatial Anchors documentation</span></span>](https://docs.microsoft.com/azure/spatial-anchors/)
* [<span data-ttu-id="760c2-251">Recursos da Âncora Espacial</span><span class="sxs-lookup"><span data-stu-id="760c2-251">Spatial Anchor features</span></span>](https://azure.microsoft.com/services/spatial-anchors/#features)
* [<span data-ttu-id="760c2-252">Diretrizes de experiência de ancoragem efetiva</span><span class="sxs-lookup"><span data-stu-id="760c2-252">Effective anchor experience guidelines</span></span>](https://docs.microsoft.com/azure/spatial-anchors/concepts/guidelines-effective-anchor-experiences)