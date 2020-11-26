---
title: 3. Como configurar seu projeto para a realidade misturada
description: Parte 3 de 6 em uma série de tutoriais para criar um aplicativo de xadrez simples usando o Unreal Engine 4 e o plug-in Ferramentas de UX do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 82e210aff35f1c41547f022b91114cbca1419830
ms.sourcegitcommit: dd13a32a5bb90bd53eeeea8214cd5384d7b9ef76
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94679875"
---
# <a name="3-setting-up-your-project-for-mixed-reality"></a><span data-ttu-id="ec4f1-104">3. Como configurar seu projeto para a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="ec4f1-104">3. Setting up your project for mixed reality</span></span>

## <a name="overview"></a><span data-ttu-id="ec4f1-105">Visão geral</span><span class="sxs-lookup"><span data-stu-id="ec4f1-105">Overview</span></span>

<span data-ttu-id="ec4f1-106">No tutorial anterior, você passou tempo configurando o projeto de aplicativo de xadrez.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-106">In the previous tutorial, you spent time setting up the chess app project.</span></span> <span data-ttu-id="ec4f1-107">Esta seção vai orientá-lo pela configuração do aplicativo para o desenvolvimento de realidade misturada, o que significa adicionar uma sessão de RA.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-107">This section is going to walk you through setting up the app for mixed reality development, which means adding an AR session.</span></span> <span data-ttu-id="ec4f1-108">Para essa tarefa, você usará um ativo de dados ARSessionConfig que tem muitas configurações úteis de RA, como mapeamento espacial e oclusão.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-108">You'll be using an ARSessionConfig data asset for this task, which has a lot of useful AR settings like spatial mapping and occlusion.</span></span> <span data-ttu-id="ec4f1-109">Se você quiser se aprofundar, a documentação do Unreal Engine tem mais detalhes sobre o ativo [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) e a classe [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html).</span><span class="sxs-lookup"><span data-stu-id="ec4f1-109">If you want to dive deeper, the Unreal Engine documentation has more details on the [ARSessionConfig](https://docs.unrealengine.com/en-US/PythonAPI/class/ARSessionConfig.html) asset and the [UARSessionConfig](https://docs.unrealengine.com/en-US/API/Runtime/AugmentedReality/UARSessionConfig/index.html) class.</span></span>

## <a name="objectives"></a><span data-ttu-id="ec4f1-110">Objetivos</span><span class="sxs-lookup"><span data-stu-id="ec4f1-110">Objectives</span></span>
* <span data-ttu-id="ec4f1-111">Como trabalhar com configurações de RA do Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="ec4f1-111">Working with Unreal Engine's AR settings</span></span> 
* <span data-ttu-id="ec4f1-112">Como usar um ativo de dados do ARSessionConfig</span><span class="sxs-lookup"><span data-stu-id="ec4f1-112">Using an ARSessionConfig data asset</span></span>
* <span data-ttu-id="ec4f1-113">Como configurar um peão e um modo de jogo</span><span class="sxs-lookup"><span data-stu-id="ec4f1-113">Setting up a Pawn and game mode</span></span>

## <a name="adding-the-session-asset"></a><span data-ttu-id="ec4f1-114">Como adicionar o ativo de sessão</span><span class="sxs-lookup"><span data-stu-id="ec4f1-114">Adding the session asset</span></span>
<span data-ttu-id="ec4f1-115">As sessões de RA no Unreal não acontecem espontaneamente.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-115">AR sessions in Unreal don't happen by themselves.</span></span> <span data-ttu-id="ec4f1-116">Para usar uma sessão, você precisa de um ativo de dados do ARSessionConfig com o qual trabalhar, que é sua próxima tarefa:</span><span class="sxs-lookup"><span data-stu-id="ec4f1-116">To use a session you need an ARSessionConfig data asset to work with, which is your next task:</span></span>

1. <span data-ttu-id="ec4f1-117">Clique em **Adicionar Novo > Diversos > Ativo de Dados** no **Navegador de Conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-117">Click **Add New > Miscellaneous > Data Asset** in the **Content Browser**.</span></span> <span data-ttu-id="ec4f1-118">Verifique se você está no nível raiz da pasta **Conteúdo**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-118">Make sure you're at the root **Content** folder level.</span></span> 
    * <span data-ttu-id="ec4f1-119">Selecione **ARSessionConfig**, clique em **Selecionar** e nomeie o ativo **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-119">Select **ARSessionConfig**, click **Select**, and name the asset **ARSessionConfig**.</span></span>

![Criar um ativo de dados](images/unreal-uxt/3-createasset.PNG)

3. <span data-ttu-id="ec4f1-121">Clique duas vezes em **ARSessionConfig** para abri-lo, deixe todas as configurações padrão e clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-121">Double-click **ARSessionConfig** to open it, leave all default settings and hit **Save**.</span></span> <span data-ttu-id="ec4f1-122">Volte para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-122">Return to the Main window.</span></span> 

![Configuração de sessão de RA](images/unreal-uxt/3-arsessionconfig.PNG)

<span data-ttu-id="ec4f1-124">Com isso feito, a próxima etapa será verificar se a sessão de RA começa quando o nível é carregado e se ela é interrompida quando o nível é encerrado.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-124">With that done, your next step is to make sure that the AR session starts when the level loads and stops when the level ends.</span></span> <span data-ttu-id="ec4f1-125">O Unreal tem um tipo especial de blueprint chamado **Blueprint de Nível**, que atua como um grafo de eventos global em todo esse nível.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-125">Luckily, Unreal has a special kind of blueprint called a **Level Blueprint** that acts as a level-wide global event graph.</span></span> <span data-ttu-id="ec4f1-126">Conectar o ativo ARSessionConfig no **Blueprint de Nível** garante que a sessão de RA será disparada exatamente quando o jogo começar.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-126">Connecting the ARSessionConfig asset in the **Level Blueprint** guarantees the AR session will fire right when the game starts playing.</span></span>

1. <span data-ttu-id="ec4f1-127">Clique em **Blueprints > Abrir Blueprint de Nível** na barra de ferramentas do editor:</span><span class="sxs-lookup"><span data-stu-id="ec4f1-127">Click **Blueprints > Open Level Blueprint** from the editor toolbar:</span></span> 

![Abrir Blueprint de Nível](images/unreal-uxt/3-level-blueprint.PNG)

5. <span data-ttu-id="ec4f1-129">Arraste o nó de execução (ícone de seta para a esquerda) saindo de **Evento BeginPlay** e solte-o.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-129">Drag the execution node (left-facing arrow icon) off **Event BeginPlay** and release.</span></span> <span data-ttu-id="ec4f1-130">Procure o nó **Iniciar Sessão de RA** e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-130">Search for the **Start AR Session** node and hit enter.</span></span>  
    * <span data-ttu-id="ec4f1-131">Clique na lista suspensa **Selecionar Ativo** em **Configuração de Sessão** e escolha o ativo **ARSessionConfig**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-131">Click the **Select Asset** dropdown under **Session Config** and choose the **ARSessionConfig** asset.</span></span> 

![Iniciar Sessão de RA](images/unreal-uxt/3-start-ar-session.PNG)

6. <span data-ttu-id="ec4f1-133">Clique com o botão direito do mouse em qualquer lugar do EventGraph e crie um nó **EndPlay de Evento**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-133">Right-click anywhere in the EventGraph and create a new **Event EndPlay** node.</span></span> <span data-ttu-id="ec4f1-134">Arraste o pino de execução e solte-o.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-134">Drag the execution pin and release.</span></span> <span data-ttu-id="ec4f1-135">Procure um nó **Interromper Sessão de RA** e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-135">Search for a **Stop AR Session** node and hit enter.</span></span> <span data-ttu-id="ec4f1-136">Se a sessão de RA não for interrompida quando o nível for encerrado, alguns recursos poderão parar de funcionar se você reiniciar o aplicativo durante o streaming para um headset.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-136">If the AR session isn't stopped when the level ends, certain features may stop working if you restart your app while streaming to a headset.</span></span> 
    * <span data-ttu-id="ec4f1-137">Escolha **Compilar**, depois **Salvar** e retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-137">Hit **Compile**, then **Save** and return to the Main window.</span></span>

![Interromper Sessão de RA](images/unreal-uxt/3-stoparsession.PNG)

## <a name="create-a-pawn"></a><span data-ttu-id="ec4f1-139">Criar um Peão</span><span class="sxs-lookup"><span data-stu-id="ec4f1-139">Create a Pawn</span></span>
<span data-ttu-id="ec4f1-140">Neste ponto, o projeto ainda precisa de um objeto de jogador.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-140">At this point, the project still needs a player object.</span></span> <span data-ttu-id="ec4f1-141">No Unreal, um **Peão** representa o usuário no jogo, mas neste caso, será a experiência do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-141">In Unreal, a **Pawn** represents the user in the game, but in this case it's going to be the HoloLens 2 experience.</span></span>

1. <span data-ttu-id="ec4f1-142">Clique em **Adicionar Novo > Classe de Blueprint** na pasta **Conteúdo** e expanda a seção **Todas as Classes** na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-142">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="ec4f1-143">Pesquise **DefaultPawn**, clique em **Selecionar**, nomeie-o **MRPawn** e clique duas vezes no ativo para abri-lo.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-143">Search for **DefaultPawn**, click **Select**, name it **MRPawn**, and double-click the asset to open.</span></span> 

![Criar um Peão herdando de DefaultPawn](images/unreal-uxt/3-defaultpawn.PNG)

> [!NOTE]
> <span data-ttu-id="ec4f1-145">Por padrão, os Peões têm componentes de malha e colisão.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-145">By default, Pawns have mesh and collision components.</span></span> <span data-ttu-id="ec4f1-146">Na maioria dos projetos do Unreal, os Peões são objetos sólidos que podem colidir com outros componentes.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-146">In most Unreal projects, Pawns are solid objects that can collide with other components.</span></span> <span data-ttu-id="ec4f1-147">Já que o peão e o usuário são a mesma coisa em realidade misturada, você deseja ser capaz de passar pelos hologramas sem nenhuma colisão.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-147">Since the Pawn and user are the same in mixed reality, you want to be able to pass through holograms without any collisions.</span></span> 

2. <span data-ttu-id="ec4f1-148">Selecione **CollisionComponent** no painel **Componentes** e role para baixo até a seção **Colisão** do painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-148">Select **CollisionComponent** from the **Components** panel and scroll down to the **Collision** section of the **Details** panel.</span></span> 
    * <span data-ttu-id="ec4f1-149">Clique na lista suspensa de **Predefinições de Colisão** e altere o valor para **NoCollision**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-149">Click the **Collision Presets** dropdown and change the value to **NoCollision**.</span></span> 
    * <span data-ttu-id="ec4f1-150">Faça o mesmo para o **MeshComponent**</span><span class="sxs-lookup"><span data-stu-id="ec4f1-150">Do the same for the **MeshComponent**</span></span>

![Ajustar as Predefinições de Colisão do Peão](images/unreal-uxt/3-nocollision.PNG)

3. <span data-ttu-id="ec4f1-152">Clique em **Adicionar Componente > Câmera** no painel **Componentes** e nomeie-o como **Câmera**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-152">Click **Add Component > Camera** from the **Components** panel and name it **Camera**.</span></span> <span data-ttu-id="ec4f1-153">Isso permite que a câmera do player se mova com o dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-153">This allows the player camera to move with the HoloLens 2 device.</span></span>

> [!NOTE]
> <span data-ttu-id="ec4f1-154">Verifique se o componente **Câmera** é um filho direto da raiz (**CollisionComponent**).</span><span class="sxs-lookup"><span data-stu-id="ec4f1-154">Make sure that the **Camera** component is a direct child of the root (**CollisionComponent**).</span></span>

4. <span data-ttu-id="ec4f1-155">**Compile** e **salve** o blueprint.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-155">**Compile** and **Save** the Blueprint.</span></span>

<span data-ttu-id="ec4f1-156">Com seu trabalho aqui terminado, retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-156">With your work here done, return to the Main Window.</span></span>

## <a name="create-a-game-mode"></a><span data-ttu-id="ec4f1-157">Criar um Modo de Jogo</span><span class="sxs-lookup"><span data-stu-id="ec4f1-157">Create a Game Mode</span></span>
<span data-ttu-id="ec4f1-158">A última peça do quebra-cabeça da configuração da realidade misturada é o Modo de Jogo.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-158">The last puzzle piece of the mixed reality setup is the Game Mode.</span></span> <span data-ttu-id="ec4f1-159">O Modo de Jogo determina um diversas configurações para o jogo ou a experiência, incluindo o peão padrão a ser usado.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-159">The Game Mode determines a number of settings for the game or experience, including the default pawn to use.</span></span>

1.  <span data-ttu-id="ec4f1-160">Clique em **Adicionar Novo > Classe de Blueprint** na pasta **Conteúdo** e expanda a seção **Todas as Classes** na parte inferior.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-160">Click **Add New > Blueprint Class** in the **Content** folder and expand the **All Classes** section at the bottom.</span></span> 
    * <span data-ttu-id="ec4f1-161">Pesquise por **Base do Modo de Jogo**, nomeie-a como **MRGameMode** e clique duas vezes para abri-la.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-161">Search for **Game Mode Base**, name it **MRGameMode** and double-click to open.</span></span> 

![MRGameMode no Navegador de Conteúdo](images/unreal-uxt/3-gamemode.PNG)

2.  <span data-ttu-id="ec4f1-163">Vá para a seção **Classes** no painel **Detalhes** e altere a **Classe de Peão Padrão** para **MRPawn**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-163">Go to the **Classes** section in the **Details** panel and change the **Default Pawn Class** to **MRPawn**.</span></span> 
    * <span data-ttu-id="ec4f1-164">Escolha **Compilar**, depois **Salvar** e retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-164">Hit **Compile**, then **Save** and return to the Main window.</span></span> 

![Definir a Classe Peão Padrão](images/unreal-uxt/3-setpawn.PNG)

3.  <span data-ttu-id="ec4f1-166">Selecione **Editar > Configurações de Projetos** e clique em **Mapas e Modos** na lista à esquerda.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-166">Select **Edit > Projects Settings** and click **Maps & Modes** in the left-hand list.</span></span> 
    * <span data-ttu-id="ec4f1-167">Expanda **Modos Padrão** e altere **Modo de Jogo Padrão** para **MRGameMode**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-167">Expand **Default Modes** and change **Default Game Mode** to **MRGameMode**.</span></span> 
    * <span data-ttu-id="ec4f1-168">Expanda **Mapas Padrão** e altere **EditorStartupMap** e **GameDefaultMap** para **Principal**.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-168">Expand **Default Maps** and change both **EditorStartupMap** and **GameDefaultMap** to **Main**.</span></span> <span data-ttu-id="ec4f1-169">Dessa forma, quando você fechar o editor e abri-lo novamente ou jogar o jogo, o mapa Principal estará selecionado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-169">This way when you close and reopen the editor, or play the game, the Main map will be selected by default.</span></span>

![Configurações do projeto – Mapas e Modos](images/unreal-uxt/3-mapsandmodes.PNG)

<span data-ttu-id="ec4f1-171">Com o projeto totalmente configurado para realidade misturada, você está pronto para passar para o próximo tutorial e começar a adicionar a entrada do usuário ao cenário.</span><span class="sxs-lookup"><span data-stu-id="ec4f1-171">With the project fully setup for mixed reality, you're ready to move on to the next tutorial and start adding user input to the scene.</span></span> 

[<span data-ttu-id="ec4f1-172">Próxima seção: 4. Como tornar sua cena interativa</span><span class="sxs-lookup"><span data-stu-id="ec4f1-172">Next Section: 4. Making your scene interactive</span></span>](unreal-uxt-ch4.md)
