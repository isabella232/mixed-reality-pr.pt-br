---
title: Como criar seu primeiro aplicativo Unreal do HoloLens
description: Saiba como configurar corretamente um projeto do Unreal com objetos de cena e interações de entrada para o desenvolvimento da realidade misturada do HoloLens.
author: hferrone
ms.author: safarooq
ms.date: 01/19/2021
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, editor do Unreal, UE4, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, documentação, guias, recursos, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, portabilidade, atualização
ms.openlocfilehash: 467987f69b50c0ec635c99899d6bcecab5a62af0
ms.sourcegitcommit: 1304f8f0a838290c1ae3db34670b67c75ea9bdaa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99421425"
---
# <a name="creating-your-first-hololens-unreal-application"></a><span data-ttu-id="c5157-104">Como criar seu primeiro aplicativo Unreal do HoloLens</span><span class="sxs-lookup"><span data-stu-id="c5157-104">Creating your first HoloLens Unreal application</span></span>

<span data-ttu-id="c5157-105">Este guia descreverá como executar seu primeiro aplicativo de Realidade Misturada no HoloLens no Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="c5157-105">This guide will walk you through getting your first Mixed Reality app running on the HoloLens in Unreal Engine.</span></span> <span data-ttu-id="c5157-106">Na tradição do "Olá, Mundo", você criará um aplicativo simples que exibe um cubo na tela.</span><span class="sxs-lookup"><span data-stu-id="c5157-106">In the tradition of "Hello World", you'll create a simple app that displays a cube on the screen.</span></span> <span data-ttu-id="c5157-107">Para torná-lo mais útil, você também criará seu primeiro gesto para girar o cubo e encerrar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5157-107">To make it more useful, you'll also create your first gesture to rotate the cube and quit the application.</span></span> 

## <a name="objectives"></a><span data-ttu-id="c5157-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="c5157-108">Objectives</span></span>

* <span data-ttu-id="c5157-109">Iniciar um projeto do HoloLens</span><span class="sxs-lookup"><span data-stu-id="c5157-109">Start a HoloLens Project</span></span>
* <span data-ttu-id="c5157-110">Habilitar os plug-ins corretos</span><span class="sxs-lookup"><span data-stu-id="c5157-110">Enable the correct plugins</span></span>
* <span data-ttu-id="c5157-111">Criar um ativo de dados ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="c5157-111">Create an ARSessionConfig Data Asset</span></span>
* <span data-ttu-id="c5157-112">Configurar entradas de gesto</span><span class="sxs-lookup"><span data-stu-id="c5157-112">Set up gesture inputs</span></span>
* <span data-ttu-id="c5157-113">Criar um nível básico</span><span class="sxs-lookup"><span data-stu-id="c5157-113">Build a basic level</span></span>
* <span data-ttu-id="c5157-114">Implementar um gesto de pinçagem</span><span class="sxs-lookup"><span data-stu-id="c5157-114">Implement a pinch gesture</span></span>

## <a name="creating-a-new-project"></a><span data-ttu-id="c5157-115">Crie um novo projeto</span><span class="sxs-lookup"><span data-stu-id="c5157-115">Creating a new project</span></span>

<span data-ttu-id="c5157-116">A primeira coisa que você precisa é de um projeto com o qual trabalhar.</span><span class="sxs-lookup"><span data-stu-id="c5157-116">The first thing you need is a project to work with.</span></span> <span data-ttu-id="c5157-117">Se você é um desenvolvedor novo do Unreal, [baixe os arquivos de suporte](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="c5157-117">If you're a first-time Unreal developer, you'll need to [download supporting files](tutorials/unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="c5157-118">Iniciar Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="c5157-118">Launch Unreal Engine</span></span>
2. <span data-ttu-id="c5157-119">Em **Novas Categorias de Projeto**, selecione **Jogos** e clique em **Avançar**:</span><span class="sxs-lookup"><span data-stu-id="c5157-119">In the **New Project Categories**, select **Games** and click **Next**:</span></span>

![Janela Projetos recentes aberta com os Jogos realçados](images/unreal-quickstart-img-01.png)

3. <span data-ttu-id="c5157-121">Selecione o modelo **Em branco** e clique em **Avançar**:</span><span class="sxs-lookup"><span data-stu-id="c5157-121">Select the **Blank** template and click **Next**:</span></span>

![A janela do navegador de projetos do Unreal com o modelo Em branco realçado](images/unreal-quickstart-img-02.png)

4. <span data-ttu-id="c5157-123">Em **Configurações do Projeto**, defina **C++, 3D ou 2D Escalonável, Celular/Tablet** e **Nenhum Conteúdo Inicial**, escolha uma localização de salvamento e clique em **Criar Projeto**</span><span class="sxs-lookup"><span data-stu-id="c5157-123">In the **Project Settings**, set **C++, Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content**, then choose a save location and click **Create Project**</span></span>

> [!NOTE] 
> <span data-ttu-id="c5157-124">Você está usando um projeto C++ em vez de um projeto Blueprint para estar pronto para usar o plug-in OpenXR mais tarde.</span><span class="sxs-lookup"><span data-stu-id="c5157-124">You're using a C++ rather than a Blueprint project in order to be ready to use the OpenXR plugin later.</span></span> <span data-ttu-id="c5157-125">Este Guia de Início Rápido usa o plug-in OpenXR padrão fornecido com o Unreal Engine.</span><span class="sxs-lookup"><span data-stu-id="c5157-125">This QuickStart uses the default OpenXR plugin that comes with Unreal Engine.</span></span> <span data-ttu-id="c5157-126">No entanto, é recomendável baixar e usar o plug-in oficial do Microsoft OpenXR.</span><span class="sxs-lookup"><span data-stu-id="c5157-126">However, downloading and using the official Microsoft OpenXR plugin is recommended.</span></span> <span data-ttu-id="c5157-127">Isso requer que o projeto seja um projeto C++.</span><span class="sxs-lookup"><span data-stu-id="c5157-127">That requires the project to be a C++ project.</span></span>

![Janela de configurações do projeto com as opções de projeto, de desempenho, de plataforma de destino e de conteúdo inicial realçadas](images/unreal-quickstart-img-03.png)

<span data-ttu-id="c5157-129">O seu novo projeto deve ser aberto automaticamente no editor do Unreal, o que significa que você está pronto para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="c5157-129">Your new project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="c5157-130">Como habilitar os plugins necessários</span><span class="sxs-lookup"><span data-stu-id="c5157-130">Enabling required plugins</span></span>

<span data-ttu-id="c5157-131">Habilite dois plug-ins para começar a adicionar objetos à cena.</span><span class="sxs-lookup"><span data-stu-id="c5157-131">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="c5157-132">Abra **Editar > Plug-ins** e selecione **Realidade Aumentada** na lista de opções internas.</span><span class="sxs-lookup"><span data-stu-id="c5157-132">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span>
* <span data-ttu-id="c5157-133">Role para baixo até **HoloLens** e marque **Habilitado**</span><span class="sxs-lookup"><span data-stu-id="c5157-133">Scroll down to **HoloLens** and check **Enabled**</span></span>

![A janela Plug-ins com a seção de realidade aumentada está aberta e o HoloLens está realçado](images/unreal-quickstart-img-04.png)

2. <span data-ttu-id="c5157-135">Digite **OpenXR** na caixa de pesquisa no canto superior direito e habilite os plug-ins **OpenXR** e **OpenXRMsftHandInteraction**:</span><span class="sxs-lookup"><span data-stu-id="c5157-135">Type **OpenXR** in the search box at the top right and enable the **OpenXR** and **OpenXRMsftHandInteraction** plugins:</span></span>

![Janela Plug-ins com o OpenXR habilitado](images/unreal-quickstart-img-05.jpg)

![Janela Plug-ins com a Interação das Mãos do Open XR Msft habilitada](images/unreal-quickstart-img-06.jpg)

3. <span data-ttu-id="c5157-138">Reiniciar o editor</span><span class="sxs-lookup"><span data-stu-id="c5157-138">Restart your editor</span></span>

> [!NOTE]
> <span data-ttu-id="c5157-139">Este tutorial usa o OpenXR, mas os dois plug-ins que você instalou acima não fornecem atualmente o conjunto de recursos completo para o desenvolvimento do HoloLens.</span><span class="sxs-lookup"><span data-stu-id="c5157-139">This tutorial uses OpenXR, but the two plugins you've installed above don't currently provide the full feature set for HoloLens development.</span></span> <span data-ttu-id="c5157-140">O plug-in HandInteraction será suficiente para o gesto de "pinçar" que você usará mais tarde, mas se quiser ir além dos conceitos básicos, você precisará [baixar o plug-in do OpenXR](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="c5157-140">The HandInteraction plugin will suffice for the "Pinch" gesture you'll use later, but if you want to go beyond the basics you'll need to [download the OpenXR plugin](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

<span data-ttu-id="c5157-141">Com os plug-ins habilitados, você pode se concentrar em preenchê-lo com conteúdo.</span><span class="sxs-lookup"><span data-stu-id="c5157-141">With the plugins enabled, you can focus on filling it with content.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="c5157-142">Criar um nível</span><span class="sxs-lookup"><span data-stu-id="c5157-142">Creating a level</span></span>

<span data-ttu-id="c5157-143">Sua próxima tarefa será criar uma configuração de jogador com um ponto de partida e um cubo para referência e escala.</span><span class="sxs-lookup"><span data-stu-id="c5157-143">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="c5157-144">Selecione **Arquivo > Novo Nível** e escolha **Nível Vazio**.</span><span class="sxs-lookup"><span data-stu-id="c5157-144">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="c5157-145">A cena padrão no visor agora deve estar vazia</span><span class="sxs-lookup"><span data-stu-id="c5157-145">The default scene in the viewport should now be empty</span></span>
2. <span data-ttu-id="c5157-146">Na guia **Modos**, selecione **Básico** e arraste **PlayerStart** para a cena</span><span class="sxs-lookup"><span data-stu-id="c5157-146">From the **Modes** tab, select **Basic** and drag **PlayerStart** into the scene</span></span>
* <span data-ttu-id="c5157-147">Na guia **Detalhes**, defina a **Localização** como o **X = 0, Y = 0** e **Z = 0** para colocar o usuário no centro da cena quando o aplicativo for iniciado</span><span class="sxs-lookup"><span data-stu-id="c5157-147">In the **Details** tab, set **Location** to **X = 0, Y = 0,** and **Z = 0** to place the user at the center of the scene when the app starts</span></span>

![A cena do editor do Unreal com a localização e o início do player adicionados](images/unreal-quickstart-img-07.png)

3. <span data-ttu-id="c5157-149">Na guia **Básico**, arraste um **Cubo** para a cena</span><span class="sxs-lookup"><span data-stu-id="c5157-149">From the **Basic** tab, drag a **Cube** into the scene</span></span>
* <span data-ttu-id="c5157-150">Defina a **Localização** do cubo como **X = 50, Y = 0** e **Z = 0** para posicionar o cubo a 50 cm de distância do player no início</span><span class="sxs-lookup"><span data-stu-id="c5157-150">Set the cube's **Location** to **X = 50, Y = 0**, and **Z = 0** to position the cube 50 cm away from the player at start</span></span>
* <span data-ttu-id="c5157-151">Altere a **Escala** do cubo para **X = 0,2, Y = 0,2** e **Z = 0,2**</span><span class="sxs-lookup"><span data-stu-id="c5157-151">Change  the cube's **Scale** to **X = 0.2, Y = 0.2**, and **Z = 0.2**</span></span> 

<span data-ttu-id="c5157-152">Você não poderá ver o cubo, a menos que adicione uma luz à cena, que será a sua última tarefa antes de testar a cena em questão.</span><span class="sxs-lookup"><span data-stu-id="c5157-152">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="c5157-153">No painel **Modos**, alterne para a guia **Luzes** e arraste uma **Luz Direcional** até a cena</span><span class="sxs-lookup"><span data-stu-id="c5157-153">In the **Modes** panel, switch to the **Lights** tab and drag a **Directional Light** into the scene</span></span>
* <span data-ttu-id="c5157-154">Posicione a luz acima de **PlayerStart** para que você possa vê-lo</span><span class="sxs-lookup"><span data-stu-id="c5157-154">Position the light above **PlayerStart** so you can see it</span></span>

![Cena do editor do Unreal com o cubo e a luz direcional adicionados](images/unreal-quickstart-img-08.png)

5. <span data-ttu-id="c5157-156">Acesse **Arquivo > Salvar Atual**, nomeie o nível **Principal** e selecione **Salvar**</span><span class="sxs-lookup"><span data-stu-id="c5157-156">Go to **File > Save Current**, name your level **Main**, and select **Save**</span></span>

<span data-ttu-id="c5157-157">Com a cena preparada, pressione **Jogar** na barra de ferramentas para ver o cubo em ação!</span><span class="sxs-lookup"><span data-stu-id="c5157-157">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="c5157-158">Quando tiver terminado de admirar seu trabalho, pressione Esc para interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5157-158">When you're finished admiring your work, press Esc to stop the application.</span></span>

![Cena no modo de jogo com o cubo no meio da tela](images/unreal-quickstart-img-09.png)

<span data-ttu-id="c5157-160">Agora que a cena está configurada, vamos prepará-la para algumas interações básicas no RA.</span><span class="sxs-lookup"><span data-stu-id="c5157-160">Now that the scene is set up, lets get it ready for some basic interactions in AR.</span></span> <span data-ttu-id="c5157-161">Primeiro, você precisa criar uma Sessão de RA e pode adicionar blueprints para habilitar a interação das mãos.</span><span class="sxs-lookup"><span data-stu-id="c5157-161">First, you need to create an AR Session and can add blueprints to enable hand interaction.</span></span>

## <a name="adding-a-session-asset"></a><span data-ttu-id="c5157-162">Como adicionar um ativo de sessão</span><span class="sxs-lookup"><span data-stu-id="c5157-162">Adding a session asset</span></span>

<span data-ttu-id="c5157-163">As sessões de RA no Unreal não acontecem espontaneamente.</span><span class="sxs-lookup"><span data-stu-id="c5157-163">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="c5157-164">Para usar uma sessão, você precisará de um ativo de dados ARSessionConfig com o qual trabalhará, que será a sua próxima tarefa:</span><span class="sxs-lookup"><span data-stu-id="c5157-164">To use a session, you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="c5157-165">No **Navegador de Conteúdo**, selecione **Adicionar Novo > Diversos > Ativos de Dados** e verifique se você está no nível da pasta de Conteúdo raiz</span><span class="sxs-lookup"><span data-stu-id="c5157-165">In the **Content Browser**, select **Add New > Miscellaneous > Data Asset** and make sure you're at the root Content folder level</span></span>
2. <span data-ttu-id="c5157-166">Selecione **ARSessionConfig**, clique em **Selecionar** e nomeie o ativo **ARSessionConfig**:</span><span class="sxs-lookup"><span data-stu-id="c5157-166">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**:</span></span>

![Janela Selecionar classe de ativo de dados aberta com o ativo de configuração de sessão de RA realçado](images/unreal-quickstart-img-10.png)

2. <span data-ttu-id="c5157-168">Clique duas vezes em **ARSessionConfig** para abri-lo, selecione **Salvar** com todas as configurações padrão e retorne para a Janela principal:</span><span class="sxs-lookup"><span data-stu-id="c5157-168">Double-click **ARSessionConfig** to open it, **Save** with all default settings, and return to the Main window:</span></span>

![Janela Detalhes do ativo de configuração de sessão de RA](images/unreal-quickstart-img-11.png)

<span data-ttu-id="c5157-170">Com isso feito, a próxima etapa será verificar se a sessão de RA começa e é interrompida quando o nível é carregado e encerrado.</span><span class="sxs-lookup"><span data-stu-id="c5157-170">With that done, your next step is to make sure the AR session starts and stops when the level loads and ends.</span></span> <span data-ttu-id="c5157-171">A boa notícia é que o Unreal tem um blueprint especial chamado **Blueprint de Nível** que funciona como um grafo de eventos global em todo esse nível.</span><span class="sxs-lookup"><span data-stu-id="c5157-171">Luckily, Unreal has a special blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="c5157-172">Conectar o ativo ARSessionConfig no Blueprint de Nível garante que a sessão de RA será disparada exatamente quando o jogo começar.</span><span class="sxs-lookup"><span data-stu-id="c5157-172">Connecting the ARSessionConfig asset in the Level Blueprint guarantees the AR session will fire right when the game starts playing.</span></span>

3. <span data-ttu-id="c5157-173">Na barra de ferramentas do editor, selecione **Blueprints > Abrir Blueprint de Nível**:</span><span class="sxs-lookup"><span data-stu-id="c5157-173">From the editor toolbar, select **Blueprints > Open Level Blueprint**:</span></span>

![Menu do Blueprint aberto com a opção Abrir blueprint de nível realçada](images/unreal-quickstart-img-12.png)

4. <span data-ttu-id="c5157-175">Arraste o nó de execução (ícone de seta à esquerda) para o **Evento BeginPlay** e solte-o</span><span class="sxs-lookup"><span data-stu-id="c5157-175">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release</span></span>
* <span data-ttu-id="c5157-176">Pesquise pelo nó **Iniciar Sessão de RA** e clique em Enter</span><span class="sxs-lookup"><span data-stu-id="c5157-176">Search for the **Start AR Session node** and hit enter</span></span>
* <span data-ttu-id="c5157-177">Clique na lista suspensa **Selecionar Ativo** em **Configuração de Sessão** e escolha o ativo **ARSessionConfig**</span><span class="sxs-lookup"><span data-stu-id="c5157-177">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset</span></span>

![Grafo de blueprint com o evento Iniciar jogo conectado à função Iniciar sessão de RA](images/unreal-quickstart-img-13.png)

5. <span data-ttu-id="c5157-179">Clique com o botão direito do mouse em qualquer lugar do EventGraph e crie um nó **EndPlay de Evento**.</span><span class="sxs-lookup"><span data-stu-id="c5157-179">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> 
* <span data-ttu-id="c5157-180">Arraste o marcador de execução e solte-o e, em seguida, pesquise um nó **Interromper Sessão de RA** e clique em Enter</span><span class="sxs-lookup"><span data-stu-id="c5157-180">Drag the execution pin and release, then search for a **Stop AR Session** node and hit enter</span></span> 
* <span data-ttu-id="c5157-181">Clique em **Compilar**, **Salvar** e retorne para a Janela principal</span><span class="sxs-lookup"><span data-stu-id="c5157-181">Hit **Compile**, then **Save** and return to the Main window</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c5157-182">Se a sessão de RA ainda estiver em execução quando o nível for encerrado, alguns recursos poderão parar de funcionar se você reiniciar o aplicativo durante o streaming para um headset.</span><span class="sxs-lookup"><span data-stu-id="c5157-182">If the AR session is still running when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span>

![Nó Encerrar jogo do evento anexado à função Parar sessão de RA](images/unreal-quickstart-img-14.png)

## <a name="setting-up-inputs"></a><span data-ttu-id="c5157-184">Como configurar entradas</span><span class="sxs-lookup"><span data-stu-id="c5157-184">Setting up inputs</span></span>

1. <span data-ttu-id="c5157-185">Selecione **Editar > Configurações de Projeto** e acesse **Mecanismo > Entrada**</span><span class="sxs-lookup"><span data-stu-id="c5157-185">Select **Edit > Project Settings** and go to the **Engine > Input**</span></span>
2. <span data-ttu-id="c5157-186">Selecione o ícone **+** ao lado de **Mapeamentos de Ação** e crie as ações **RightPinch** e **LeftPinch**:</span><span class="sxs-lookup"><span data-stu-id="c5157-186">Select the **+** icon next to **Action Mappings** and create **RightPinch** and **LeftPinch** actions:</span></span>

![Associando as configurações de entrada com os mapeamentos de ação de pinçagem à direita e à esquerda realçados](images/unreal-quickstart-img-15.jpg)

3. <span data-ttu-id="c5157-188">Mapeie as ações **RightPinch** e **LeftPinch** para as respectivas ações **Interação das mãos do OpenXR MSFT**:</span><span class="sxs-lookup"><span data-stu-id="c5157-188">Map the **RightPinch** and **LeftPinch** actions the to the respective **OpenXR Msft Hand Interaction** actions:</span></span>

![Mapeamentos de ação com as opções de Interação das mãos do OpenXR MSFT realçadas](images/unreal-quickstart-img-16.jpg)

## <a name="setting-up-gestures"></a><span data-ttu-id="c5157-190">Como configurar gestos</span><span class="sxs-lookup"><span data-stu-id="c5157-190">Setting up gestures</span></span>

<span data-ttu-id="c5157-191">Agora que configuramos as entradas, podemos chegar à parte interessante: Adicionar gestos!</span><span class="sxs-lookup"><span data-stu-id="c5157-191">Now that we have setup the inputs, we can get to the exciting part: Adding gestures!</span></span> <span data-ttu-id="c5157-192">Vamos girar o cubo com uma pinçagem à direita e encerrar o aplicativo com uma pinçagem à esquerda.</span><span class="sxs-lookup"><span data-stu-id="c5157-192">Lets rotate the cube on the right pinch and quit the application on left pinch.</span></span>

1. <span data-ttu-id="c5157-193">Abra o **Blueprint de Nível** e adicione **InputAction RightPinch** e **InputAction LeftPinch**</span><span class="sxs-lookup"><span data-stu-id="c5157-193">Open the **Level Blueprint** and add an **InputAction RightPinch** and **InputAction LeftPinch**</span></span>
* <span data-ttu-id="c5157-194">Conecte o evento de pinçagem à direita a um **AddActorLocalRotation** com o seu **Cubo** como o destino e a **Rotação Delta** definida como **X = 0, Y = 0** e **Z = 20**.</span><span class="sxs-lookup"><span data-stu-id="c5157-194">Connect the right pinch event to an **AddActorLocalRotation** with your **Cube** as the target and **Delta Rotation** set to **X = 0, Y = 0**, and **Z = 20**.</span></span> <span data-ttu-id="c5157-195">O cubo agora será girado em 20 graus sempre que você pinçar</span><span class="sxs-lookup"><span data-stu-id="c5157-195">The cube will now rotate by 20 degrees every time you pinch</span></span>
* <span data-ttu-id="c5157-196">Conecte o evento de pinçagem à esquerda para **Encerrar o Jogo**</span><span class="sxs-lookup"><span data-stu-id="c5157-196">Connect the left pinch event to **Quit Game**</span></span>

![Blueprint de nível aberto com as ações de entrada para eventos de pinçagem à direita e à esquerda](images/unreal-quickstart-img-17.jpg)

2. <span data-ttu-id="c5157-198">Nas configurações de **Transformação** do cubo, defina a **Mobilidade** como **Móvel** para que ele possa ser movido dinamicamente:</span><span class="sxs-lookup"><span data-stu-id="c5157-198">In the cube's **Transform** settings, set **Mobility** to **Movable** so it can move dynamically:</span></span>

![Configurações de transformação com a propriedade de mobilidade realçada](images/unreal-quickstart-img-18.jpg)

<span data-ttu-id="c5157-200">Neste ponto, você está pronto para implantar e testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c5157-200">At this point, you're ready to deploy and test the application!</span></span>