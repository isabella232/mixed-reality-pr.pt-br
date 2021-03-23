---
title: Tutoriais do MRTK – 4. Como posicionar objetos na cena
description: Este curso mostra como posicionar objetos na cena e como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para organizar objetos em uma grade.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, solucionadores, coleção de objetos de grade
ms.localizationpriority: high
ms.openlocfilehash: 9087800eca3536704ed4ef01a5d8178720b6a875
ms.sourcegitcommit: 59c91f8c70d1ad30995fba6cf862615e25e78d10
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/19/2021
ms.locfileid: "99590488"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="38c6f-105">4. Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="38c6f-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="38c6f-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="38c6f-106">Overview</span></span>

<span data-ttu-id="38c6f-107">Neste tutorial, você importará os ativos do tutorial e posicionará os objetos fornecidos na cena.</span><span class="sxs-lookup"><span data-stu-id="38c6f-107">In this tutorial, you will import the tutorial assets and position the provided objects in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="38c6f-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="38c6f-108">Objectives</span></span>

* <span data-ttu-id="38c6f-109">Saiba como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="38c6f-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="38c6f-110">Saiba como usar o recurso Coleção de Objetos de Grade do MRTK</span><span class="sxs-lookup"><span data-stu-id="38c6f-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="38c6f-111">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="38c6f-111">Importing the tutorial assets</span></span>

<span data-ttu-id="38c6f-112">Baixe o seguinte pacote personalizado do Unity:</span><span class="sxs-lookup"><span data-stu-id="38c6f-112">Download the following Unity custom package:</span></span>

* [<span data-ttu-id="38c6f-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span><span class="sxs-lookup"><span data-stu-id="38c6f-113">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.4.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage)

<span data-ttu-id="38c6f-114">Para importar um pacote personalizado do Unity, no menu do Unity selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:</span><span class="sxs-lookup"><span data-stu-id="38c6f-114">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](images/mr-learning-base/base-04-section1-step1-1.png)

<span data-ttu-id="38c6f-116">Na janela Importar pacote..., selecione o **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage** que você baixou e clique no botão Abrir:</span><span class="sxs-lookup"><span data-stu-id="38c6f-116">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.4.0.unitypackage** you downloaded and click the Open button:</span></span>

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="38c6f-118">Na janela Importar Pacote do Unity, clique no botão Todos para garantir que todos os ativos sejam selecionados e clique no botão Importar para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="38c6f-118">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](images/mr-learning-base/base-04-section1-step1-3.png)

<span data-ttu-id="38c6f-120">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="38c6f-120">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Janelas Hierarquia, Cena e Projeto do Unity após a importação dos ativos do tutorial](images/mr-learning-base/base-04-section1-step1-4.png)

## <a name="creating-the-parent-object"></a><span data-ttu-id="38c6f-122">Como criar um objeto pai</span><span class="sxs-lookup"><span data-stu-id="38c6f-122">Creating the parent object</span></span>

<span data-ttu-id="38c6f-123">Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Criar Vazio** para adicionar um objeto vazio à sua cena:</span><span class="sxs-lookup"><span data-stu-id="38c6f-123">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Menu pop-up contextual Criar Vazio do Unity](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="38c6f-125">Para exibir a janela Cena e Jogo lado a lado como mostra a imagem acima, arraste a janela Jogo para o lado direito da janela Cena.</span><span class="sxs-lookup"><span data-stu-id="38c6f-125">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="38c6f-126">Para saber mais sobre como personalizar o seu workspace, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Como personalizar o seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="38c6f-126">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="38c6f-127">Clique com o botão direito do mouse no objeto recém-criado, selecione **Renomear** e altere o nome para **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="38c6f-127">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Menu pop-up contextual Renomear do Unity](images/mr-learning-base/base-04-section2-step1-2.png)

<span data-ttu-id="38c6f-129">Com o objeto RoverExplorer ainda selecionado, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="38c6f-129">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="38c6f-130">**Posição**: X = 0, Y = -0,6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="38c6f-130">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="38c6f-131">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="38c6f-131">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="38c6f-132">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="38c6f-132">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o objeto RoverExplorer selecionado e posicionado](images/mr-learning-base/base-04-section2-step1-3.png)

> [!NOTE]
> <span data-ttu-id="38c6f-134">A câmera representa a cabeça do usuário e é posicionada na origem, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="38c6f-134">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="38c6f-135">Em geral, uma unidade no Unity corresponde a aproximadamente um metro no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="38c6f-135">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="38c6f-136">Porém, há exceções, por exemplo, quando objetos são filhos de objetos dimensionados.</span><span class="sxs-lookup"><span data-stu-id="38c6f-136">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="38c6f-137">No cenário acima, o RoverExplorer é posicionado 2 metros na frente e 0,6 metros abaixo da cabeça do usuário.</span><span class="sxs-lookup"><span data-stu-id="38c6f-137">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="38c6f-138">Como adicionar os pré-fabricados do tutorial</span><span class="sxs-lookup"><span data-stu-id="38c6f-138">Adding the tutorial prefabs</span></span>

<span data-ttu-id="38c6f-139">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados**:</span><span class="sxs-lookup"><span data-stu-id="38c6f-139">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Janela Projeto do Unity com a pasta Pré-fabricados selecionada](images/mr-learning-base/base-04-section3-step1-1.png)

> [!TIP]
> <span data-ttu-id="38c6f-141">Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um GameObject pré-configurado armazenado como um Ativo Unitário e pode ser reutilizado em todo o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="38c6f-141">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="38c6f-142">Na janela Projeto, clique e arraste o pré-fabricado **Tabela** no objeto **RoverExplorer** para torná-la um filho do objeto RoverExplorer e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="38c6f-142">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="38c6f-143">**Posição**: X = 0, Y = -0,005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="38c6f-143">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="38c6f-144">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="38c6f-144">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="38c6f-145">**Escala**: X = 1,2, Y = 0,01, Z = 1,2</span><span class="sxs-lookup"><span data-stu-id="38c6f-145">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity com o pré-fabricado Tabela recém-adicionado selecionado e posicionado](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="38c6f-147">Para exibir a cena conforme mostrado na imagem acima use o <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Utensílio de Cena</a>, localizado no canto superior direito da janela Cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço, clique duas vezes no objeto MixedRealityPlayspace para colocá-lo em foco na câmera e amplie se necessário.</span><span class="sxs-lookup"><span data-stu-id="38c6f-147">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="38c6f-148">Na janela Projeto, clique e arraste o pré-fabricado **RoverAssembly** para o objeto **RoverExplorer** para torná-lo um filho do objeto RoverExplorer e, em seguida, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="38c6f-148">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="38c6f-149">**Posição**: X = -0,1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="38c6f-149">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="38c6f-150">**Rotação**: X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="38c6f-150">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="38c6f-151">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="38c6f-151">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o pré-fabricado RoverAssembly recém-adicionado selecionado e posicionado](images/mr-learning-base/base-04-section3-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="38c6f-153">Como organizar objetos em uma coleção</span><span class="sxs-lookup"><span data-stu-id="38c6f-153">Organizing objects in a collection</span></span>

<span data-ttu-id="38c6f-154">Na janela Hierarquia, clique com o botão direito do mouse no objeto **RoverExplorer** e selecione **Criar Vazio** para adicionar um objeto vazio como um filho do RoverExplorer, nomeie o objeto **RoverParts** e configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="38c6f-154">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="38c6f-155">**Posição**: X = 0, Y = 0,06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="38c6f-155">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="38c6f-156">**Rotação**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="38c6f-156">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="38c6f-157">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="38c6f-157">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o objeto RoverParts recém-criado selecionado e posicionado](images/mr-learning-base/base-04-section4-step1-1.png)

<span data-ttu-id="38c6f-159">Na janela Hierarquia, selecione todos os objetos filhos em RoverExplorer > RoverAssembly > RoverModel > **Parts** clique com o botão direito do mouse neles e selecione **Duplicar** para criar uma cópia de cada uma das peças:</span><span class="sxs-lookup"><span data-stu-id="38c6f-159">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity com todas as Peças selecionadas e o menu pop-up contextual Duplicar](images/mr-learning-base/base-04-section4-step1-2.png)

> [!TIP]
> <span data-ttu-id="38c6f-161">Para selecionar vários objetos adjacentes, pressione e segure a tecla SHIFT enquanto usa o mouse para selecionar o primeiro e o último objeto.</span><span class="sxs-lookup"><span data-stu-id="38c6f-161">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="38c6f-162">Com os objetos filho de Peças recentemente duplicados ainda selecionados, clique e arraste-os para o objeto **RoverParts** para torná-los objetos filho do objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="38c6f-162">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity com as peças recém-duplicadas como filhos do objeto RoverParts](images/mr-learning-base/base-04-section4-step1-3.png)

<span data-ttu-id="38c6f-164">Para facilitar o trabalho com a sua cena, na janela Hierarquia, clique no ícone de **olho** à esquerda do objeto para desativar a **visibilidade da cena** para o objeto **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="38c6f-164">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="38c6f-165">Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo:</span><span class="sxs-lookup"><span data-stu-id="38c6f-165">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity com a visibilidade de cena do RoverAssembly desativada](images/mr-learning-base/base-04-section4-step1-4.png)

> [!TIP]
> <span data-ttu-id="38c6f-167">Para saber mais sobre os controles de Visibilidade da Cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="38c6f-167">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="38c6f-168">Na janela Hierarquia, limpe os nomes dos objetos filho RoverParts substituindo o **(1)** acrescentado por **_Part**:</span><span class="sxs-lookup"><span data-stu-id="38c6f-168">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity com o nome de peças duplicadas limpo](images/mr-learning-base/base-04-section4-step1-5.png)

<span data-ttu-id="38c6f-170">Na janela Hierarquia, selecione o objeto **RoverParts** e, em seguida, na janela Inspetor, clique no botão **Adicionar Componente** e pesquise e selecione **GridObjectCollection** para adicionar o componente GridObjectCollection ao objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="38c6f-170">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Objeto RoverParts do Unity com a Adição de Coleção de Objetos de Grade de Componentes em andamento](images/mr-learning-base/base-04-section4-step1-6.png)

<span data-ttu-id="38c6f-172">Configure os valores de componente **GridObjectCollection** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="38c6f-172">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="38c6f-173">**Tipo de Classificação**: Alfabético</span><span class="sxs-lookup"><span data-stu-id="38c6f-173">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="38c6f-174">**Layout**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="38c6f-174">**Layout**: Horizontal</span></span>
* <span data-ttu-id="38c6f-175">**Largura da Célula**: 0,25</span><span class="sxs-lookup"><span data-stu-id="38c6f-175">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="38c6f-176">**Distância do pai**: 0,38</span><span class="sxs-lookup"><span data-stu-id="38c6f-176">**Distance from parent**: 0.38</span></span>

![Unity com o componente GridObjectCollection configurado](images/mr-learning-base/base-04-section4-step1-7.png)

<span data-ttu-id="38c6f-178">Em seguida, clique no botão **Atualizar Coleção** para atualizar a posição dos objetos filho RoverParts:</span><span class="sxs-lookup"><span data-stu-id="38c6f-178">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity com o componente GridObjectCollection aplicado](images/mr-learning-base/base-04-section4-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="38c6f-180">Parabéns</span><span class="sxs-lookup"><span data-stu-id="38c6f-180">Congratulations</span></span>

<span data-ttu-id="38c6f-181">Neste tutorial, você aprendeu a posicionar objetos na cena em relação ao usuário e a usar o recurso Coleção de Objetos de Grade do MRTK para organizar objetos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="38c6f-181">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="38c6f-182">Próximo tutorial: 5. Criar conteúdo dinâmico usando Solucionadores</span><span class="sxs-lookup"><span data-stu-id="38c6f-182">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
