---
title: Tutoriais do MRTK – 4. Como posicionar objetos na cena
description: Este curso mostra como posicionar objetos na cena e como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para organizar objetos em uma grade.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, solucionadores, coleção de objetos de grade
ms.localizationpriority: high
ms.openlocfilehash: 28cebe871e1046e8668a079affabf6167632cfa4
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982989"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="bba09-105">4. Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="bba09-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="bba09-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="bba09-106">Overview</span></span>

<span data-ttu-id="bba09-107">Neste tutorial, você posicionará na cena os objetos fornecidos nos ativos.</span><span class="sxs-lookup"><span data-stu-id="bba09-107">In this tutorial, you will position the provided objects from the tutorial assets in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="bba09-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="bba09-108">Objectives</span></span>

* <span data-ttu-id="bba09-109">Saiba como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="bba09-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="bba09-110">Saiba como usar o recurso Coleção de Objetos de Grade do MRTK</span><span class="sxs-lookup"><span data-stu-id="bba09-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="creating-the-parent-object"></a><span data-ttu-id="bba09-111">Como criar um objeto pai</span><span class="sxs-lookup"><span data-stu-id="bba09-111">Creating the parent object</span></span>

<span data-ttu-id="bba09-112">Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Criar Vazio** para adicionar um objeto vazio à sua cena:</span><span class="sxs-lookup"><span data-stu-id="bba09-112">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Menu pop-up contextual Criar Vazio do Unity](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="bba09-114">Para exibir a janela Cena e Jogo lado a lado como mostra a imagem acima, arraste a janela Jogo para o lado direito da janela Cena.</span><span class="sxs-lookup"><span data-stu-id="bba09-114">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="bba09-115">Para saber mais sobre como personalizar o seu workspace, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Como personalizar o seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="bba09-115">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="bba09-116">Clique com o botão direito do mouse no objeto recém-criado, selecione **Renomear** e altere o nome para **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="bba09-116">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Menu pop-up contextual Renomear do Unity](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="bba09-118">Com o objeto RoverExplorer ainda selecionado, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bba09-118">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="bba09-119">**Posição**: X = 0, Y = -0,6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="bba09-119">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="bba09-120">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bba09-120">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="bba09-121">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="bba09-121">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o objeto RoverExplorer selecionado e posicionado](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> <span data-ttu-id="bba09-123">A câmera representa a cabeça do usuário e é posicionada na origem, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="bba09-123">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="bba09-124">Em geral, uma unidade no Unity corresponde a aproximadamente um metro no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="bba09-124">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="bba09-125">Porém, há exceções, por exemplo, quando objetos são filhos de objetos dimensionados.</span><span class="sxs-lookup"><span data-stu-id="bba09-125">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="bba09-126">No cenário acima, o RoverExplorer é posicionado 2 metros na frente e 0,6 metros abaixo da cabeça do usuário.</span><span class="sxs-lookup"><span data-stu-id="bba09-126">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="bba09-127">Como adicionar os pré-fabricados do tutorial</span><span class="sxs-lookup"><span data-stu-id="bba09-127">Adding the tutorial prefabs</span></span>

<span data-ttu-id="bba09-128">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados**:</span><span class="sxs-lookup"><span data-stu-id="bba09-128">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Janela Projeto do Unity com a pasta Pré-fabricados selecionada](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="bba09-130">Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um GameObject pré-configurado armazenado como um Ativo Unitário e pode ser reutilizado em todo o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="bba09-130">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="bba09-131">Na janela Projeto, clique e arraste o pré-fabricado **Tabela** no objeto **RoverExplorer** para torná-la um filho do objeto RoverExplorer e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bba09-131">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="bba09-132">**Posição**: X = 0, Y = -0,005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bba09-132">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="bba09-133">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bba09-133">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="bba09-134">**Escala**: X = 1,2, Y = 0,01, Z = 1,2</span><span class="sxs-lookup"><span data-stu-id="bba09-134">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity com o pré-fabricado Tabela recém-adicionado selecionado e posicionado](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="bba09-136">Para exibir a cena conforme mostrado na imagem acima use o <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Utensílio de Cena</a>, localizado no canto superior direito da janela Cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço, clique duas vezes no objeto MixedRealityPlayspace para colocá-lo em foco na câmera e amplie se necessário.</span><span class="sxs-lookup"><span data-stu-id="bba09-136">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="bba09-137">Na janela Projeto, clique e arraste o pré-fabricado **RoverAssembly** para o objeto **RoverExplorer** para torná-lo um filho do objeto RoverExplorer e, em seguida, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bba09-137">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="bba09-138">**Posição**: X = -0,1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bba09-138">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="bba09-139">**Rotação**: X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bba09-139">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="bba09-140">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="bba09-140">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o pré-fabricado RoverAssembly recém-adicionado selecionado e posicionado](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="bba09-142">Como organizar objetos em uma coleção</span><span class="sxs-lookup"><span data-stu-id="bba09-142">Organizing objects in a collection</span></span>

<span data-ttu-id="bba09-143">Na janela Hierarquia, clique com o botão direito do mouse no objeto **RoverExplorer** e selecione **Criar Vazio** para adicionar um objeto vazio como um filho do RoverExplorer, nomeie o objeto **RoverParts** e configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bba09-143">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="bba09-144">**Posição**: X = 0, Y = 0,06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bba09-144">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="bba09-145">**Rotação**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="bba09-145">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="bba09-146">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="bba09-146">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o objeto RoverParts recém-criado selecionado e posicionado](images/mr-learning-base/base-04-section3-step1-1.png)

<span data-ttu-id="bba09-148">Na janela Hierarquia, selecione todos os objetos filhos em RoverExplorer > RoverAssembly > RoverModel > **Parts** clique com o botão direito do mouse neles e selecione **Duplicar** para criar uma cópia de cada uma das peças:</span><span class="sxs-lookup"><span data-stu-id="bba09-148">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity com todas as Peças selecionadas e o menu pop-up contextual Duplicar](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="bba09-150">Para selecionar vários objetos adjacentes, pressione e segure a tecla SHIFT enquanto usa o mouse para selecionar o primeiro e o último objeto.</span><span class="sxs-lookup"><span data-stu-id="bba09-150">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="bba09-151">Com os objetos filho de Peças recentemente duplicados ainda selecionados, clique e arraste-os para o objeto **RoverParts** para torná-los objetos filho do objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="bba09-151">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity com as peças recém-duplicadas como filhos do objeto RoverParts](images/mr-learning-base/base-04-section3-step1-3.png)

<span data-ttu-id="bba09-153">Para facilitar o trabalho com a sua cena, na janela Hierarquia, clique no ícone de **olho** à esquerda do objeto para desativar a **visibilidade da cena** para o objeto **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="bba09-153">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="bba09-154">Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo:</span><span class="sxs-lookup"><span data-stu-id="bba09-154">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity com a visibilidade de cena do RoverAssembly desativada](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> <span data-ttu-id="bba09-156">Para saber mais sobre os controles de Visibilidade da Cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="bba09-156">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="bba09-157">Na janela Hierarquia, limpe os nomes dos objetos filho RoverParts substituindo o **(1)** acrescentado por **_Part**:</span><span class="sxs-lookup"><span data-stu-id="bba09-157">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity com o nome de peças duplicadas limpo](images/mr-learning-base/base-04-section3-step1-5.png)

<span data-ttu-id="bba09-159">Na janela Hierarquia, selecione o objeto **RoverParts** e, em seguida, na janela Inspetor, clique no botão **Adicionar Componente** e pesquise e selecione **GridObjectCollection** para adicionar o componente GridObjectCollection ao objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="bba09-159">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Objeto RoverParts do Unity com a Adição de Coleção de Objetos de Grade de Componentes em andamento](images/mr-learning-base/base-04-section3-step1-6.png)

<span data-ttu-id="bba09-161">Configure os valores de componente **GridObjectCollection** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="bba09-161">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="bba09-162">**Tipo de Classificação**: Alfabético</span><span class="sxs-lookup"><span data-stu-id="bba09-162">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="bba09-163">**Layout**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="bba09-163">**Layout**: Horizontal</span></span>
* <span data-ttu-id="bba09-164">**Largura da Célula**: 0,25</span><span class="sxs-lookup"><span data-stu-id="bba09-164">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="bba09-165">**Distância do pai**: 0,38</span><span class="sxs-lookup"><span data-stu-id="bba09-165">**Distance from parent**: 0.38</span></span>

![Unity com o componente GridObjectCollection configurado](images/mr-learning-base/base-04-section3-step1-7.png)

<span data-ttu-id="bba09-167">Em seguida, clique no botão **Atualizar Coleção** para atualizar a posição dos objetos filho RoverParts:</span><span class="sxs-lookup"><span data-stu-id="bba09-167">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity com o componente GridObjectCollection aplicado](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="bba09-169">Parabéns</span><span class="sxs-lookup"><span data-stu-id="bba09-169">Congratulations</span></span>

<span data-ttu-id="bba09-170">Neste tutorial, você aprendeu a posicionar objetos na cena em relação ao usuário e a usar o recurso Coleção de Objetos de Grade do MRTK para organizar objetos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="bba09-170">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="bba09-171">Próximo tutorial: 5. Criar conteúdo dinâmico usando Solucionadores</span><span class="sxs-lookup"><span data-stu-id="bba09-171">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
