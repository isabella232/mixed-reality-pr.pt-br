---
ms.openlocfilehash: be4a3243bc00f29f992957de0dfa29416c13284d
ms.sourcegitcommit: bdf4babd13e021f41fb04cdb3611bb759bd77537
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112392489"
---
# <a name="unity-2020--openxr"></a>[<span data-ttu-id="8bf50-101">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="8bf50-101">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-switching-build-platform"></a><span data-ttu-id="8bf50-102">1. Como alternar a plataforma de build</span><span class="sxs-lookup"><span data-stu-id="8bf50-102">1. Switching Build Platform</span></span>

<span data-ttu-id="8bf50-103">No menu do Unity, selecione Arquivo > Configurações de Build para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="8bf50-103">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="8bf50-104">Na janela Configurações de build, selecione plataforma **Autônoma de PC, Mac e Linux** e clique em **Alternar plataforma** para alterar a Plataforma de build:</span><span class="sxs-lookup"><span data-stu-id="8bf50-104">In the Build Settings window, select **PC, Mac & Linux Standalone** Platform and click the **Switch Platform** button to change the Build Platform:</span></span>

![Como alternar a plataforma de build](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-1.PNG)

<span data-ttu-id="8bf50-106">Quando o Unity concluir a troca da plataforma, clique no ícone x para fechar a janela Configurações de build.</span><span class="sxs-lookup"><span data-stu-id="8bf50-106">When Unity has finished switching the platform, click the x icon to close the Build Settings window.</span></span>

### <a name="2-set-the-project-settings"></a><span data-ttu-id="8bf50-107">2. Definir as configurações do projeto</span><span class="sxs-lookup"><span data-stu-id="8bf50-107">2. Set the project settings</span></span>

<span data-ttu-id="8bf50-108">No menu do Unity, selecione **Editar** > **Configurações de projeto** > **Gerenciamento do plug-in XR**, confira se você está na guia Autônomo do Windows e marque a caixa de seleção **OpenXR** e **conjunto de recursos do Windows Mixed Reality**.</span><span class="sxs-lookup"><span data-stu-id="8bf50-108">In the Unity menu, select **Edit** > **Project Settings** > **XR Plug-in Management** ensure that you are in Windows Standalone tab and check the **OpenXR** and **Windows Mixed Reality feature set** checkbox.</span></span>

![Habilitar o OpenXR e o conjunto de recursos do Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-2.PNG)

<span data-ttu-id="8bf50-110">Na janela Configurações de projeto, selecione **OpenXR**, confira se você está na guia Autônomo do Windows e altere o **modo de envio de Profundidade** de Nenhum para **Profundidade 16 bits**.</span><span class="sxs-lookup"><span data-stu-id="8bf50-110">In Project Settings window, select **OpenXR** and ensure that you are in Windows Standalone tab and change the **Depth submission mode** from None to **Depth 16 Bit**.</span></span>

<span data-ttu-id="8bf50-111">Na guia Perfis de interação, clique no símbolo + e adicione **Perfil de interação do olhar** e **Perfil de interação com a mão da Microsoft**.</span><span class="sxs-lookup"><span data-stu-id="8bf50-111">In interaction profiles tab add **Eye Gaze Interaction Profile** and **Microsoft Hand Interaction Profile** by clicking on the + symbol.</span></span>

![Adicionar Perfil de interação do olhar e Perfil de interação com a mão da Microsoft](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-3.PNG)

<span data-ttu-id="8bf50-113">Em **Grupos de recursos do Open XR** > **Todos os recursos** > marque a caixa de seleção **Comunicação Remota de aplicativo holográfico**.</span><span class="sxs-lookup"><span data-stu-id="8bf50-113">Under **Open XR feature groups** > **All features** > check the **Holographic App Remoting** checkbox.</span></span>

![Habilitar a Comunicação Remota de aplicativo holográfico](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-4.PNG)

<span data-ttu-id="8bf50-115">Em seguida, marque a caixa de seleção **Windows Mixed Reality** e, no grupo do Windows Mixed Reality, selecione **Comunicação Remota de aplicativo holográfico**.</span><span class="sxs-lookup"><span data-stu-id="8bf50-115">next select the **Windows Mixed Reality**  check box and under Windows Mixed Reality group select the  **Holographic App Remoting** checkbox.</span></span>

![Habilitar a Comunicação Remota de aplicativo holográfico do Windows Mixed Reality](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-5.PNG)

### <a name="3-build-the-unity-project"></a><span data-ttu-id="8bf50-117">3. Criar o projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="8bf50-117">3. Build the Unity Project</span></span>

<span data-ttu-id="8bf50-118">No menu do Unity, selecione Arquivo > Configurações de Build para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="8bf50-118">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="8bf50-119">Na janela Configurações de Build, clique no botão \***Adicionar Cenas Abertas** _ para adicionar a cena atual às Cenas.</span><span class="sxs-lookup"><span data-stu-id="8bf50-119">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="8bf50-120">Na lista do Build, clique em _ \*Build\*\*:</span><span class="sxs-lookup"><span data-stu-id="8bf50-120">In the Build list, then click the _ *Build*\* button:</span></span>

![Janela Configurações de Build do Unity com a cena adicionada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-6.PNG)

<span data-ttu-id="8bf50-122">Escolha um local adequado para armazenar seu projeto, por exemplo, Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="8bf50-122">choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="8bf50-123">Crie uma pasta e dê a ela um nome adequado, por exemplo, PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="8bf50-123">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="8bf50-124">Em seguida, clique no botão ***Selecionar Pasta*** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="8bf50-124">Then click the ***Select Folder*** button to start the build process:</span></span>

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-7.png)

<span data-ttu-id="8bf50-126">Aguarde até que o Unity conclua o processo de build.</span><span class="sxs-lookup"><span data-stu-id="8bf50-126">Wait for Unity to finish the build process.</span></span>

![Processo de build do Unity em andamento](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step4-8.png)

<span data-ttu-id="8bf50-128">Clique duas vezes no arquivo executável para abrir o Aplicativo Holográfico de Comunicação Remota para PC em seu computador.</span><span class="sxs-lookup"><span data-stu-id="8bf50-128">double click on the Executable file to open the PC Holographic Remoting Application in your PC.</span></span>

> [!NOTE]
> <span data-ttu-id="8bf50-129">Devido a alguns problemas conhecidos no aplicativo Holográfico de Comunicação Remota para PC criado como UWP, estamos construindo o aplicativo para PC como Autônomo do Windows para OpenXR.</span><span class="sxs-lookup"><span data-stu-id="8bf50-129">Due to some known issues in Holographic Remoting for PC app Built as UWP we are Building the PC App as Windows Standalone for OpenXR.</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="8bf50-130">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="8bf50-130">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-set-the-player-settings"></a><span data-ttu-id="8bf50-131">1. Definir as configurações do player</span><span class="sxs-lookup"><span data-stu-id="8bf50-131">1. Set the player settings</span></span>

<span data-ttu-id="8bf50-132">Na seção **Configurações de XR**, marque a caixa de seleção **Comunicação Remota Holográfica do WSA com Suporte** e habilite a Comunicação Remota Holográfica.</span><span class="sxs-lookup"><span data-stu-id="8bf50-132">In the **XR Settings** section, select the **WSA Holographic Remoting Supported** checkbox and enable the Holographic Remoting.</span></span>

![Janela Configurações de XR do Unity com a caixa Comunicação Remota Holográfica do WSA com Suporte habilitada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step1-1.png)

### <a name="2-build-the-unity-project"></a><span data-ttu-id="8bf50-134">2. Criar o Projeto do Unity</span><span class="sxs-lookup"><span data-stu-id="8bf50-134">2. Build the Unity Project</span></span>

<span data-ttu-id="8bf50-135">No menu do Unity, selecione Arquivo > Configurações de Build para abrir a janela Configurações de Build.</span><span class="sxs-lookup"><span data-stu-id="8bf50-135">In the Unity menu, select File > Build Settings to open the Build Settings window.</span></span>

<span data-ttu-id="8bf50-136">Na janela Configurações de Build, clique no botão \***Adicionar Cenas Abertas** _ para adicionar a cena atual às Cenas.</span><span class="sxs-lookup"><span data-stu-id="8bf50-136">In the Build Settings window, click the \***Add Open Scenes** _ button to add your current scene to the Scenes.</span></span> <span data-ttu-id="8bf50-137">Na lista Build, clique no _ *_botão Build_*\* para abrir a janela Criar Plataforma Universal do Windows:</span><span class="sxs-lookup"><span data-stu-id="8bf50-137">In the Build list, then click the _ *_Build button_*\* to open the Build Universal Windows Platform window:</span></span>

![Janela Configurações de Build do Unity com a cena adicionada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-1.png)

<span data-ttu-id="8bf50-139">Na janela Criar Plataforma Universal do Windows, escolha uma localização adequada para armazenar o seu build, por exemplo, Documents\MixedRealityLearning.</span><span class="sxs-lookup"><span data-stu-id="8bf50-139">In the Build Universal Windows Platform window, choose a suitable location to store your build, for example, Documents\MixedRealityLearning.</span></span> <span data-ttu-id="8bf50-140">Crie uma pasta e dê a ela um nome adequado, por exemplo, PCHolographicRemoting.</span><span class="sxs-lookup"><span data-stu-id="8bf50-140">Create a new folder and give it a suitable name, for example, PCHolographicRemoting.</span></span> <span data-ttu-id="8bf50-141">Em seguida, clique no botão ***Selecionar Pasta*** para iniciar o processo de build:</span><span class="sxs-lookup"><span data-stu-id="8bf50-141">Then click the ***Select Folder*** button to start the build process:</span></span>

![Janela Configurações de Build do Unity com a janela de prompt Selecionar Pasta](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-2.png)

<span data-ttu-id="8bf50-143">Aguarde até que o Unity conclua o processo de build.</span><span class="sxs-lookup"><span data-stu-id="8bf50-143">Wait for Unity to finish the build process.</span></span>

![Processo de build do Unity em andamento](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step2-3.png)

### <a name="3-build-and-deploy-the-application"></a><span data-ttu-id="8bf50-145">3. Compilar e implantar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="8bf50-145">3. Build and deploy the application</span></span>

<span data-ttu-id="8bf50-146">Quando o processo de build for concluído, o Unity solicitará que o Explorador de Arquivos do Windows abra o local em que você armazenou o build.</span><span class="sxs-lookup"><span data-stu-id="8bf50-146">When the build process is completed, Unity will prompt Windows File Explorer to open the location you stored the build.</span></span> <span data-ttu-id="8bf50-147">Navegue dentro da pasta e clique duas vezes no arquivo .sln para abri-lo no Visual Studio:</span><span class="sxs-lookup"><span data-stu-id="8bf50-147">Navigate inside the folder, and double-click the .sln file to open it in Visual Studio:</span></span>

![Windows Explorer com a solução do Visual Studio recém-criada selecionada](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-1.png)

> [!NOTE]
> <span data-ttu-id="8bf50-149">Se o Visual Studio solicitar a instalação de novos componentes, reserve um momento para assegurar que todos os componentes necessários estejam instalados conforme especificado na documentação Instalar as Ferramentas.</span><span class="sxs-lookup"><span data-stu-id="8bf50-149">If Visual Studio asks you to install new components, take a moment to ensure that all prerequisite components are installed as specified in the Install the Tools documentation.</span></span>

<span data-ttu-id="8bf50-150">Configure o Visual Studio para PC selecionando a configuração da Versão, a arquitetura x64 e o Computador Local como um destino:</span><span class="sxs-lookup"><span data-stu-id="8bf50-150">Configure Visual Studio for PC by selecting the Release configuration, the x64 architecture, and Local Machine as target:</span></span>

![Visual Studio configurado para Computador Local](../images/mrlearning-pc-holographic-remoting/Tutorial2-Section2-Step3-2.png)

<span data-ttu-id="8bf50-152">Clique no botão ***Computador Local***.</span><span class="sxs-lookup"><span data-stu-id="8bf50-152">Click the button that says ***Local Machine***.</span></span> <span data-ttu-id="8bf50-153">Ele começa a criar e implantar o aplicativo no seu PC.</span><span class="sxs-lookup"><span data-stu-id="8bf50-153">It starts to build and deploy the application on to your PC.</span></span> <span data-ttu-id="8bf50-154">O aplicativo será instalado no seu PC por padrão.</span><span class="sxs-lookup"><span data-stu-id="8bf50-154">The application will be installed in your PC by default.</span></span>
