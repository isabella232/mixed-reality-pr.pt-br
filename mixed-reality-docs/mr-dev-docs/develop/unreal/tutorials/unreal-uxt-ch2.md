---
title: 2. Inicializar o projeto e seu primeiro aplicativo
description: Parte 2 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 06/10/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: 9e02ea6cb2710b4661e97dc8b0d5f4f48ab09fa7
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583903"
---
# <a name="2-initializing-your-project-and-first-application"></a><span data-ttu-id="2e088-104">2. Inicializar o projeto e seu primeiro aplicativo</span><span class="sxs-lookup"><span data-stu-id="2e088-104">2. Initializing your project and first application</span></span>

<span data-ttu-id="2e088-105">No primeiro tutorial, você começará com um projeto do Unreal e habilitará o plug-in do HoloLens, criará e iluminará um nível e adicionará peças de xadrez.</span><span class="sxs-lookup"><span data-stu-id="2e088-105">In the first tutorial, you'll start out with a new Unreal project and enable the HoloLens plugin, create and light a level, and add chess pieces.</span></span> <span data-ttu-id="2e088-106">Você usará nossos ativos predefinidos para todos os objetos e materiais 3D. Portanto, não se preocupe em modelar nada por conta própria.</span><span class="sxs-lookup"><span data-stu-id="2e088-106">You'll be using our pre-made assets for all 3D objects and materials, so don't worry about modeling anything yourself.</span></span> <span data-ttu-id="2e088-107">No final deste tutorial, você terá uma tela em branco que está pronta para a realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2e088-107">By the end of this tutorial, you'll have a blank canvas that's ready for mixed reality.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2e088-108">Verifique se você atende a todos os pré-requisitos da página [Introdução](/windows/mixed-reality/unreal-uxt-ch1).</span><span class="sxs-lookup"><span data-stu-id="2e088-108">Make sure you have all the prerequisites from the [Getting Started](/windows/mixed-reality/unreal-uxt-ch1) page.</span></span>

## <a name="objectives"></a><span data-ttu-id="2e088-109">Objetivos</span><span class="sxs-lookup"><span data-stu-id="2e088-109">Objectives</span></span>

* <span data-ttu-id="2e088-110">Como configurar um projeto do Unreal para desenvolvimento no HoloLens</span><span class="sxs-lookup"><span data-stu-id="2e088-110">Configuring an Unreal project for HoloLens development</span></span>
* <span data-ttu-id="2e088-111">Como importar ativos e configurar um cenário</span><span class="sxs-lookup"><span data-stu-id="2e088-111">Importing assets and setting up a scene</span></span>
* <span data-ttu-id="2e088-112">Como criar Atores e eventos em nível de script com blueprints</span><span class="sxs-lookup"><span data-stu-id="2e088-112">Creating Actors and script-level events with blueprints</span></span>

## <a name="creating-a-new-unreal-project"></a><span data-ttu-id="2e088-113">Como criar um projeto do Unreal</span><span class="sxs-lookup"><span data-stu-id="2e088-113">Creating a new Unreal project</span></span>

<span data-ttu-id="2e088-114">A primeira coisa que você precisa é de um projeto com o qual trabalhar.</span><span class="sxs-lookup"><span data-stu-id="2e088-114">The first thing you need is a project to work with.</span></span> <span data-ttu-id="2e088-115">Se você é um desenvolvedor novo do Unreal, [baixe os arquivos de suporte](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) do Epic Launcher.</span><span class="sxs-lookup"><span data-stu-id="2e088-115">If you're a first-time Unreal developer, you'll need to [download supporting files](./unreal-uxt-ch6.md#packaging-and-deploying-the-app-via-device-portal) from the Epic Launcher.</span></span>

1. <span data-ttu-id="2e088-116">Iniciar Unreal Engine</span><span class="sxs-lookup"><span data-stu-id="2e088-116">Launch Unreal Engine</span></span>

2. <span data-ttu-id="2e088-117">Selecione **Jogos** em **Novas Categorias de Projeto** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="2e088-117">Select **Games** in **New Project Categories** and click **Next**.</span></span> 

![Selecionar um modelo de projeto de jogos](images/unreal-uxt/2-gamestemplate.png)

3. <span data-ttu-id="2e088-119">Selecione o modelo **Em Branco** e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="2e088-119">Select the **Blank** Template and click **Next**.</span></span> 

![Selecionar o modelo Em Branco](images/unreal-uxt/2-template.PNG)

4. <span data-ttu-id="2e088-121">Defina **C++** , **3D ou 2D Escalonável, Celular/Tablet** e **Nenhum Conteúdo Inicial** como as **Configurações de Projeto** e escolha uma localização de salvamento e clique em **Criar Projeto**.</span><span class="sxs-lookup"><span data-stu-id="2e088-121">Set **C++**, **Scalable 3D or 2D, Mobile/Tablet**, and **No Starter Content** as your **Project Settings**, then choose a save location and click **Create Project**.</span></span> 

> [!NOTE]
> <span data-ttu-id="2e088-122">Você precisará selecionar um projeto C++ em vez de um projeto Blueprint para criar o plug-in das Ferramentas de UX, que você vai configurar mais adiante na seção 4.</span><span class="sxs-lookup"><span data-stu-id="2e088-122">You must select a C++ project rather than a Blueprint project in order to build the UX Tools plugin, which you'll be setting up later on in section 4.</span></span>

![Configurações iniciais do projeto](images/unreal-uxt/2-project-settings.PNG)

<span data-ttu-id="2e088-124">O projeto deve ser aberto automaticamente no editor Unreal, o que significa que você está pronto para a próxima seção.</span><span class="sxs-lookup"><span data-stu-id="2e088-124">The project should open up automatically in the Unreal editor, which means you're ready for the next section.</span></span>

## <a name="enabling-required-plugins"></a><span data-ttu-id="2e088-125">Como habilitar os plugins necessários</span><span class="sxs-lookup"><span data-stu-id="2e088-125">Enabling required plugins</span></span>

<span data-ttu-id="2e088-126">Habilite dois plug-ins para começar a adicionar objetos à cena.</span><span class="sxs-lookup"><span data-stu-id="2e088-126">You'll need to enable two plugins before you can start adding objects to the scene.</span></span>

1. <span data-ttu-id="2e088-127">Abra **Editar > Plug-ins** e selecione **Realidade Aumentada** na lista de opções internas.</span><span class="sxs-lookup"><span data-stu-id="2e088-127">Open **Edit > Plugins** and select **Augmented Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="2e088-128">Role para baixo até **HoloLens** e marque **Habilitado**.</span><span class="sxs-lookup"><span data-stu-id="2e088-128">Scroll down to **HoloLens** and check **Enabled**.</span></span> 

![Como habilitar plugins do HoloLens](images/unreal-uxt/2-plugins.PNG)

2. <span data-ttu-id="2e088-130">Selecione **Realidade Virtual** na lista de opções internas.</span><span class="sxs-lookup"><span data-stu-id="2e088-130">Select **Virtual Reality** from the built-in options list.</span></span> 
    * <span data-ttu-id="2e088-131">Role a página para baixo até **Microsoft Windows Mixed Reality**, marque a opção **Habilitado** e reinicie o editor.</span><span class="sxs-lookup"><span data-stu-id="2e088-131">Scroll down to **Microsoft Windows Mixed Reality**, check **Enabled**, and restart your editor.</span></span> 

![Como habilitar o plug-in do Windows Mixed Reality](images/unreal-uxt/2-virtual-reality-plugin.PNG)

> [!NOTE]
> <span data-ttu-id="2e088-133">Os dois plug-ins são necessários para o desenvolvimento no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="2e088-133">Both plugins are required for HoloLens 2 development.</span></span>

<span data-ttu-id="2e088-134">Com os plug-ins habilitados, seu nível vazio está pronto para a empresa.</span><span class="sxs-lookup"><span data-stu-id="2e088-134">With the plugins enabled, your empty level is ready for company.</span></span>

## <a name="creating-a-level"></a><span data-ttu-id="2e088-135">Criar um nível</span><span class="sxs-lookup"><span data-stu-id="2e088-135">Creating a level</span></span>
<span data-ttu-id="2e088-136">Sua próxima tarefa será criar uma configuração de jogador com um ponto de partida e um cubo para referência e escala.</span><span class="sxs-lookup"><span data-stu-id="2e088-136">Your next task is to create a player setup with a starting point and a cube for reference and scale.</span></span>

1. <span data-ttu-id="2e088-137">Selecione **Arquivo > Novo Nível** e escolha **Nível Vazio**.</span><span class="sxs-lookup"><span data-stu-id="2e088-137">Select **File > New Level** and choose **Empty Level**.</span></span> <span data-ttu-id="2e088-138">A cena padrão no visor agora deve estar vazia.</span><span class="sxs-lookup"><span data-stu-id="2e088-138">The default scene in the viewport should now be empty.</span></span>

2. <span data-ttu-id="2e088-139">Selecione **Básico** na guia **Modos** e arraste **PlayerStart** para a cena.</span><span class="sxs-lookup"><span data-stu-id="2e088-139">Select **Basic** from the **Modes** tab and drag **PlayerStart** into the scene.</span></span> 
    * <span data-ttu-id="2e088-140">Defina **Localização** como **X = 0**, **Y = 0** e **Z = 0** na guia **Detalhes** para definir o usuário no centro da cena quando o aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="2e088-140">Set **Location** to **X = 0**, **Y = 0**, and **Z = 0** in the **Details** tab to set the user at the center of the scene when the app starts up.</span></span>

![Visor com PlayerStart](images/unreal-uxt/2-playerstart.PNG)

3. <span data-ttu-id="2e088-142">Arraste um **Cubo** da guia **Básico** para a cena.</span><span class="sxs-lookup"><span data-stu-id="2e088-142">Drag a **Cube** from the **Basic** tab into the scene.</span></span> 
    * <span data-ttu-id="2e088-143">Defina **Localização** como **X = 50**, **Y = 0** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="2e088-143">Set **Location** to **X = 50**, **Y = 0**, and **Z = 0**.</span></span> <span data-ttu-id="2e088-144">para posicionar o cubo a 50 cm do jogador na hora de início.</span><span class="sxs-lookup"><span data-stu-id="2e088-144">to position the cube 50 cm away from the player at start time.</span></span> 
    * <span data-ttu-id="2e088-145">Altere **Escala** para **X = 0,2**, **Y = 0,2** e **Z = 0,2** para diminuir o cubo.</span><span class="sxs-lookup"><span data-stu-id="2e088-145">Change **Scale** to **X = 0.2**, **Y = 0.2**, and **Z = 0.2** to shrink the cube down.</span></span> 

<span data-ttu-id="2e088-146">Você não poderá ver o cubo, a menos que adicione uma luz à cena, que será a sua última tarefa antes de testar a cena em questão.</span><span class="sxs-lookup"><span data-stu-id="2e088-146">You can't see the cube unless you add a light to your scene, which is your last task before testing the scene.</span></span>

4. <span data-ttu-id="2e088-147">Alterne para a guia **Luzes** no painel **Modos** e arraste uma **Luz Direcional** até a cena.</span><span class="sxs-lookup"><span data-stu-id="2e088-147">Switch to the **Lights** tab in the **Modes** panel and drag a **Directional Light** into the scene.</span></span> <span data-ttu-id="2e088-148">Posicione a luz acima **PlayerStart** para que você possa vê-la.</span><span class="sxs-lookup"><span data-stu-id="2e088-148">Position the light above **PlayerStart** so you can see it.</span></span>

![Visor com luz adicionada](images/unreal-uxt/2-light.PNG)

5. <span data-ttu-id="2e088-150">Acesse **Arquivo > Salvar Atual**, nomeie o nível **Principal** e selecione **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2e088-150">Go to **File > Save Current**, name your level **Main**, and select **Save**.</span></span> 

<span data-ttu-id="2e088-151">Com a cena preparada, pressione **Jogar** na barra de ferramentas para ver o cubo em ação!</span><span class="sxs-lookup"><span data-stu-id="2e088-151">With the scene set, press **Play** in the toolbar to see your cube in action!</span></span> <span data-ttu-id="2e088-152">Quando tiver terminado de admirar seu trabalho, pressione **Esc** para interromper o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e088-152">When you're finished admiring your work, press **Esc** to stop the application.</span></span>

![Um cubo no visor](images/unreal-uxt/2-cube.PNG)

<span data-ttu-id="2e088-154">Agora que a cena está configurada, você pode começar a adicionar o tabuleiro de xadrez e a peça para completar o ambiente do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e088-154">Now that the scene is set up, you can start adding in the chess board and piece to round out the application environment.</span></span>

## <a name="importing-assets"></a><span data-ttu-id="2e088-155">Como importar ativos</span><span class="sxs-lookup"><span data-stu-id="2e088-155">Importing assets</span></span>
<span data-ttu-id="2e088-156">A cena está parecendo um tanto vazia no momento, mas você corrigirá isso importando os ativos prontos para o projeto.</span><span class="sxs-lookup"><span data-stu-id="2e088-156">The scene is looking a bit empty at the moment, but you'll fix that by importing the ready-made assets into the project.</span></span>

1. <span data-ttu-id="2e088-157">Baixe e descompacte a pasta de ativos do [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) usando o [7-zip](https://www.7-zip.org/).</span><span class="sxs-lookup"><span data-stu-id="2e088-157">Download and unzip the [GitHub](https://github.com/microsoft/MixedReality-Unreal-Samples/blob/master/ChessApp/ChessAssets.7z) assets folder using [7-zip](https://www.7-zip.org/).</span></span>

2. <span data-ttu-id="2e088-158">Selecione **Adicionar Novo > Nova Pasta** no **Navegador de Conteúdo** e nomeie-o **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="2e088-158">Select **Add New > New Folder** from the **Content Browser** and name it **ChessAssets**.</span></span> 
    * <span data-ttu-id="2e088-159">Clique duas vezes na nova pasta, em que você importará os ativos 3D.</span><span class="sxs-lookup"><span data-stu-id="2e088-159">Double-click the new folder where you'll import the 3D assets.</span></span>

![Mostrar ou ocultar o painel de fontes](images/unreal-uxt/2-showhidesources.PNG)

3. <span data-ttu-id="2e088-161">Selecione **Importar** no **Navegador de Conteúdo**, escolha todos os itens da pasta de ativos descompactados e clique em **Abrir**.</span><span class="sxs-lookup"><span data-stu-id="2e088-161">Select **Import** from the **Content Browser**, select all the items in the unzipped assets folder and click **Open**.</span></span> 
    * <span data-ttu-id="2e088-162">Os ativos incluem as malhas de objetos 3D para o tabuleiro de xadrez e as peças no formato FBX, bem como os mapas de textura no formato TGA que você usará para os materiais.</span><span class="sxs-lookup"><span data-stu-id="2e088-162">Assets include the 3D object meshes for the chess board and pieces in FBX format and texture maps in TGA format that you'll use to for materials.</span></span>  

4. <span data-ttu-id="2e088-163">Quando a janela Opções de Importação do FBX for exibida, expanda a seção **Material** e altere **Método de Importação de Material** para **Não Criar o Material**.</span><span class="sxs-lookup"><span data-stu-id="2e088-163">When the FBX Import Options window pops up, expand the **Material** section and change **Material Import Method** to **Do Not Create Material**.</span></span>
    * <span data-ttu-id="2e088-164">Selecione **Importar Tudo**.</span><span class="sxs-lookup"><span data-stu-id="2e088-164">Select **Import All**.</span></span>

![Opções em Importar FBX](images/unreal-uxt/2-nocreatemat.PNG)

<span data-ttu-id="2e088-166">Isso é tudo o que você precisa fazer com relação aos ativos.</span><span class="sxs-lookup"><span data-stu-id="2e088-166">That's all you need to do for the assets.</span></span> <span data-ttu-id="2e088-167">Seu próximo conjunto de tarefas é criar os blocos de construção do aplicativo com blueprints.</span><span class="sxs-lookup"><span data-stu-id="2e088-167">Your next set of tasks is to create the building blocks of the application with blueprints.</span></span>

## <a name="adding-blueprints"></a><span data-ttu-id="2e088-168">Como adicionar blueprints</span><span class="sxs-lookup"><span data-stu-id="2e088-168">Adding blueprints</span></span>

1. <span data-ttu-id="2e088-169">Selecione **Adicionar Novo > Nova Pasta** no **Navegador de Conteúdo** e nomeie-o **Blueprints**.</span><span class="sxs-lookup"><span data-stu-id="2e088-169">Select **Add New > New Folder** in the **Content Browser** and name it **Blueprints**.</span></span> 

> [!NOTE]
> <span data-ttu-id="2e088-170">Se você não está familiarizado com [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), saiba que eles são ativos especiais que fornecem uma interface baseada em nó para criação de tipos de Atores e eventos de nível de script.</span><span class="sxs-lookup"><span data-stu-id="2e088-170">If you're new to [blueprints](https://docs.unrealengine.com/en-US/Engine/Blueprints/index.html), they're special assets that provide a node-based interface for creating new types of Actors and script level events.</span></span> 

2. <span data-ttu-id="2e088-171">Clique duas vezes na pasta **Blueprints**, depois clique com o botão direito do mouse e selecione **Classe de Blueprint**.</span><span class="sxs-lookup"><span data-stu-id="2e088-171">Double-click into the **Blueprints** folder, then right-click and select **Blueprint Class**.</span></span>         
    * <span data-ttu-id="2e088-172">Selecione **Ator** e nomeie o novo blueprint como **Tabuleiro**.</span><span class="sxs-lookup"><span data-stu-id="2e088-172">Select **Actor** and name the blueprint **Board**.</span></span> 

![Selecione uma classe pai para seu Blueprint](images/unreal-uxt/2-bpparent.PNG)

<span data-ttu-id="2e088-174">O novo blueprint **Tabuleiro** agora aparece na pasta **Blueprints**, conforme mostrado na captura de tela a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e088-174">The new **Board** blueprint now shows up in the **Blueprints** folder as seen in the following screenshot.</span></span> 

![O novo Blueprint Board](images/unreal-uxt/2-bpboard.PNG)

<span data-ttu-id="2e088-176">Você está pronto para começar a adicionar materiais aos objetos criados.</span><span class="sxs-lookup"><span data-stu-id="2e088-176">You're all set to start adding materials to the created objects.</span></span>

## <a name="working-with-materials"></a><span data-ttu-id="2e088-177">Como trabalhar com materiais</span><span class="sxs-lookup"><span data-stu-id="2e088-177">Working with materials</span></span>
<span data-ttu-id="2e088-178">Os objetos que você criou são no padrão cinza, o que não os deixa com uma aparência muito divertida.</span><span class="sxs-lookup"><span data-stu-id="2e088-178">The objects you've created are default grey, which isn't much fun to look at.</span></span> <span data-ttu-id="2e088-179">Adicionar materiais e malhas a seus objetos é o último conjunto de tarefas neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="2e088-179">Adding materials and meshes to your objects is the last set of tasks in this tutorial.</span></span>

1. <span data-ttu-id="2e088-180">Clique duas vezes em **Painel** para abrir o editor de blueprints.</span><span class="sxs-lookup"><span data-stu-id="2e088-180">Double-click **Board** to open the blueprint editor.</span></span> 

2. <span data-ttu-id="2e088-181">Selecione **Adicionar Componente > Cena** no painel **Componentes** e nomeie-o **Root**.</span><span class="sxs-lookup"><span data-stu-id="2e088-181">Select **Add Component > Scene** from the **Components** panel and name it **Root**.</span></span> <span data-ttu-id="2e088-182">Observe que **Root** aparece como um filho de **DefaultSceneRoot** na captura de tela abaixo:</span><span class="sxs-lookup"><span data-stu-id="2e088-182">Notice that **Root** shows up as a child of **DefaultSceneRoot** in the screenshot below:</span></span>

![Como substituir a raiz no blueprint](images/unreal-uxt/2-root-blueprint.PNG)


3. <span data-ttu-id="2e088-184">Clique e arraste **Root** para **DefaultSceneRoot** para substituí-lo e livrar-se da esfera no visor.</span><span class="sxs-lookup"><span data-stu-id="2e088-184">Click-and-drag **Root** onto **DefaultSceneRoot** to replace it and get rid of the sphere in the viewport.</span></span> 

![Substituindo a raiz](images/unreal-uxt/2-root.PNG)


4. <span data-ttu-id="2e088-186">Selecione **Adicionar Componente > Malha Estática** no painel **Componentes** e nomeie-o **SM_Board**.</span><span class="sxs-lookup"><span data-stu-id="2e088-186">Select **Add Component > Static Mesh** from the **Components** panel and name it **SM_Board**.</span></span> <span data-ttu-id="2e088-187">Ele será exibido como um objeto filho em **Root**.</span><span class="sxs-lookup"><span data-stu-id="2e088-187">It will appear as a child object under **Root**.</span></span>

![Adicionando uma malha estática](images/unreal-uxt/2-sm-board.PNG)

4. <span data-ttu-id="2e088-189">Selecione **SM_Board**, role o painel para baixo até a seção **Malha Estática** do painel **Detalhes** e selecione **ChessBoard** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="2e088-189">Select **SM_Board**, scroll down to the **Static Mesh** section of the **Details** panel, and select **ChessBoard** from the dropdown.</span></span> 

![A malha do tabuleiro no visor](images/unreal-uxt/2-sm-board-view.PNG)

5.  <span data-ttu-id="2e088-191">Ainda no painel **Detalhes**, expanda a seção **Materiais** e selecione **Criar Ativo > Material** na lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="2e088-191">Still in the **Details** panel, expand the **Materials** section and select **Create New Asset > Material** from the dropdown.</span></span> 
    * <span data-ttu-id="2e088-192">Nomeie o material **M_ChessBoard** e salve-o na pasta **ChessAssets**.</span><span class="sxs-lookup"><span data-stu-id="2e088-192">Name the material **M_ChessBoard** and save it to the **ChessAssets** folder.</span></span> 

![Criar um material](images/unreal-uxt/2-newmat.PNG)

6.  <span data-ttu-id="2e088-194">Clique duas vezes na imagem do material **M_ChessBoard** para abrir o editor de material.</span><span class="sxs-lookup"><span data-stu-id="2e088-194">Double-click the **M_ChessBoard** material imaged to open the Material Editor.</span></span> 

![Abrir editor de material](images/unreal-uxt/2-material-editor.PNG)

7. <span data-ttu-id="2e088-196">No Editor de Material, clique com o botão direito do mouse e procure **Exemplo de Textura**.</span><span class="sxs-lookup"><span data-stu-id="2e088-196">In the Material Editor, right-click and search for **Texture Sample**.</span></span> 
    * <span data-ttu-id="2e088-197">Expanda a seção **Base de Textura de Expressão do Material** no painel **Detalhes** e defina **Textura** para **ChessBoard_Albedo**.</span><span class="sxs-lookup"><span data-stu-id="2e088-197">Expand the **Material Expression Texture Base** section in the **Details** panel and set **Texture** to **ChessBoard_Albedo**.</span></span> 
    * <span data-ttu-id="2e088-198">Arraste o marcador de saída **RGB** para o marcador de Cor Base de **M_ChessBoard**.</span><span class="sxs-lookup"><span data-stu-id="2e088-198">Drag the **RGB** output pin to the Base Color pin of **M_ChessBoard**.</span></span> 

![Definir a cor base](images/unreal-uxt/2-boardalbedomat.PNG)

8.  <span data-ttu-id="2e088-200">Repita a etapa anterior mais quatro vezes para criar mais quatro nós **Exemplo de Textura** com as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="2e088-200">Repeat the previous step 4 more times to create four more **Texture Sample** nodes with the following settings:</span></span>
    * <span data-ttu-id="2e088-201">Defina **Textura** como **ChessBoard_AO** e vincule o **RGB** ao marcador **Oclusão Ambiente**.</span><span class="sxs-lookup"><span data-stu-id="2e088-201">Set **Texture** to **ChessBoard_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="2e088-202">Defina **Textura** como **ChessBoard_Metal** e vincule o **RGB** ao marcador **Metálico**.</span><span class="sxs-lookup"><span data-stu-id="2e088-202">Set **Texture** to **ChessBoard_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="2e088-203">Defina **Textura** como **ChessBoard_Normal** e vincule o **RGB** ao marcador **Normal**.</span><span class="sxs-lookup"><span data-stu-id="2e088-203">Set **Texture** to **ChessBoard_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="2e088-204">Defina **Textura** como **ChessBoard_Rough** e vincule o **RGB** ao marcador **Aspereza**.</span><span class="sxs-lookup"><span data-stu-id="2e088-204">Set **Texture** to **ChessBoard_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="2e088-205">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2e088-205">Click **Save**.</span></span> 

![Conectar as texturas restantes](images/unreal-uxt/2-boardmat.PNG)

<span data-ttu-id="2e088-207">Verifique se a configuração do material está parecida com a captura de tela acima antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2e088-207">Make sure your material setup looks like the above screenshot before continuing.</span></span>

## <a name="populating-the-scene"></a><span data-ttu-id="2e088-208">Como popular a cena</span><span class="sxs-lookup"><span data-stu-id="2e088-208">Populating the scene</span></span>
<span data-ttu-id="2e088-209">Se você retornar ao blueprint **Tabuleiro**, verá que o material que acabou de criar foi aplicado.</span><span class="sxs-lookup"><span data-stu-id="2e088-209">If you go back to the **Board** blueprint, you'll see that the material you just created has been applied.</span></span> <span data-ttu-id="2e088-210">Tudo o que falta fazer é configurar a cena!</span><span class="sxs-lookup"><span data-stu-id="2e088-210">All that's left is setting up the scene!</span></span> <span data-ttu-id="2e088-211">Primeiro, altere as propriedades a seguir para assegurar que o tabuleiro seja de um tamanho razoável e esteja inclinado corretamente quando posicionado na cena:</span><span class="sxs-lookup"><span data-stu-id="2e088-211">First, change the following properties to make sure the board is a reasonable size and angled correctly when it's placed in the scene:</span></span>
1.  <span data-ttu-id="2e088-212">Defina **Escala** como **(0,05, 0,05, 0,05)** e **Rotação Z** como **90**.</span><span class="sxs-lookup"><span data-stu-id="2e088-212">Set **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span> 
    * <span data-ttu-id="2e088-213">Clique em **Compilar** na barra de ferramentas superior e depois em **Salvar**, então volte para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="2e088-213">Click **Compile** in the top toolbar, then **Save** and return to the Main window.</span></span> 

![Tabuleiro de xadrez com material aplicado](images/unreal-uxt/2-chessboard.PNG)

2.  <span data-ttu-id="2e088-215">Clique com o botão direito do mouse em **Cubo > Editar > Excluir** e arraste **Tabuleiro** do **Navegador de Conteúdo** para o visor.</span><span class="sxs-lookup"><span data-stu-id="2e088-215">Right-click **Cube > Edit > Delete** and drag **Board** from the **Content Browser** into the viewport.</span></span> 
    * <span data-ttu-id="2e088-216">Defina **Localização** como **X = 80**, **Y = 0** e **Z = -20**.</span><span class="sxs-lookup"><span data-stu-id="2e088-216">Set **Location** to **X = 80**, **Y = 0**, and **Z = -20**.</span></span> 

3.  <span data-ttu-id="2e088-217">Selecione o botão **Jogar** para ver o novo tabuleiro no nível.</span><span class="sxs-lookup"><span data-stu-id="2e088-217">Select the **Play** button to view your new board in the level.</span></span> <span data-ttu-id="2e088-218">Pressione **ESC** para retornar ao editor.</span><span class="sxs-lookup"><span data-stu-id="2e088-218">Press **Esc** to return to the editor.</span></span> 

<span data-ttu-id="2e088-219">Agora você seguirá as mesmas etapas para criar uma peça de xadrez, do mesmo modo que você fez com o tabuleiro:</span><span class="sxs-lookup"><span data-stu-id="2e088-219">Now you'll follow the same steps to create a chess piece as you did with the board:</span></span>

1. <span data-ttu-id="2e088-220">Acesse a pasta **Blueprints**, clique com o botão direito do mouse, selecione **Classe de Blueprint** e escolha **Ator**.</span><span class="sxs-lookup"><span data-stu-id="2e088-220">Go to the **Blueprints** folder, right-click, and select **Blueprint Class** and choose **Actor**.</span></span> <span data-ttu-id="2e088-221">Nomeie esse ator como **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="2e088-221">Name the actor **WhiteKing**.</span></span>

2. <span data-ttu-id="2e088-222">Clique duas vezes em **WhiteKing** para abri-lo no Editor do Blueprint, selecione **Adicionar Componente > Cena** e nomeie-o **Root**.</span><span class="sxs-lookup"><span data-stu-id="2e088-222">Double-click **WhiteKing** to open it in the Blueprint Editor, select **Add Component > Scene** and name it **Root**.</span></span> 
    * <span data-ttu-id="2e088-223">Arraste e solte **Root** em **DefaultSceneRoot** para substituí-lo.</span><span class="sxs-lookup"><span data-stu-id="2e088-223">Drag-and-drop **Root** onto **DefaultSceneRoot** to replace it.</span></span> 

3. <span data-ttu-id="2e088-224">Clique em **Adicionar Componente > Malha Estática** e nomeie-o como **SM_King**.</span><span class="sxs-lookup"><span data-stu-id="2e088-224">Click **Add Component > Static Mesh** and name it **SM_King**.</span></span> 
    * <span data-ttu-id="2e088-225">No painel Detalhes, defina **Malha Estática** como **Chess_King** e **Material** como um novo material chamado **M_ChessWhite**.</span><span class="sxs-lookup"><span data-stu-id="2e088-225">Set **Static Mesh** to **Chess_King** and **Material** to a new Material called **M_ChessWhite** in the Details panel.</span></span> 

4. <span data-ttu-id="2e088-226">Abra **M_ChessWhite** no Editor de material e conecte os nós de **Exemplo de Textura** a seguir ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="2e088-226">Open **M_ChessWhite** in the Material editor and hook up the following **Texture Sample** nodes to the following:</span></span>
   * <span data-ttu-id="2e088-227">Defina **Textura** como **ChessWhite_Albedo** e vincule o **RGB** ao marcador **Cor de Base**.</span><span class="sxs-lookup"><span data-stu-id="2e088-227">Set **Texture** to **ChessWhite_Albedo** and link the **RGB** to the **Base Color** pin.</span></span>
    * <span data-ttu-id="2e088-228">Defina **Textura** como **ChessWhite_AO** e vincule o **RGB** ao marcador **Oclusão Ambiente**.</span><span class="sxs-lookup"><span data-stu-id="2e088-228">Set **Texture** to **ChessWhite_AO** and link the **RGB** to the **Ambient Occlusion** pin.</span></span>
    * <span data-ttu-id="2e088-229">Defina **Textura** como **ChessWhite_Metal** e vincule o **RGB** ao marcador **Metálico**.</span><span class="sxs-lookup"><span data-stu-id="2e088-229">Set **Texture** to **ChessWhite_Metal** and link the **RGB** to the **Metallic** pin.</span></span> 
    * <span data-ttu-id="2e088-230">Defina **Textura** como **ChessWhite_Normal** e vincule o **RGB** ao marcador **Normal**.</span><span class="sxs-lookup"><span data-stu-id="2e088-230">Set **Texture** to **ChessWhite_Normal** and link the **RGB** to the **Normal** pin.</span></span>
    * <span data-ttu-id="2e088-231">Defina **Textura** como **ChessWhite_Rough** e vincule o **RGB** ao marcador **Aspereza**.</span><span class="sxs-lookup"><span data-stu-id="2e088-231">Set **Texture** to **ChessWhite_Rough** and link the **RGB** to the **Roughness** pin.</span></span> 
    * <span data-ttu-id="2e088-232">Clique em **Salvar**.</span><span class="sxs-lookup"><span data-stu-id="2e088-232">Click **Save**.</span></span> 

<span data-ttu-id="2e088-233">Verifique se o material **M_ChessKing** tem aparência semelhante à da imagem a seguir antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2e088-233">Your **M_ChessKing** material should look like the following image before continuing.</span></span>

![Criar o material para o rei do xadrez](images/unreal-uxt/2-chesskingmat.PNG)

<span data-ttu-id="2e088-235">Você está quase lá, falta apenas adicionar a nova peça de xadrez à cena:</span><span class="sxs-lookup"><span data-stu-id="2e088-235">You're almost there, just need to add the new chess piece into the scene:</span></span> 

1. <span data-ttu-id="2e088-236">Abra o blueprint **WhiteKing**, altere a **Escala** para **(0,05; 0,05; 0,05)** e a **Rotação em Z** para **90**.</span><span class="sxs-lookup"><span data-stu-id="2e088-236">Open the **WhiteKing** blueprint and change the **Scale** to **(0.05, 0.05, 0.05)** and **Z Rotation** to **90**.</span></span>
    * <span data-ttu-id="2e088-237">Compile e salve o blueprint e, em seguida, retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="2e088-237">Compile and save your blueprint, then head back to the main window.</span></span> 

2.  <span data-ttu-id="2e088-238">Arraste **WhiteKing** para o visor, alterne para o painel **Esboço do Mundo** e arraste **WhiteKing** para o **Tabuleiro** para torná-lo um objeto filho.</span><span class="sxs-lookup"><span data-stu-id="2e088-238">Drag **WhiteKing** into the viewport, switch to the **World Outliner** panel drag **WhiteKing** onto **Board** to make it a child object.</span></span>

![Contorno do Mundo](images/unreal-uxt/2-child.PNG)

3.  <span data-ttu-id="2e088-240">No painel **Detalhes**, em **Transformar**, defina a **Localização** de **WhiteKing** como **X = -26**, **Y = 4** e **Z = 0**.</span><span class="sxs-lookup"><span data-stu-id="2e088-240">In the **Details** panel under **Transform**, set **WhiteKing**'s **Location** to **X = -26**, **Y = 4**, and **Z = 0**.</span></span>

<span data-ttu-id="2e088-241">Tudo concluído!</span><span class="sxs-lookup"><span data-stu-id="2e088-241">That's a wrap!</span></span> <span data-ttu-id="2e088-242">Selecione **Jogar** para ver o nível preenchido em ação e clique em **ESC** quando estiver pronto para sair.</span><span class="sxs-lookup"><span data-stu-id="2e088-242">Select **Play** to see your populated level in action, and press **Esc** when you're ready to exit.</span></span> <span data-ttu-id="2e088-243">Você viu muito conteúdo apenas criando um projeto simples, mas agora está pronto para passar para a próxima parte da série: configuração para a realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="2e088-243">You covered a lot of ground just creating a simple project, but now you're ready to move on to the next part of the series: setting up for mixed reality.</span></span> 

[<span data-ttu-id="2e088-244">Próxima seção: 3. Configurar seu projeto para a realidade misturada</span><span class="sxs-lookup"><span data-stu-id="2e088-244">Next Section: 3. Set up your project for mixed reality</span></span>](unreal-uxt-ch3.md)