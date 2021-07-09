---
title: 2. Inicializar o projeto e seu primeiro aplicativo
description: Parte 2 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: f7cf43e8f1c040660b6a2688e234a271bc071b00
ms.sourcegitcommit: 4a6c26615d52776bdc4faab70391592092a471fc
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2021
ms.locfileid: "110712635"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="7bdde-104">2. Inicializar o projeto e seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="7bdde-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="7bdde-105">No primeiro tutorial, você começará com um projeto do Unreal e habilitará o plug-in do HoloLens, criará e iluminará um nível e adicionará peças de xadrez.</span><span class="sxs-lookup"><span data-stu-id="7bdde-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="7bdde-106">Você usará nossos ativos predefinidos para todos os objetos e materiais 3D. Portanto, não se preocupe em modelar nada por conta própria.</span><span class="sxs-lookup"><span data-stu-id="7bdde-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="7bdde-107">No final deste tutorial, você terá uma tela em branco que está pronta para a realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7bdde-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7bdde-108">Verifique se você atende a todos os pré-requisitos da página [Introdução](/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="7bdde-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="7bdde-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="7bdde-109">Objectives</span></span>

* <span data-ttu-id="7bdde-110">Como configurar um projeto do Unreal para desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="7bdde-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="7bdde-111">Como importar ativos e configurar um cenário</span><span class="sxs-lookup"><span data-stu-id="7bdde-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="7bdde-112">Como criar Atores e eventos em nível de script com blueprints</span><span class="sxs-lookup"><span data-stu-id="7bdde-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="7bdde-113">Como criar um projeto do Unreal</span><span class="sxs-lookup"><span data-stu-id="7bdde-113">Creating a new Unreal project</span></span>

<span data-ttu-id="7bdde-114">A primeira coisa que você precisa é de um projeto com o qual trabalhar.</span><span class="sxs-lookup"><span data-stu-id="7bdde-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="7bdde-115">Se você é um desenvolvedor novo do Unreal, [baixe os arquivos de suporte](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="7bdde-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="7bdde-116">Iniciar Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="7bdde-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="7bdde-117">Selecione **Jogos** em **Novas Categorias de Projeto** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Selecionar um modelo de projeto de jogos](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="7bdde-119">Selecione o modelo **Em Branco** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-119">Select the **Blank** Template and click **Next**.</span></span> 

![Selecionar o modelo Em Branco](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="7bdde-121">Defina **C++** , **3D ou 2D Escalonável, Celular/Tablet** e **Nenhum Conteúdo Inicial** como as **Configurações de Projeto** e escolha uma localização de salvamento e clique em **Criar Projeto**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="7bdde-122">Você precisará selecionar um projeto C++ em vez de um projeto Blueprint para criar o plug-in das Ferramentas de UX, que você vai configurar mais adiante na seção 4.</span><span class="sxs-lookup"><span data-stu-id="7bdde-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Configurações iniciais do projeto](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="7bdde-124">O projeto deve ser aberto automaticamente no editor Unreal, o que significa que você está pronto para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="7bdde-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="7bdde-125">Como habilitar os plugins necessários</span><span class="sxs-lookup"><span data-stu-id="7bdde-125">Enabling required plugins</span></span>

<span data-ttu-id="7bdde-126">Para usar os recursos disponíveis por meio da plataforma de realidade misturada da Microsoft, primeiro você precisa instalar e habilitar o plug-in OpenXR da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7bdde-126">In order to use the features available via Microsoft's mixed reality platform, you'll first need to install and enable the Microsoft OpenXR plugin.</span></span> <span data-ttu-id="7bdde-127">Para saber mais sobre o plug-in, confira o projeto no [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span><span class="sxs-lookup"><span data-stu-id="7bdde-127">To learn more about the plugin, you can check out the project on [GitHub](https://github.com/microsoft/Microsoft-OpenXR-Unreal).</span></span>

1. <span data-ttu-id="7bdde-128">Abra o Epic Games Launcher.</span><span class="sxs-lookup"><span data-stu-id="7bdde-128">Open the Epic Games Launcher.</span></span> <span data-ttu-id="7bdde-129">Navegue até o Marketplace do Unreal Engine e pesquise "[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)".</span><span class="sxs-lookup"><span data-stu-id="7bdde-129">Navigate to Unreal Engine Marketplace and search for "[Microsoft OpenXR](https://www.unrealengine.com/marketplace/product/ef8930ca860148c498b46887da196239)".</span></span> <span data-ttu-id="7bdde-130">Instale o plug-in em seu mecanismo.</span><span class="sxs-lookup"><span data-stu-id="7bdde-130">Install the plugin to your engine.</span></span>

![Marketplace do Unreal](images/unreal-uxt/2-openxr-plugin.PNG)

2. <span data-ttu-id="7bdde-132">Retorne ao editor do Unreal, acesse as **Configurações de projeto** > **Plug-ins** e pesquise "Microsoft OpenXR".</span><span class="sxs-lookup"><span data-stu-id="7bdde-132">Back in the Unreal editor, go to **Project Settings** > **Plugins** and search for "Microsoft OpenXR".</span></span> <span data-ttu-id="7bdde-133">Verifique se o plug-in está ativado e reinicie o editor, se solicitado.</span><span class="sxs-lookup"><span data-stu-id="7bdde-133">Ensure the plugin is enabled and restart the editor if prompted.</span></span>

![Ativação do plug-in OpenXR da Microsoft](images/unreal-uxt/2-enable-plugin.PNG)

<span data-ttu-id="7bdde-135">A ativação do plug-in OpenXR da Microsoft habilitará automaticamente todos os outros plug-ins necessários para o desenvolvimento de realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7bdde-135">Enabling the Microsoft OpenXR plugin will automatically enable all the other plugins required for mixed reality development.</span></span> <span data-ttu-id="7bdde-136">Observe que o plug-in "Windows Mixed Reality da Microsoft" deve ser desabilitado para usar o OpenXR.</span><span class="sxs-lookup"><span data-stu-id="7bdde-136">Note that the "Microsoft Windows Mixed Reality" plugin must be disabled in order to use OpenXR.</span></span> 

## <a name="creating-a-level"></a><span data-ttu-id="7bdde-137">Criar um nível</span><span class="sxs-lookup"><span data-stu-id="7bdde-137">Creating a level</span></span>
<span data-ttu-id="7bdde-138">Sua próxima tarefa será criar uma configuração de jogador com um ponto de partida e um cubo para referência e escala.</span><span class="sxs-lookup"><span data-stu-id="7bdde-138">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="7bdde-139">Selecione **Arquivo > Novo Nível** e escolha **Nível Vazio**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-139">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="7bdde-140">A cena padrão no visor agora deve estar vazia.</span><span class="sxs-lookup"><span data-stu-id="7bdde-140">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="7bdde-141">Selecione **Básico** na guia **Modos** e arraste **PlayerStart** para a cena.</span><span class="sxs-lookup"><span data-stu-id="7bdde-141">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="7bdde-142">Defina **Localização** como **X = 0**, **Y = 0** e **Z = 0** na guia **Detalhes** para definir o usuário no centro da cena quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="7bdde-142">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![Visor com PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="7bdde-144">Arraste um **Cubo** da guia **Básico** para a cena.</span><span class="sxs-lookup"><span data-stu-id="7bdde-144">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="7bdde-145">Defina **Localização** como **X = 50**, **Y = 0** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-145">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="7bdde-146">para posicionar o cubo a 50 cm do jogador na hora de início.</span><span class="sxs-lookup"><span data-stu-id="7bdde-146">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="7bdde-147">Altere **Escala** para **X = 0,2**, **Y = 0,2** e **Z = 0,2** para diminuir o cubo.</span><span class="sxs-lookup"><span data-stu-id="7bdde-147">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="7bdde-148">Você não poderá ver o cubo, a menos que adicione uma luz à cena, que será a sua última tarefa antes de testar a cena em questão.</span><span class="sxs-lookup"><span data-stu-id="7bdde-148">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="7bdde-149">Alterne para a guia **Luzes** no painel **Modos** e arraste uma **Luz Direcional** até a cena.</span><span class="sxs-lookup"><span data-stu-id="7bdde-149">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="7bdde-150">Posicione a luz acima **PlayerStart** para que você possa vê-la.</span><span class="sxs-lookup"><span data-stu-id="7bdde-150">Position the light above **PlayerStart** so you can see it.</span></span>

![Visor com luz adicionada](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="7bdde-152">Acesse **Arquivo > Salvar Atual**, nomeie o nível **Principal** e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-152">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="7bdde-153">Com a cena preparada, pressione **Jogar** na barra de ferramentas para ver o cubo em ação!</span><span class="sxs-lookup"><span data-stu-id="7bdde-153">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="7bdde-154">Quando tiver terminado de admirar seu trabalho, pressione **Esc** para interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7bdde-154">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Um cubo no visor](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="7bdde-156">Agora que a cena está configurada, você pode começar a adicionar o tabuleiro de xadrez e a peça para completar o ambiente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7bdde-156">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="7bdde-157">Como importar ativos</span><span class="sxs-lookup"><span data-stu-id="7bdde-157">Importing assets</span></span>
<span data-ttu-id="7bdde-158">A cena está parecendo um tanto vazia no momento, mas você corrigirá isso importando os ativos prontos para o projeto.</span><span class="sxs-lookup"><span data-stu-id="7bdde-158">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="7bdde-159">Baixe e descompacte a pasta de ativos do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) usando o [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="7bdde-159">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="7bdde-160">Selecione **Adicionar Novo > Nova Pasta** no **Navegador de Conteúdo** e nomeie-o **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-160">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="7bdde-161">Clique duas vezes na nova pasta, em que você importará os ativos 3D.</span><span class="sxs-lookup"><span data-stu-id="7bdde-161">Double-click the new folder where you'll import the 3D assets.</span></span>

![Mostrar ou ocultar o painel de fontes](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="7bdde-163">Selecione **Importar** no **Navegador de Conteúdo**, escolha todos os itens da pasta de ativos descompactados e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-163">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="7bdde-164">Os ativos incluem as malhas de objetos 3D para o tabuleiro de xadrez e as peças no formato FBX, bem como os mapas de textura no formato TGA que você usará para os materiais.</span><span class="sxs-lookup"><span data-stu-id="7bdde-164">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="7bdde-165">Quando a janela Opções de Importação do FBX for exibida, expanda a seção **Material** e altere **Método de Importação de Material** para **Não Criar o Material**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-165">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="7bdde-166">Selecione **Importar Tudo**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-166">Select **Import All**.</span></span>

![Opções em Importar FBX](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="7bdde-168">Isso é tudo o que você precisa fazer com relação aos ativos.</span><span class="sxs-lookup"><span data-stu-id="7bdde-168">That's all you need to do for the assets.</span></span> <span data-ttu-id="7bdde-169">Seu próximo conjunto de tarefas é criar os blocos de construção do aplicativo com blueprints.</span><span class="sxs-lookup"><span data-stu-id="7bdde-169">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="7bdde-170">Como adicionar blueprints</span><span class="sxs-lookup"><span data-stu-id="7bdde-170">Adding blueprints</span></span>

1. <span data-ttu-id="7bdde-171">Selecione **Adicionar Novo > Nova Pasta** no **Navegador de Conteúdo** e nomeie-o **Blueprints**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-171">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="7bdde-172">Se você não está familiarizado com [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), saiba que eles são ativos especiais que fornecem uma interface baseada em nó para criação de tipos de Atores e eventos de nível de script.</span><span class="sxs-lookup"><span data-stu-id="7bdde-172">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="7bdde-173">Clique duas vezes na pasta **Blueprints**, depois clique com o botão direito do mouse e selecione **Classe de Blueprint**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-173">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="7bdde-174">Selecione **Ator** e nomeie o novo blueprint como **Tabuleiro**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-174">Select **Actor** and name the blueprint **Board**.</span></span> 

![Selecione uma classe pai para seu Blueprint](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="7bdde-176">O novo blueprint **Tabuleiro** agora aparece na pasta **Blueprints**, conforme mostrado na captura de tela a seguir.</span><span class="sxs-lookup"><span data-stu-id="7bdde-176">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![O novo Blueprint Board](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="7bdde-178">Você está pronto para começar a adicionar materiais aos objetos criados.</span><span class="sxs-lookup"><span data-stu-id="7bdde-178">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="7bdde-179">Como trabalhar com materiais</span><span class="sxs-lookup"><span data-stu-id="7bdde-179">Working with materials</span></span>
<span data-ttu-id="7bdde-180">Os objetos que você criou são no padrão cinza, o que não os deixa com uma aparência muito divertida.</span><span class="sxs-lookup"><span data-stu-id="7bdde-180">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="7bdde-181">Adicionar materiais e malhas a seus objetos é o último conjunto de tarefas neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="7bdde-181">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="7bdde-182">Clique duas vezes em **Painel** para abrir o editor de blueprints.</span><span class="sxs-lookup"><span data-stu-id="7bdde-182">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="7bdde-183">Selecione **Adicionar Componente > Cena** no painel **Componentes** e nomeie-o **Root**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-183">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="7bdde-184">Observe que **Root** aparece como um filho de **DefaultSceneRoot** na captura de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="7bdde-184">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Como substituir a raiz no blueprint](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="7bdde-186">Clique e arraste **Root** para **DefaultSceneRoot** para substituí-lo e livrar-se da esfera no visor.</span><span class="sxs-lookup"><span data-stu-id="7bdde-186">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Substituindo a raiz](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="7bdde-188">Selecione **Adicionar Componente > Malha Estática** no painel **Componentes** e nomeie-o **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-188">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="7bdde-189">Ele será exibido como um objeto filho em **Root**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-189">It will appear as a child object under **Root**.</span></span>

![Adicionando uma malha estática](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="7bdde-191">Selecione **SM_Board**, role o painel para baixo até a seção **Malha Estática** do painel **Detalhes** e selecione **ChessBoard** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="7bdde-191">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![A malha do tabuleiro no visor](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="7bdde-193">Ainda no painel **Detalhes**, expanda a seção **Materiais** e selecione **Criar Ativo > Material** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="7bdde-193">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="7bdde-194">Nomeie o material **M_ChessBoard** e salve-o na pasta **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-194">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Criar um material](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="7bdde-196">Clique duas vezes na imagem do material **M_ChessBoard** para abrir o editor de material.</span><span class="sxs-lookup"><span data-stu-id="7bdde-196">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Abrir editor de material](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="7bdde-198">No Editor de Material, clique com o botão direito do mouse e procure **Exemplo de Textura**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-198">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="7bdde-199">Expanda a seção **Base de Textura de Expressão do Material** no painel **Detalhes** e defina **Textura** para **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-199">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="7bdde-200">Arraste o marcador de saída **RGB** para o marcador de Cor Base de **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-200">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Definir a cor base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="7bdde-202">Repita a etapa anterior mais quatro vezes para criar mais quatro nós **Exemplo de Textura** com as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="7bdde-202">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="7bdde-203">Defina **Textura** como **ChessBoard_AO** e vincule o **RGB** ao marcador **Oclusão Ambiente**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-203">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="7bdde-204">Defina **Textura** como **ChessBoard_Metal** e vincule o **RGB** ao marcador **Metálico**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-204">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="7bdde-205">Defina **Textura** como **ChessBoard_Normal** e vincule o **RGB** ao marcador **Normal**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-205">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="7bdde-206">Defina **Textura** como **ChessBoard_Rough** e vincule o **RGB** ao marcador **Aspereza**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-206">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="7bdde-207">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-207">Click **Save**.</span></span> 

![Conectar as texturas restantes](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="7bdde-209">Verifique se a configuração do material está parecida com a captura de tela acima antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7bdde-209">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="7bdde-210">Como popular a cena</span><span class="sxs-lookup"><span data-stu-id="7bdde-210">Populating the scene</span></span>
<span data-ttu-id="7bdde-211">Se você retornar ao blueprint **Tabuleiro**, verá que o material que acabou de criar foi aplicado.</span><span class="sxs-lookup"><span data-stu-id="7bdde-211">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="7bdde-212">Tudo o que falta fazer é configurar a cena!</span><span class="sxs-lookup"><span data-stu-id="7bdde-212">All that's left is setting up the scene!</span></span> <span data-ttu-id="7bdde-213">Primeiro, altere as propriedades a seguir para assegurar que o tabuleiro seja de um tamanho razoável e esteja inclinado corretamente quando posicionado na cena:</span><span class="sxs-lookup"><span data-stu-id="7bdde-213">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="7bdde-214">Defina **Escala** como **(0,05, 0,05, 0,05)** e **Rotação Z** como **90**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-214">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="7bdde-215">Clique em **Compilar** na barra de ferramentas superior e depois em **Salvar**, então volte para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="7bdde-215">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Tabuleiro de xadrez com material aplicado](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="7bdde-217">Clique com o botão direito do mouse em **Cubo > Editar > Excluir** e arraste **Tabuleiro** do **Navegador de Conteúdo** para o visor.</span><span class="sxs-lookup"><span data-stu-id="7bdde-217">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="7bdde-218">Defina **Localização** como **X = 80**, **Y = 0** e **Z = -20**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-218">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="7bdde-219">Selecione o botão **Jogar** para ver o novo tabuleiro no nível.</span><span class="sxs-lookup"><span data-stu-id="7bdde-219">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="7bdde-220">Pressione **ESC** para retornar ao editor.</span><span class="sxs-lookup"><span data-stu-id="7bdde-220">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="7bdde-221">Agora você seguirá as mesmas etapas para criar uma peça de xadrez, do mesmo modo que você fez com o tabuleiro:</span><span class="sxs-lookup"><span data-stu-id="7bdde-221">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="7bdde-222">Acesse a pasta **Blueprints**, clique com o botão direito do mouse, selecione **Classe de Blueprint** e escolha **Ator**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-222">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="7bdde-223">Nomeie esse ator como **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-223">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="7bdde-224">Clique duas vezes em **WhiteKing** para abri-lo no Editor do Blueprint, selecione **Adicionar Componente > Cena** e nomeie-o **Root**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-224">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="7bdde-225">Arraste e solte **Root** em **DefaultSceneRoot** para substituí-lo.</span><span class="sxs-lookup"><span data-stu-id="7bdde-225">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="7bdde-226">Clique em **Adicionar Componente > Malha Estática** e nomeie-o como **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-226">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="7bdde-227">No painel Detalhes, defina **Malha Estática** como **Chess_King** e **Material** como um novo material chamado **M_ChessWhite**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-227">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="7bdde-228">Abra **M_ChessWhite** no Editor de material e conecte os nós de **Exemplo de Textura** a seguir ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="7bdde-228">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="7bdde-229">Defina **Textura** como **ChessWhite_Albedo** e vincule o **RGB** ao marcador **Cor de Base**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-229">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="7bdde-230">Defina **Textura** como **ChessWhite_AO** e vincule o **RGB** ao marcador **Oclusão Ambiente**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-230">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="7bdde-231">Defina **Textura** como **ChessWhite_Metal** e vincule o **RGB** ao marcador **Metálico**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-231">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="7bdde-232">Defina **Textura** como **ChessWhite_Normal** e vincule o **RGB** ao marcador **Normal**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-232">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="7bdde-233">Defina **Textura** como **ChessWhite_Rough** e vincule o **RGB** ao marcador **Aspereza**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-233">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="7bdde-234">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-234">Click **Save**.</span></span> 

<span data-ttu-id="7bdde-235">Verifique se o material **M_ChessKing** tem aparência semelhante à da imagem a seguir antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="7bdde-235">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Criar o material para o rei do xadrez](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="7bdde-237">Você está quase lá, falta apenas adicionar a nova peça de xadrez à cena:</span><span class="sxs-lookup"><span data-stu-id="7bdde-237">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="7bdde-238">Abra o blueprint **WhiteKing**, altere a **Escala** para **(0,05; 0,05; 0,05)** e a **Rotação em Z** para **90**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-238">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="7bdde-239">Compile e salve o blueprint e, em seguida, retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="7bdde-239">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="7bdde-240">Arraste **WhiteKing** para o visor, alterne para o painel **Esboço do Mundo** e arraste **WhiteKing** para o **Tabuleiro** para torná-lo um objeto filho.</span><span class="sxs-lookup"><span data-stu-id="7bdde-240">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Contorno do Mundo](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="7bdde-242">No painel **Detalhes**, em **Transformar**, defina a **Localização** de **WhiteKing** como **X = -26**, **Y = 4** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="7bdde-242">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="7bdde-243">Tudo concluído!</span><span class="sxs-lookup"><span data-stu-id="7bdde-243">That's a wrap!</span></span> <span data-ttu-id="7bdde-244">Selecione **Jogar** para ver o nível preenchido em ação e clique em **ESC** quando estiver pronto para sair.</span><span class="sxs-lookup"><span data-stu-id="7bdde-244">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="7bdde-245">Você viu muito conteúdo apenas criando um projeto simples, mas agora está pronto para passar para a próxima parte da série: configuração para a realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="7bdde-245">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="7bdde-246">Próxima seção: 3. Configurar seu projeto para a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="7bdde-246">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)