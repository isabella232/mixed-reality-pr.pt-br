---
title: 4. Como tornar sua cena interativa
description: Parte 4 de 6 de uma série de tutoriais para criação de um aplicativo de xadrez usando o Unreal Engine 4 e o plug-in Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada
author: hferrone
ms.author: v-hferrone
ms.date: 11/18/2020
ms.topic: article
ms.localizationpriority: high
keywords: Unreal, Unreal Engine 4, UE4, HoloLens, HoloLens 2, realidade misturada, tutorial, introdução, mrtk, uxt, Ferramentas de UX, documentação, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual
ms.openlocfilehash: c26f5579aad29624c9a8f374caa4799423d0637e
ms.sourcegitcommit: 04927427226928bd9178da0049d4cef626a6b0bf
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/21/2021
ms.locfileid: "98635438"
---
# <a name="4-making-your-scene-interactive"></a><span data-ttu-id="39575-104">4. Como tornar sua cena interativa</span><span class="sxs-lookup"><span data-stu-id="39575-104">4. Making your scene interactive</span></span>

<span data-ttu-id="39575-105">No tutorial anterior, você adicionou um ARSession, um Peão e um Modo de Jogo para concluir a configuração de realidade misturada para o aplicativo de xadrez.</span><span class="sxs-lookup"><span data-stu-id="39575-105">In the previous tutorial, you added an ARSession, Pawn, and Game Mode to complete the mixed reality setup for the chess app.</span></span> <span data-ttu-id="39575-106">Esta seção concentra-se no plug-in de software livre [Ferramentas de UX do Kit de Ferramentas de Realidade Misturada](https://github.com/microsoft/MixedReality-UXTools-Unreal), que oferece ferramentas para tornar sua cena interativa.</span><span class="sxs-lookup"><span data-stu-id="39575-106">This section focuses on using the open source [Mixed Reality Toolkit UX Tools](https://github.com/microsoft/MixedReality-UXTools-Unreal) plugin, which provides tools to make the scene interactive.</span></span> <span data-ttu-id="39575-107">Ao final desta seção, as peças de xadrez serão movidas pela entrada do usuário.</span><span class="sxs-lookup"><span data-stu-id="39575-107">By the end of this section, your chess pieces will be moving by user input.</span></span>

## <a name="objectives"></a><span data-ttu-id="39575-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="39575-108">Objectives</span></span>

* <span data-ttu-id="39575-109">Instalar o plug-in de Ferramentas de Experiência de Usuário de Realidade Misturada do GitHub</span><span class="sxs-lookup"><span data-stu-id="39575-109">Installing the Mixed Reality UX Tools plugin from GitHub</span></span>
* <span data-ttu-id="39575-110">Como adicionar Atores de Interação à Mão às pontas dos seus dedos</span><span class="sxs-lookup"><span data-stu-id="39575-110">Adding Hand Interaction Actors to your fingertips</span></span>
* <span data-ttu-id="39575-111">Como criar e adicionar manipuladores a objetos na cena</span><span class="sxs-lookup"><span data-stu-id="39575-111">Creating and adding Manipulators to objects in the scene</span></span>
* <span data-ttu-id="39575-112">Como usar simulação de entrada para validar o projeto</span><span class="sxs-lookup"><span data-stu-id="39575-112">Using input simulation to validate the project</span></span>

## <a name="downloading-the-mixed-reality-ux-tools-plugin"></a><span data-ttu-id="39575-113">Baixar o plug-in das Ferramentas de Experiência de Usuário do Kit de Ferramentas de Realidade Misturada</span><span class="sxs-lookup"><span data-stu-id="39575-113">Downloading the Mixed Reality UX Tools plugin</span></span>
<span data-ttu-id="39575-114">Antes de começar a trabalhar com a entrada do usuário, você precisará adicionar o plug-in ao projeto.</span><span class="sxs-lookup"><span data-stu-id="39575-114">Before you start working with user input, you'll need to add the plugin to the project.</span></span>

1. <span data-ttu-id="39575-115">Na [página de versões](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) das Ferramentas de Experiência de Usuário de Realidade Misturada no GitHub, navegue até a versão v0.10.0 das Ferramentas de Experiência de Usuário para Unreal e baixe o **UXTools.0.10.0.zip**.</span><span class="sxs-lookup"><span data-stu-id="39575-115">On the Mixed Reality UX Tools [releases page](https://github.com/microsoft/MixedReality-UXTools-Unreal/releases) on GitHub, navigate to the UX Tools for Unreal v0.10.0 release and download **UXTools.0.10.0.zip**.</span></span> <span data-ttu-id="39575-116">Descompacte o arquivo.</span><span class="sxs-lookup"><span data-stu-id="39575-116">Unzip the file.</span></span>

2.  <span data-ttu-id="39575-117">Na pasta raiz do projeto, crie uma pasta chamada **Plugins**.</span><span class="sxs-lookup"><span data-stu-id="39575-117">Create a new folder called **Plugins** in the root folder of the project.</span></span> <span data-ttu-id="39575-118">Copie o plug-in UXTools descompactado para essa pasta e reinicie o editor Unreal.</span><span class="sxs-lookup"><span data-stu-id="39575-118">Copy the unzipped UXTools plugin into this folder and restart the Unreal editor.</span></span>

![Criar uma pasta de plug-ins do projeto](images/unreal-uxt/4-plugins.PNG)

3.  <span data-ttu-id="39575-120">O plug-in de UXTools fornece uma pasta Conteúdo com subpastas para componentes, incluindo **Botões**, **Simulação de Entrada** e **Ponteiros**, bem como uma pasta Classes C++ com um código adicional.</span><span class="sxs-lookup"><span data-stu-id="39575-120">The UXTools plugin has a Content folder with subfolders for components, including **Buttons**, **Input Simulation**, and **Pointers**, and a C++ Classes folder with additional code.</span></span>  

> [!NOTE]
> <span data-ttu-id="39575-121">Se você não vir a seção **Conteúdo do UXTools** no **Navegador de Conteúdo**, clique em **Exibir Opções > Mostrar Conteúdo do Plug-in**.</span><span class="sxs-lookup"><span data-stu-id="39575-121">If you don’t see the **UXTools Content** section in the **Content Browser**, click **View Options > Show Plugin Content**.</span></span>

![Mostrar conteúdo do plug-in](images/unreal-uxt/4-showplugincontent.PNG)

<span data-ttu-id="39575-123">Encontre a documentação adicional do plug-in no [repositório](https://aka.ms/uxt-unreal) GitHub das Ferramentas de Experiência de Usuário de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="39575-123">Additional plugin documentation can be found on the Mixed Reality UX Tools GitHub [repository](https://aka.ms/uxt-unreal).</span></span>

<span data-ttu-id="39575-124">Com o plug-in instalado, você está pronto para começar a usar as ferramentas que ele tem a oferecer, começando com os atores de interação à mão.</span><span class="sxs-lookup"><span data-stu-id="39575-124">With the plugin installed, you're ready to start using the tools it has to offer, starting with hand interaction actors.</span></span>

## <a name="spawning-hand-interaction-actors"></a><span data-ttu-id="39575-125">Como gerar Atores de Interação à Mão</span><span class="sxs-lookup"><span data-stu-id="39575-125">Spawning Hand Interaction Actors</span></span>

<span data-ttu-id="39575-126">A interação da mão com elementos de Experiência de Usuário é feita com Atores de Interação da Mão, que criam e orientam os ponteiros e os visuais para interações próximas e distantes.</span><span class="sxs-lookup"><span data-stu-id="39575-126">Hand interaction with UX elements is done with Hand Interaction Actors, which create and drive the pointers and visuals for near and far interactions.</span></span>
- <span data-ttu-id="39575-127">*Interações próximas*: pinçar os elementos entre o dedo indicador e o polegar ou cutucá-los com a ponta do dedo.</span><span class="sxs-lookup"><span data-stu-id="39575-127">*Near interactions* - pinching elements between index finger and thumb or by poking them with a fingertip.</span></span>
- <span data-ttu-id="39575-128">*Interações distantes*: apontar um raio da mão virtual para um elemento e pressionar o indicador e o polegar juntos.</span><span class="sxs-lookup"><span data-stu-id="39575-128">*Far interactions* - pointing a ray from the virtual hand at an element and pressing index and thumb together.</span></span>

<span data-ttu-id="39575-129">Em nosso caso, adicionar um Ator de Interação Manual a **MRPawn** vai:</span><span class="sxs-lookup"><span data-stu-id="39575-129">In our case, adding a Hand Interaction Actor to **MRPawn** will:</span></span>
- <span data-ttu-id="39575-130">Adicionar um cursor às pontas dos dedos indicadores do peão.</span><span class="sxs-lookup"><span data-stu-id="39575-130">Add a cursor to the tips of the Pawn’s index fingers.</span></span>
- <span data-ttu-id="39575-131">Fornecer eventos de entrada com a mão articulada, que podem ser manipulados por meio do peão.</span><span class="sxs-lookup"><span data-stu-id="39575-131">Provide articulated hand input events that can be manipulated through the Pawn.</span></span>
- <span data-ttu-id="39575-132">Permita eventos de entrada de interação distante por meio de raios de mão, que se estendem das palmas das mãos virtuais.</span><span class="sxs-lookup"><span data-stu-id="39575-132">Allow far interaction input events through hand rays extending from the palms of the virtual hands.</span></span>

<span data-ttu-id="39575-133">Recomendamos ler a [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) sobre interações das mãos antes de prosseguir.</span><span class="sxs-lookup"><span data-stu-id="39575-133">We recommend reading through the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html) on hand interactions before continuing.</span></span>

<span data-ttu-id="39575-134">Quando você estiver pronto, abra o Blueprint **MRPawn** e navegue até o **Grafo de Eventos**.</span><span class="sxs-lookup"><span data-stu-id="39575-134">Once you're ready, open the **MRPawn** Blueprint and go to the **Event Graph**.</span></span>

1. <span data-ttu-id="39575-135">Arraste o marcador de execução do **Evento BeginPlay** e solte-o para criar um nó no local desejado.</span><span class="sxs-lookup"><span data-stu-id="39575-135">Drag and release the execution pin from **Event BeginPlay** to place a new node.</span></span>
    * <span data-ttu-id="39575-136">Selecione **Gerar Ator Com Base em Classe**, clique na lista suspensa próxima ao marcador **Classe** e pesquise por **Ator de Interação à Mão Uxt**.</span><span class="sxs-lookup"><span data-stu-id="39575-136">Select **Spawn Actor from Class**, click the dropdown next to the **Class** pin and search for **Uxt Hand Interaction Actor**.</span></span>  

2. <span data-ttu-id="39575-137">Gere um segundo **Ator de Interação à Mão Uxt**, desta vez definindo a **Mão** como **Direita**.</span><span class="sxs-lookup"><span data-stu-id="39575-137">Spawn a second **Uxt Hand Interaction Actor**, this time setting the **Hand** to **Right**.</span></span> <span data-ttu-id="39575-138">Quando o evento for iniciado, um Ator de Interação à Mão Uxt será gerado em cada mão.</span><span class="sxs-lookup"><span data-stu-id="39575-138">When the event begins, a Uxt Hand Interaction Actor will be spawned on each hand.</span></span>

<span data-ttu-id="39575-139">Seu **Grafo do Eventos** deve corresponder à seguinte captura de tela:</span><span class="sxs-lookup"><span data-stu-id="39575-139">Your **Event Graph** should match the following screenshot:</span></span>

![Gerar Atores de Interação à Mão UXT](images/unreal-uxt/4-spawnactor.PNG)

<span data-ttu-id="39575-141">Ambos os Atores de Interação à Mão Uxt precisam de proprietários e locais de transformação inicial.</span><span class="sxs-lookup"><span data-stu-id="39575-141">Both Uxt Hand Interaction Actors need owners and initial transform locations.</span></span> <span data-ttu-id="39575-142">A transformação inicial não importa nesse caso, pois as Ferramentas de Experiência de Usuário farão com que os Atores de Interação da Mão passem para as mãos virtuais assim que elas estiverem visíveis.</span><span class="sxs-lookup"><span data-stu-id="39575-142">The initial transform  doesn’t matter in this case because UX Tools will have the Hand Interaction Actors will jump to the virtual hands as soon as they're visible.</span></span> <span data-ttu-id="39575-143">No entanto, a função `SpawnActor` requer uma entrada de Transformação para evitar um erro de compilador, então você usará os valores padrão.</span><span class="sxs-lookup"><span data-stu-id="39575-143">However, the `SpawnActor` function requires a Transform input to avoid a compiler error, so you'll use the default values.</span></span>

1. <span data-ttu-id="39575-144">Arraste o marcador de um dos marcadores **Gerar Transformação** e solte-o para criar um nó no local desejado.</span><span class="sxs-lookup"><span data-stu-id="39575-144">Drag and release the pin off one of the **Spawn Transform** pins to place a new node.</span></span>
    * <span data-ttu-id="39575-145">Procure o nó **Efetuar Transformação** e, em seguida, arraste o **Valor Retornado** para o pino **Gerar Transformação** da outra mão para que ambos os nós **SpawnActor** sejam conectados.</span><span class="sxs-lookup"><span data-stu-id="39575-145">Search for the **Make Transform** node, then drag the **Return Value** to the other hand’s **Spawn Transform** so that both **SpawnActor** nodes are connected.</span></span>

2.  <span data-ttu-id="39575-146">Selecione a **seta para baixo** na parte inferior de ambos os nós **SpawnActor** para revelar o marcador **Proprietário**.</span><span class="sxs-lookup"><span data-stu-id="39575-146">Select the **down arrow** at the bottom of both **SpawnActor** nodes to reveal the **Owner** pin.</span></span>    
    * <span data-ttu-id="39575-147">Arraste o pino de um dos pinos **Proprietário** e solte-o para posicionar um novo nó.</span><span class="sxs-lookup"><span data-stu-id="39575-147">Drag the pin off one of the **Owner** pins and release to place a new node.</span></span>
    * <span data-ttu-id="39575-148">Pesquise **self** e selecione a variável **Obter uma referência a self**.</span><span class="sxs-lookup"><span data-stu-id="39575-148">Search for **self** and select the **Get a reference to self** variable.</span></span>
    * <span data-ttu-id="39575-149">Crie um vínculo entre o nó de referência do objeto **Self** e o outro marcador **Proprietário** do Ator de Interação da Mão.</span><span class="sxs-lookup"><span data-stu-id="39575-149">Create a link between the **Self** object reference node and the other Hand Interaction Actor’s **Owner** pin.</span></span>
3. <span data-ttu-id="39575-150">Por fim, marque a caixa **Mostrar o Cursor Próximo aos Destinos de Captura** para os Atores de Interação da Mão.</span><span class="sxs-lookup"><span data-stu-id="39575-150">Lastly, check the **Show Near Cursor on Grab Targets** box for both Hand Interaction Actors.</span></span> <span data-ttu-id="39575-151">Um cursor será exibido no destino de captura, à medida que o seu dedo indicador se aproximar, de modo que você possa ver em que local o dedo é relativo ao destino.</span><span class="sxs-lookup"><span data-stu-id="39575-151">A cursor should appear on the grab target as your index finger gets close, so you can see where your finger is relative to the target.</span></span>
    * <span data-ttu-id="39575-152">**Compile**, **salve** e retorne para a Janela principal.</span><span class="sxs-lookup"><span data-stu-id="39575-152">**Compile**, **save**, and return to the Main window.</span></span>

<span data-ttu-id="39575-153">Verifique se as conexões correspondem à captura de tela a seguir, mas fique à vontade para arrastar os nós a fim de tornar o Blueprint mais legível.</span><span class="sxs-lookup"><span data-stu-id="39575-153">Make sure the connections match the following screenshot, but feel free to drag around nodes to make your Blueprint more readable.</span></span>

![Configuração de Ator de Interação à Mão UXT completa](images/unreal-uxt/4-fingerptrs.PNG)

<span data-ttu-id="39575-155">Encontre mais informações sobre os Atores de Interação da Mão na [documentação das Ferramentas de Experiência de Usuário](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html).</span><span class="sxs-lookup"><span data-stu-id="39575-155">You can find more information about Hand Interaction Actors in the [UX Tools documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/HandInteraction.html).</span></span>

<span data-ttu-id="39575-156">Agora, as mãos virtuais no projeto têm uma forma de selecionar objetos, mas ainda não podem manipulá-los.</span><span class="sxs-lookup"><span data-stu-id="39575-156">Now the virtual hands in the project have a way of selecting objects, but they still can't manipulate them.</span></span> <span data-ttu-id="39575-157">Sua última tarefa antes de testar o aplicativo é adicionar componentes de Manipulador aos atores na cena.</span><span class="sxs-lookup"><span data-stu-id="39575-157">Your last task before testing the app is to add Manipulator components to the actors in the scene.</span></span>

## <a name="attaching-manipulators"></a><span data-ttu-id="39575-158">Como anexar manipuladores</span><span class="sxs-lookup"><span data-stu-id="39575-158">Attaching Manipulators</span></span>

<span data-ttu-id="39575-159">Um manipulador é um componente que responde à entrada de mão articulada e pode ser pego, girado e traduzido.</span><span class="sxs-lookup"><span data-stu-id="39575-159">A Manipulator is a component that responds to articulated hand input and can be grabbed, rotated, and translated.</span></span> <span data-ttu-id="39575-160">Aplicar a transformação do Manipulador a uma transformação de Atores permite a manipulação direta do Ator.</span><span class="sxs-lookup"><span data-stu-id="39575-160">Applying the Manipulator’s transform to an Actors transform allows direct Actor manipulation.</span></span>

1. <span data-ttu-id="39575-161">Abra o blueprint **Tabuleiro**, clique em **Adicionar Componente** e pesquise por **Manipulador Genérico Uxt** no painel **Componentes**.</span><span class="sxs-lookup"><span data-stu-id="39575-161">Open the **Board** blueprint, click **Add Component** and search for **Uxt Generic Manipulator** in the **Components** panel.</span></span>

![Adicionar manipulador genérico](images/unreal-uxt/4-addmanip.PNG)

2. <span data-ttu-id="39575-163">Expanda a seção **Manipulador Genérico** no painel **Detalhes**.</span><span class="sxs-lookup"><span data-stu-id="39575-163">Expand the **Generic Manipulator** section in the **Details** panel.</span></span> <span data-ttu-id="39575-164">Nela, você pode definir a manipulação de uma ou duas mãos, o modo de rotação e a suavização.</span><span class="sxs-lookup"><span data-stu-id="39575-164">You can set one-handed or two-handed manipulation, rotation mode, and smoothing from here.</span></span> <span data-ttu-id="39575-165">Selecione os modos que quiser e, em seguida, **Compile** e **Salve** o Board.</span><span class="sxs-lookup"><span data-stu-id="39575-165">Feel free to select whichever modes you wish, then **Compile** and **Save** Board.</span></span>

![Definir o modo](images/unreal-uxt/4-setrotmode.PNG)

3. <span data-ttu-id="39575-167">Repita as etapas acima para o Ator **WhiteKing**.</span><span class="sxs-lookup"><span data-stu-id="39575-167">Repeat the steps above for the **WhiteKing** Actor.</span></span>

<span data-ttu-id="39575-168">Encontre mais informações sobre os Componentes do Manipulador fornecidos no plug-in das Ferramentas de Experiência de Usuário de Realidade Misturada na [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html).</span><span class="sxs-lookup"><span data-stu-id="39575-168">You can find more information about the Manipulator Components provided in the Mixed Reality UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/Manipulator.html).</span></span>

## <a name="testing-the-scene"></a><span data-ttu-id="39575-169">Como testar a cena</span><span class="sxs-lookup"><span data-stu-id="39575-169">Testing the scene</span></span>

<span data-ttu-id="39575-170">Boa notícia para todos!</span><span class="sxs-lookup"><span data-stu-id="39575-170">Good news everyone!</span></span> <span data-ttu-id="39575-171">Você está pronto para testar o aplicativo com as novas mãos virtuais e entrada do usuário dele.</span><span class="sxs-lookup"><span data-stu-id="39575-171">You're ready to test out the app with its new virtual hands and user input.</span></span> <span data-ttu-id="39575-172">Clique em **Jogar** na Janela principal e você verá duas mãos de malha com raios se estendendo da palma de cada mão.</span><span class="sxs-lookup"><span data-stu-id="39575-172">Press **Play** in the Main Window and you'll see two mesh hands with rays extending from each hand’s palm.</span></span> <span data-ttu-id="39575-173">Você pode controlar as mãos e as respectivas interações da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="39575-173">You can control the hands and their interactions as follows:</span></span>
- <span data-ttu-id="39575-174">Mantenha pressionada a tecla **Alt esquerda** para controlar a **mão esquerda** e a tecla **Shift esquerda** para controlar a **mão direita**.</span><span class="sxs-lookup"><span data-stu-id="39575-174">Hold down the **left Alt** key to control the **left hand** and the **left Shift** key to control the **right hand**.</span></span>
- <span data-ttu-id="39575-175">Mova o cursor do mouse para mover a mão e use o **botão de rolagem do mouse** para mover a mão **para frente** ou **para trás**.</span><span class="sxs-lookup"><span data-stu-id="39575-175">Move your mouse to move the hand and scroll with your **mouse wheel** to move the hand **forwards** or **backwards**.</span></span>
- <span data-ttu-id="39575-176">Use o botão esquerdo do mouse para **pinçar** e o botão do meio do mouse para **cutucar**.</span><span class="sxs-lookup"><span data-stu-id="39575-176">Use the left mouse button to **pinch** and the middle mouse button to **poke**.</span></span>

> [!NOTE]
> <span data-ttu-id="39575-177">A simulação de entrada poderá não funcionar se você tiver vários headsets conectados a seu PC.</span><span class="sxs-lookup"><span data-stu-id="39575-177">Input simulation may not work if you have multiple headsets plugged into your PC.</span></span> <span data-ttu-id="39575-178">Se você estiver com problemas, experimente desconectar os outros headsets.</span><span class="sxs-lookup"><span data-stu-id="39575-178">If you're having issues, try unplugging your other headsets.</span></span>

![Mãos simuladas no visor](images/unreal-uxt/4-handsim.PNG)

<span data-ttu-id="39575-180">Tente usar as mãos simuladas para pegar, mover e posicionar o rei branco do xadrez e manipular o tabuleiro!</span><span class="sxs-lookup"><span data-stu-id="39575-180">Try using the simulated hands to pick up, move, and set down the white chess king and manipulate the board!</span></span> <span data-ttu-id="39575-181">Faça experimentos com a interação próxima e distante. Observe que, quando as mãos ficam próximas o suficiente para pegar o tabuleiro e o rei diretamente, um cursor na ponta do dedo indicador substitui o raio de mão.</span><span class="sxs-lookup"><span data-stu-id="39575-181">Experiment with both near and far interaction - notice that when your hands get close enough to grab the board and king directly, a finger cursor at the tip of the index finger replaces the hand ray.</span></span>

<span data-ttu-id="39575-182">Você pode obter mais informações sobre o recurso de mãos simuladas fornecido pelo plug-in Ferramentas de UX do MRTK na [documentação](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html).</span><span class="sxs-lookup"><span data-stu-id="39575-182">You can find more information about the simulated hands feature provided by the MRTK UX Tools plugin in the [documentation](https://microsoft.github.io/MixedReality-UXTools-Unreal/Docs/InputSimulation.html).</span></span>

<span data-ttu-id="39575-183">Agora que suas mãos virtuais podem interagir com objetos, você está pronto para passar para o próximo tutorial e adicionar interfaces do usuário e eventos.</span><span class="sxs-lookup"><span data-stu-id="39575-183">Now that your virtual hands can interact with objects, you're ready to move on to the next tutorial and add user interfaces and events.</span></span>

[<span data-ttu-id="39575-184">Próxima seção: 5. Como adicionar um botão e redefinir locais de peças</span><span class="sxs-lookup"><span data-stu-id="39575-184">Next Section: 5. Adding a button & resetting piece locations</span></span>](unreal-uxt-ch5.md)
