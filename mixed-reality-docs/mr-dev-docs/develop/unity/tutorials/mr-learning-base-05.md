---
title: Criar conteúdo dinâmico usando Solucionadores
description: Este curso mostra como usar os solucionadores do MRTK (Kit de Ferramentas de Realidade Misturada) para criar um conteúdo dinâmico.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, solucionadores
ms.localizationpriority: high
ms.openlocfilehash: 6006bf5e3edaee13c8ede0bdc04fd5ea928f1757
ms.sourcegitcommit: a56a551ebc59529a3683fe6db90d59f982ab0b45
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2021
ms.locfileid: "98579135"
---
# <a name="5-creating-dynamic-content-using-solvers"></a><span data-ttu-id="432b3-104">5. Criar conteúdo dinâmico usando Solucionadores</span><span class="sxs-lookup"><span data-stu-id="432b3-104">5. Creating dynamic content using Solvers</span></span>

<span data-ttu-id="432b3-105">Neste tutorial, você vai explorar maneiras de posicionar hologramas dinamicamente usando as ferramentas de posicionamento disponíveis do MRTK, conhecidas como Solucionadores, para resolver cenários de posicionamento espacial complexos.</span><span class="sxs-lookup"><span data-stu-id="432b3-105">In this tutorial, you will explore ways to dynamically place holograms using the MRTK's available placement tools, known as Solvers, to solve complex spatial placement scenarios.</span></span> <span data-ttu-id="432b3-106">No MRTK, os Solucionadores são um sistema de scripts e comportamentos usados para permitir que os objetos sigam você, o usuário ou outros objetos do jogo na cena.</span><span class="sxs-lookup"><span data-stu-id="432b3-106">In the MRTK, Solvers are a system of scripts and behaviors used to allow objects to follow you, the user, or other game objects in the scene.</span></span> <span data-ttu-id="432b3-107">Eles também podem ser usados para se ajustar a determinadas posições, tornando seu aplicativo mais intuitivo.</span><span class="sxs-lookup"><span data-stu-id="432b3-107">They can also be used to snap to certain positions, making your app more intuitive.</span></span>

## <a name="objectives"></a><span data-ttu-id="432b3-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="432b3-108">Objectives</span></span>

* <span data-ttu-id="432b3-109">Apresentar os Solucionadores do MRTK</span><span class="sxs-lookup"><span data-stu-id="432b3-109">Introduce the MRTK's Solvers</span></span>
* <span data-ttu-id="432b3-110">Saiba como usar os solucionadores para direcionar o usuário para objetos</span><span class="sxs-lookup"><span data-stu-id="432b3-110">Learn how to use Solvers to direct the user to objects</span></span>
* <span data-ttu-id="432b3-111">Saiba como usar os solucionadores para reposicionar objetos</span><span class="sxs-lookup"><span data-stu-id="432b3-111">Learn how to use Solvers to reposition objects</span></span>

## <a name="location-of-solvers-in-the-mrtk"></a><span data-ttu-id="432b3-112">Localização dos Solucionadores no MRTK</span><span class="sxs-lookup"><span data-stu-id="432b3-112">Location of Solvers in the MRTK</span></span>

 <span data-ttu-id="432b3-113">Os Solucionadores do MRTK estão localizados na pasta MRTK SDK.</span><span class="sxs-lookup"><span data-stu-id="432b3-113">The MRTK's Solvers are located in the MRTK SDK folder.</span></span> <span data-ttu-id="432b3-114">Para ver os Solucionadores disponíveis em seu projeto, na janela Projeto, navegue até **Ativos** > **MRTK** > **SDK** > **Recursos** > **Utilitários** > **Solucionadores**:</span><span class="sxs-lookup"><span data-stu-id="432b3-114">To see the available Solvers in your project, in the Project window, navigate to **Assets** > **MRTK** > **SDK** > **Features** > **Utilities** > **Solvers**:</span></span>

![Janela Projeto do Unity com a pasta Solucionadores selecionada](images/mr-learning-base/base-05-section1-step1-1.png)

<span data-ttu-id="432b3-116">Neste tutorial, examinaremos a implementação do Solucionador de Indicador Direcional e o Solucionador Toque para Posicionar.</span><span class="sxs-lookup"><span data-stu-id="432b3-116">In this tutorial, we will review the implementation of the Directional Indicator Solver and the Tap To Place Solver.</span></span> <span data-ttu-id="432b3-117">Para saber mais sobre a gama completa de Solucionadores disponíveis no MRTK, você pode consultar o guia [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="432b3-117">To learn more about the full range of Solvers available in the MRTK, you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!NOTE]
> <span data-ttu-id="432b3-118">O Solucionador de Indicador Direcional não está localizado nas pastas de Solucionadores supramencionadas, mas nas pastas Ativos > MRTK > SDK > Experimental > Recursos > Utilitários, pois é um recurso experimental.</span><span class="sxs-lookup"><span data-stu-id="432b3-118">The Directional Indicator Solver is not located in the Solvers folders referenced above, but in the Assets > MRTK > SDK > Experimental > Features > Utilities folders, because it is an experimental feature.</span></span>

## <a name="using-the-directional-indicator-solver-to-direct-the-user-to-objects"></a><span data-ttu-id="432b3-119">Como usar o Solucionador de Indicador Direcional para direcionar o usuário a objetos</span><span class="sxs-lookup"><span data-stu-id="432b3-119">Using the Directional Indicator Solver to direct the user to objects</span></span>

<span data-ttu-id="432b3-120">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-Fabricados**, clique e arraste o pré-fabricado **Divisa** para a janela Hierarquia e defina sua **Posição** de Transformação como X = 0, Y = 0, Z = 2 para posicioná-lo perto do objeto RoverExplorer:</span><span class="sxs-lookup"><span data-stu-id="432b3-120">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder, click-and-drag the **Chevron** prefab into the Hierarchy window, and set it's Transform **Position** to X = 0, Y = 0, Z = 2 to position it near the RoverExplorer object:</span></span>

![Unity com o pré-fabricado Divisa recém-adicionado selecionado](images/mr-learning-base/base-05-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="432b3-122">Se você descobrir que a câmera ou quaisquer outros ícones em sua cena estão ocultando os objetos ou causando distração, poderá ocultá-los <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">alternando o Gizmos</a> para a posição Desligado, conforme mostra a imagem acima.</span><span class="sxs-lookup"><span data-stu-id="432b3-122">If you find that the camera or any other icons in your scene are hiding the objects or are distracting, you can hide these by <a href="https://docs.unity3d.com/2019.1/Documentation/Manual/GizmosMenu.html" target="_blank">toggling the Gizmos</a> to the off position, as shown in the image above.</span></span> <span data-ttu-id="432b3-123">Para saber mais sobre o menu Gizmos e como você pode usá-lo para otimizar a exibição de cena, consulte a documentação do <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">menu Gizmos</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="432b3-123">To learn more about the Gizmos menu and how you can use it to optimize your scene view, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/GizmosMenu.html" target="_blank">Gizmos menu</a> documentation.</span></span>

<span data-ttu-id="432b3-124">Renomeie o **Indicador** do objeto de Divisa recém-adicionado e, em seguida, na janela do Inspetor, use o botão **Adicionar Componente** para adicionar o componente **DirectionalIndicator**:</span><span class="sxs-lookup"><span data-stu-id="432b3-124">Rename the newly added Chevron object **Indicator**, then in the Inspector window, use the **Add Component** button to add the **DirectionalIndicator**:</span></span>

![Unity com o componente do solucionador DirectionalIndicator adicionado](images/mr-learning-base/base-05-section2-step1-2.png)

> [!NOTE]
> <span data-ttu-id="432b3-126">Quando você adiciona um solucionador, nesse caso, o componente DirectionalIndicator, o componente SolverHandler é adicionado automaticamente porque os solucionadores exigem isso.</span><span class="sxs-lookup"><span data-stu-id="432b3-126">When you add a Solver, in this case, the DirectionalIndicator component, the SolverHandler component is automatically added because Solvers require it.</span></span>

> [!NOTE]
> <span data-ttu-id="432b3-127">O Controlador de Indicador Direcional (Script) não faz parte do MRTK, mas foi incluído nos ativos do tutorial.</span><span class="sxs-lookup"><span data-stu-id="432b3-127">The Directional Indicator Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="432b3-128">Configure os componentes DirectionalIndicator e SolverHandler da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="432b3-128">Configure the DirectionalIndicator and SolverHandler components as follows:</span></span>

* <span data-ttu-id="432b3-129">Verifique se o **Tipo de Destino Rastreado** do componente **SolverHandler** está definido como **Cabeça**</span><span class="sxs-lookup"><span data-stu-id="432b3-129">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="432b3-130">Atribua o **RoverExplorer** ao **Destino Direcional** do componente **DirectionalIndicator** arrastando-o da janela hierarquia para o campo **Nenhum (Transformação)**</span><span class="sxs-lookup"><span data-stu-id="432b3-130">Assign the **RoverExplorer** to the **DirectionalIndicator** component's **Directional Target** by dragging it from the Hierarchy window into the **None (Transform)** field</span></span>
* <span data-ttu-id="432b3-131">Altere o **Deslocamento de Exibição** para 0,2</span><span class="sxs-lookup"><span data-stu-id="432b3-131">Change the **View Offset** to 0.2</span></span>

![Unity com o componente do solucionador DirectionalIndicator configurado](images/mr-learning-base/base-05-section2-step1-3.png)

<span data-ttu-id="432b3-133">Pressione o botão Reproduzir para entrar no modo Jogo, pressione e mantenha o botão direito do mouse pressionado enquanto move o mouse para a esquerda ou para a direita para girar a direção do foco e observe o seguinte:</span><span class="sxs-lookup"><span data-stu-id="432b3-133">Press the Play button to enter Game mode, press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, and notice the following:</span></span>

* <span data-ttu-id="432b3-134">Quando você olhar para longe do objeto RoverExplorer, o objeto de Indicador será exibido e apontará para o objeto RoverExplorer</span><span class="sxs-lookup"><span data-stu-id="432b3-134">When you look away from the RoverExplorer object, the Indicator object will appear and point towards the RoverExplorer object</span></span>

![Modo de exibição dividida do Modo de reprodução do Unity com o solucionador DirectionalIndicator em uso](images/mr-learning-base/base-05-section2-step1-4.png)

> [!NOTE]
> <span data-ttu-id="432b3-136">Se você não vir o raio da câmera na janela Cena, verifique se o menu Gizmos está habilitado, como mostra a imagem acima.</span><span class="sxs-lookup"><span data-stu-id="432b3-136">If you don't see the camera ray in your Scene window, make sure your Gizmos menu is enabled, as shown in the image above.</span></span>

> [!TIP]
> <span data-ttu-id="432b3-137">Para saber como usar a simulação de entrada no editor, você pode consultar o guia [Como usar a simulação de entrada de mão no editor para testar uma cena](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) no [Portal de documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="432b3-137">To learn how to use the in-editor input simulation, you can refer to the [Using the In-Editor Hand Input Simulation to test a scene](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/GettingStartedWithTheMRTK.html#using-the-in-editor-hand-input-simulation-to-test-a-scene) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!TIP]
> <span data-ttu-id="432b3-138">Se o computador tiver um microfone, você poderá alternar facilmente o estado ativo do painel Diagnóstico que aparece na janela Jogo usando o comando de fala "alternar diagnóstico".</span><span class="sxs-lookup"><span data-stu-id="432b3-138">If your computer has a microphone, you can easily toggle the active state of the Diagnostics panel that appears in the Game window by using the speech command "toggle diagnostics."</span></span> <span data-ttu-id="432b3-139">Como alternativa, você pode desabilitá-lo no Perfil de Configuração do MRTK > Diagnóstico > Habilitar o Sistema de Diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="432b3-139">Alternatively, you can disable it in the MRTK Configuration Profile > Diagnostics > Enable Diagnostics System.</span></span> <span data-ttu-id="432b3-140">No entanto, geralmente é recomendável manter o Sistema de Diagnóstico ativo durante o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="432b3-140">However, it is generally recommended to keep the Diagnostics System active during development.</span></span>

## <a name="using-the-tap-to-place-solver-to-reposition-objects"></a><span data-ttu-id="432b3-141">Usando o Solucionador Tocar para Posicionar para reposicionar objetos</span><span class="sxs-lookup"><span data-stu-id="432b3-141">Using the Tap to Place Solver to reposition objects</span></span>

<span data-ttu-id="432b3-142">Na janela hierarquia, selecione o objeto RoverExplorer > **RoverAssembly** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Tocar para Posicionar (Script)** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="432b3-142">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **Tap To Place (Script)** component, and configure it as follows:</span></span>

* <span data-ttu-id="432b3-143">Verifique se o **Tipo de Destino Rastreado** do componente **SolverHandler** está definido como **Cabeça**</span><span class="sxs-lookup"><span data-stu-id="432b3-143">Verify that the **SolverHandler** component's **Tracked Target Type** is set to **Head**</span></span>
* <span data-ttu-id="432b3-144">Marque a caixa de seleção **Manter Orientação Vertical**</span><span class="sxs-lookup"><span data-stu-id="432b3-144">Check the **Keep Orientation Vertical** checkbox</span></span>
* <span data-ttu-id="432b3-145">No menu suspenso **Superfícies Magnéticas** > **Elemento 0**, desmarque todas as opções que esperam **Reconhecimento Espacial**</span><span class="sxs-lookup"><span data-stu-id="432b3-145">From the **Magnetic Surfaces** > **Element 0** dropdown, uncheck all options expect **Spatial Awareness**</span></span>

![Unity com o componente do solucionador TapToPlace adicionado e configurado](images/mr-learning-base/base-05-section3-step1-1.png)

> [!NOTE]
> <span data-ttu-id="432b3-147">A configuração de Superfícies Magnéticas determina quais objetos o componente Tocar para Posicionar (Script) pode detectar ao posicionar um objeto.</span><span class="sxs-lookup"><span data-stu-id="432b3-147">The Magnetic Surfaces setting determines which objects the Tap To Place (Script) component can detect when placing an object.</span></span> <span data-ttu-id="432b3-148">Ao alterar a configuração para Somente Reconhecimento Espacial, o componente Tocar para Posicionar (Script) só poderá posicionar o Rover em objetos na camada do Unity denominada Reconhecimento Espacial, que, por padrão, é a Malha de Conscientização Espacial gerada pelo HoloLens.</span><span class="sxs-lookup"><span data-stu-id="432b3-148">By changing the setting to only Spatial Awareness, the Tap To Place (Script) component will only be able to place the Rover on objects on the Unity Layer named Spatial Awareness, which by default is the Spatial Awareness Mesh generated by the HoloLens.</span></span>
>
><span data-ttu-id="432b3-149">Para saber mais sobre Camadas, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Camadas</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="432b3-149">To learn more about Layers, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/Layers.html" target="_blank">Layers</a> documentation.</span></span>

> [!TIP]
> <span data-ttu-id="432b3-150">Se você quiser ver a malha de conscientização espacial ao testar a funcionalidade Tocar para Posicionar em seu HoloLens, poderá definir temporariamente a Opção de Exibição do Observador de Malha Espacial como Visível.</span><span class="sxs-lookup"><span data-stu-id="432b3-150">If you want to see the Spatial Awareness Mesh when testing the Tap To Place functionality on your HoloLens, you can temporarily set the Spatial Mesh Observer's Display Option to Visible.</span></span> <span data-ttu-id="432b3-151">Para obter um lembrete sobre como alterar a Opção de Exibição, você pode consultar as instruções de [Como alterar a opção de exibição de conscientização espacial](mr-learning-base-03.md#changing-the-spatial-awareness-display-option).</span><span class="sxs-lookup"><span data-stu-id="432b3-151">For a reminder on how to change the Display Option, you can refer to the [Changing the Spatial Awareness Display Option](mr-learning-base-03.md#changing-the-spatial-awareness-display-option) instructions.</span></span>

<span data-ttu-id="432b3-152">Com o objeto RoverAssembly ainda selecionado na janela Hierarquia, na janela Inspetor, localize o evento **On Placing Started ()** e clique no ícone **+** para adicionar um evento:</span><span class="sxs-lookup"><span data-stu-id="432b3-152">With the RoverAssembly object still selected in the Hierarchy window, in the Inspector window, locate the **On Placing Started ()** event and click the **+** icon to add a new event:</span></span>

![Unity com o evento TapToPlace OnPlacingStarted adicionado](images/mr-learning-base/base-05-section3-step1-2.png)

<span data-ttu-id="432b3-154">Configure o evento da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="432b3-154">Configure the event as follows:</span></span>

* <span data-ttu-id="432b3-155">Atribua o objeto **RoverAssembly** como um ouvinte para o evento On Placing Started () arrastando-o da janela Hierarquia para o campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="432b3-155">Assign the **RoverAssembly** object as a listener for the On Placing Started () event by dragging it from the Hierarchy window into the **None (Object)** field</span></span>
* <span data-ttu-id="432b3-156">Na lista suspensa **Sem Função**, selecione **TapToPlace** > **float SurfaceNormalOffset** para atualizar o valor da propriedade SurfaceNormalOffset quando o evento é disparado</span><span class="sxs-lookup"><span data-stu-id="432b3-156">From the **No Function** dropdown, select **TapToPlace** > **float SurfaceNormalOffset** to update the SurfaceNormalOffset property value when the event is triggered</span></span>
* <span data-ttu-id="432b3-157">Verifique se o argumento está definido como **0**</span><span class="sxs-lookup"><span data-stu-id="432b3-157">Verify that the argument is set to **0**</span></span>

![Unity com o evento TapToPlace OnPlacingStarted configurado](images/mr-learning-base/base-05-section3-step1-3.png)

<span data-ttu-id="432b3-159">Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Objeto 3D** > **Cubo**, para criar um objeto temporário que representa o aterramento e configure o componente **Transformação** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="432b3-159">In the Hierarchy window, right-click on an empty spot and select **3D Object** > **Cube**, to create a temporary object representing the ground, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="432b3-160">**Posição**: X = 0, Y = -1,65, Z = 6</span><span class="sxs-lookup"><span data-stu-id="432b3-160">**Position**: X = 0, Y = -1.65, Z = 6</span></span>
* <span data-ttu-id="432b3-161">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="432b3-161">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="432b3-162">**Escala**: X = 10, Y = 0,2, Z = 10</span><span class="sxs-lookup"><span data-stu-id="432b3-162">**Scale**: X = 10, Y = 0.2, Z = 10</span></span>

![Unity com o objeto de cubo de chão temporário adicionado e posicionado](images/mr-learning-base/base-05-section3-step1-4.png)

<span data-ttu-id="432b3-164">Com o Cubo temporário ainda selecionado na janela Hierarquia, na janela Inspetor, use a lista suspensa **Camadas** para alterar a configuração de camada do cubo apenas para incluir a camada **Conscientização Espacial**:</span><span class="sxs-lookup"><span data-stu-id="432b3-164">With the temporary Cube still selected in the Hierarchy window, in the Inspector window, use the **Layers** dropdown to change the Cube's Layer setting only to include the **Spatial Awareness** layer:</span></span>

![Unity com a Camada de objeto de cubo de chão temporário definida como Reconhecimento Espacial](images/mr-learning-base/base-05-section3-step1-5.png)

<span data-ttu-id="432b3-166">Pressione o botão Reproduzir para entrar no modo Jogo e pressione e segure o botão direito do mouse enquanto move o mouse para baixo até o foco atingir o objeto RoverAssembly:</span><span class="sxs-lookup"><span data-stu-id="432b3-166">Press the Play button to enter Game mode, then press-and-hold the right mouse button while moving your mouse down until the gaze hit's the RoverAssembly object:</span></span>

![Modo de exibição dividida do Modo de reprodução do Unity com o foco sobre o objeto RoverAssembly](images/mr-learning-base/base-05-section3-step1-6.png)

<span data-ttu-id="432b3-168">Clique no botão esquerdo do mouse para iniciar o processo de tocar para posicionar:</span><span class="sxs-lookup"><span data-stu-id="432b3-168">Click the left mouse button to start the tap-to-place process:</span></span>

![Modo de exibição dividida do Modo de reprodução do Unity com o posicionamento de TapToPlace iniciado](images/mr-learning-base/base-05-section3-step1-7.png)

<span data-ttu-id="432b3-170">Pressione e mantenha o botão direito do mouse pressionado enquanto move o mouse para a esquerda ou para a direita para girar sua direção de foco. Quando estiver satisfeito com o posicionamento, clique no botão esquerdo do mouse:</span><span class="sxs-lookup"><span data-stu-id="432b3-170">Press-and-hold the right mouse button while moving your mouse to the left or right to rotate your gaze direction, when you are happy with the placement, click the left mouse button:</span></span>

![Modo de exibição dividida do Modo de reprodução do Unity com o posicionamento de TapToPlace encerrado](images/mr-learning-base/base-05-section3-step1-8.png)

<span data-ttu-id="432b3-172">Quando terminar de testar o recurso no modo de jogo, clique com o botão direito do mouse no objeto Cubo e selecione **Excluir** para removê-lo da cena:</span><span class="sxs-lookup"><span data-stu-id="432b3-172">Once you are done testing the feature in the Game mode, right-click on the Cube object and select **Delete** to remove it from the scene:</span></span>

![Unity com o cubo de chão temporário selecionado e o menu pop-up contextual Excluir](images/mr-learning-base/base-05-section3-step1-9.png)

## <a name="congratulations"></a><span data-ttu-id="432b3-174">Parabéns</span><span class="sxs-lookup"><span data-stu-id="432b3-174">Congratulations</span></span>

<span data-ttu-id="432b3-175">Neste tutorial, você aprendeu a usar o Solucionador Direcional do MRTK para ter um elemento de interface do usuário instruindo intuitivamente os usuários a objetos.</span><span class="sxs-lookup"><span data-stu-id="432b3-175">In this tutorial, you learned how to use the MRTK's Directional Indicator Solver to have a UI element intuitively direct the user to objects.</span></span> <span data-ttu-id="432b3-176">Você também aprendeu a usar o Solucionador Toque para Posicionar para reposicionar os objetos facilmente.</span><span class="sxs-lookup"><span data-stu-id="432b3-176">You also learned how to use the Tap To Place Solver to reposition objects easily.</span></span>

<span data-ttu-id="432b3-177">Para saber mais sobre esses e outros solucionadores incluídos no MRTK, consulte o guia [Solucionadores](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="432b3-177">To learn more about these and other solvers included with the MRTK,  you can refer to the [Solvers](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_Solver.html) guide in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="432b3-178">Próximo tutorial: 6. Como criar interfaces do usuário</span><span class="sxs-lookup"><span data-stu-id="432b3-178">Next Tutorial: 6. Creating user interfaces</span></span>](mr-learning-base-06.md)
