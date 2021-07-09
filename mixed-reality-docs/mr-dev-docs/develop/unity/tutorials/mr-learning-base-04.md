---
title: Tutoriais do MRTK – 4. Como posicionar objetos na cena
description: Este curso mostra como posicionar objetos na cena e como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para organizar objetos em uma grade.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, solucionadores, coleção de objetos de grade
ms.localizationpriority: high
ms.openlocfilehash: d5d10893ba8274139c6e09b8cd426d58a0b3a0cb
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175469"
---
# <a name="4-positioning-objects-in-the-scene"></a><span data-ttu-id="7fd97-105">4. Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="7fd97-105">4. Positioning objects in the scene</span></span>

## <a name="overview"></a><span data-ttu-id="7fd97-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="7fd97-106">Overview</span></span>

<span data-ttu-id="7fd97-107">Neste tutorial, você posicionará na cena os objetos fornecidos nos ativos.</span><span class="sxs-lookup"><span data-stu-id="7fd97-107">In this tutorial, you will position the provided objects from the tutorial assets in the scene.</span></span>

## <a name="objectives"></a><span data-ttu-id="7fd97-108">Objetivos</span><span class="sxs-lookup"><span data-stu-id="7fd97-108">Objectives</span></span>

* <span data-ttu-id="7fd97-109">Saiba como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="7fd97-109">Learn how to position objects in the scene</span></span>
* <span data-ttu-id="7fd97-110">Saiba como usar o recurso Coleção de Objetos de Grade do MRTK</span><span class="sxs-lookup"><span data-stu-id="7fd97-110">Learn how to use MRTK's Grid Object Collection feature</span></span>

## <a name="importing-the-textmeshpro-essential-resources"></a><span data-ttu-id="7fd97-111">Como importar os Recursos Essenciais do TextMeshPro</span><span class="sxs-lookup"><span data-stu-id="7fd97-111">Importing the TextMeshPro Essential Resources</span></span>
<span data-ttu-id="7fd97-112">Os Recursos Essenciais do TextMeshPro são exigidos pelos elementos da interface do usuário do MRTK.</span><span class="sxs-lookup"><span data-stu-id="7fd97-112">The TextMeshPro Essential Resources are required by MRTK's UI elements.</span></span> <span data-ttu-id="7fd97-113">No menu do Unity, selecione **Janela** > **TextMeshPro** > **Importar Recursos Essenciais do TMP** para abrir a janela Importar Pacote do Unity:</span><span class="sxs-lookup"><span data-stu-id="7fd97-113">In the Unity menu, select **Window** > **TextMeshPro** > **Import TMP Essential Resources** to open the Import Unity Package window:</span></span>

![Caminho do menu Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-1.png)

<span data-ttu-id="7fd97-115">Na janela Importar Pacote do Unity, clique no botão **Todos** para garantir que todos os ativos sejam selecionados e clique no botão **Importar** para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="7fd97-115">In the Import Unity Package window, click the **All** button to ensure all the assets are selected, then click the **Import** button to import the assets:</span></span>

![Janela Importar Recursos Essenciais do TMP do Unity](images/mr-learning-base/base-02-section3-step1-2.png)

## <a name="importing-the-tutorial-assets"></a><span data-ttu-id="7fd97-117">Como importar os ativos do tutorial</span><span class="sxs-lookup"><span data-stu-id="7fd97-117">Importing the tutorial assets</span></span>

<span data-ttu-id="7fd97-118">Faça o download do seguinte pacote personalizado do Unity.</span><span class="sxs-lookup"><span data-stu-id="7fd97-118">Download the following Unity custom package.</span></span> <span data-ttu-id="7fd97-119">Esse pacote inclui ativos 3D, como o Mars Rover que vamos usar neste tutorial.</span><span class="sxs-lookup"><span data-stu-id="7fd97-119">This package includes 3D assets such as Mars Rover that we are going to use in this tutorial.</span></span>

* [<span data-ttu-id="7fd97-120">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span><span class="sxs-lookup"><span data-stu-id="7fd97-120">MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage</span></span>](https://github.com/microsoft/MixedRealityLearning/releases/download/getting-started-v2.5.0/MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage)

<span data-ttu-id="7fd97-121">Para importar um pacote personalizado do Unity, no menu do Unity selecione **Ativos** > **Importar Pacote** > **Pacote Personalizado...** para abrir a janela Importar pacote...:</span><span class="sxs-lookup"><span data-stu-id="7fd97-121">To Import a Unity custom package, In the Unity menu, select **Assets** > **Import Package** > **Custom Package...** to open the Import package... window:</span></span>

![Como importar um pacote personalizado](images/mr-learning-base/base-02-section7-step1-1.png)

<span data-ttu-id="7fd97-123">Na janela Importar Pacote..., selecione o **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** que você baixou e clique no botão Abrir:</span><span class="sxs-lookup"><span data-stu-id="7fd97-123">In the Import package... window, select the **MRTK.HoloLens2.Unity.Tutorials.Assets.GettingStarted.2.5.0.1.unitypackage** you downloaded and click the Open button:</span></span>

![Como selecionar um pacote de ativos](images/mr-learning-base/base-02-section7-step1-2.png)

<span data-ttu-id="7fd97-125">Na janela Importar Pacote do Unity, clique no botão Todos para garantir que todos os ativos sejam selecionados e clique no botão Importar para importar os ativos:</span><span class="sxs-lookup"><span data-stu-id="7fd97-125">In the Import Unity Package window, click the All button to ensure all the assets are selected, then click the Import button to import the assets:</span></span>

![Como selecionar todos os ativos a serem importados](images/mr-learning-base/base-02-section7-step1-3.png)

<span data-ttu-id="7fd97-127">Depois de importar os ativos do tutorial, a janela do projeto deverá ser semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="7fd97-127">After you have imported the tutorial assets your Project window should look similar to this:</span></span>

![Janela de projeto do Unity após importar os ativos](images/mr-learning-base/base-02-section7-step1-4.png)

## <a name="creating-the-parent-object"></a><span data-ttu-id="7fd97-129">Como criar um objeto pai</span><span class="sxs-lookup"><span data-stu-id="7fd97-129">Creating the parent object</span></span>

<span data-ttu-id="7fd97-130">Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Criar Vazio** para adicionar um objeto vazio à sua cena:</span><span class="sxs-lookup"><span data-stu-id="7fd97-130">In the Hierarchy window, right-click on an empty spot, and select **Create Empty** to add an empty object to your scene:</span></span>

![Menu pop-up contextual Criar Vazio do Unity](images/mr-learning-base/base-04-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="7fd97-132">Para exibir a janela Cena e Jogo lado a lado como mostra a imagem acima, arraste a janela Jogo para o lado direito da janela Cena.</span><span class="sxs-lookup"><span data-stu-id="7fd97-132">To display your Scene and Game window side by side as shown in the image above, drag the Game window to the right side of the Scene window.</span></span> <span data-ttu-id="7fd97-133">Para saber mais sobre como personalizar o seu workspace, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Como personalizar o seu workspace</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="7fd97-133">To learn more about customizing your workspace, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/CustomizingYourWorkspace.html" target="_blank">Customizing Your Workspace</a> documentation.</span></span>

<span data-ttu-id="7fd97-134">Clique com o botão direito do mouse no objeto recém-criado, selecione **Renomear** e altere o nome para **RoverExplorer**:</span><span class="sxs-lookup"><span data-stu-id="7fd97-134">Right-click on the newly created object, select **Rename**, and change the name to **RoverExplorer**:</span></span>

![Menu pop-up contextual Renomear do Unity](images/mr-learning-base/base-04-section1-step1-2.png)

<span data-ttu-id="7fd97-136">Com o objeto RoverExplorer ainda selecionado, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="7fd97-136">With the RoverExplorer object still selected, in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="7fd97-137">**Posição**: X = 0, Y = -0,6, Z = 2</span><span class="sxs-lookup"><span data-stu-id="7fd97-137">**Position**: X = 0, Y = -0.6, Z = 2</span></span>
* <span data-ttu-id="7fd97-138">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="7fd97-138">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="7fd97-139">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="7fd97-139">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o objeto RoverExplorer selecionado e posicionado](images/mr-learning-base/base-04-section1-step1-3.png)

> [!NOTE]
> <span data-ttu-id="7fd97-141">A câmera representa a cabeça do usuário e é posicionada na origem, X = 0, Y = 0, Z = 0.</span><span class="sxs-lookup"><span data-stu-id="7fd97-141">The camera represents the users head and is positioned at origin, X = 0, Y = 0, Z = 0.</span></span> <span data-ttu-id="7fd97-142">Em geral, uma unidade no Unity corresponde a aproximadamente um metro no mundo físico.</span><span class="sxs-lookup"><span data-stu-id="7fd97-142">In general, 1 unit in Unity is roughly 1 meter in the physical world.</span></span> <span data-ttu-id="7fd97-143">Porém, há exceções, por exemplo, quando objetos são filhos de objetos dimensionados.</span><span class="sxs-lookup"><span data-stu-id="7fd97-143">However, there are exceptions to this, for example, when objects are children of scaled objects.</span></span> <span data-ttu-id="7fd97-144">No cenário acima, o RoverExplorer é posicionado 2 metros na frente e 0,6 metros abaixo da cabeça do usuário.</span><span class="sxs-lookup"><span data-stu-id="7fd97-144">In the scenario above, the RoverExplorer is positioned 2 meters in front of and 0.6 meters below the user's head.</span></span>

## <a name="adding-the-tutorial-prefabs"></a><span data-ttu-id="7fd97-145">Como adicionar os pré-fabricados do tutorial</span><span class="sxs-lookup"><span data-stu-id="7fd97-145">Adding the tutorial prefabs</span></span>

<span data-ttu-id="7fd97-146">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK.Tutorials.GettingStarted** > **Pré-fabricados**:</span><span class="sxs-lookup"><span data-stu-id="7fd97-146">In the Project window, navigate to the **Assets** > **MRTK.Tutorials.GettingStarted** > **Prefabs** folder:</span></span>

![Janela Projeto do Unity com a pasta Pré-fabricados selecionada](images/mr-learning-base/base-04-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="7fd97-148">Um <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">pré-fabricado</a> é um GameObject pré-configurado armazenado como um Ativo Unitário e pode ser reutilizado em todo o seu projeto.</span><span class="sxs-lookup"><span data-stu-id="7fd97-148">A <a href="https://docs.unity3d.com/Manual/Prefabs.html" target="_blank">prefab</a> is a pre-configured GameObject stored as a Unity Asset and can be reused throughout your project.</span></span>

<span data-ttu-id="7fd97-149">Na janela Projeto, clique e arraste o pré-fabricado **Tabela** no objeto **RoverExplorer** para torná-la um filho do objeto RoverExplorer e, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="7fd97-149">From the Project window, click-and-drag the **Table** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="7fd97-150">**Posição**: X = 0, Y = -0,005, Z = 0</span><span class="sxs-lookup"><span data-stu-id="7fd97-150">**Position**: X = 0, Y = -0.005, Z = 0</span></span>
* <span data-ttu-id="7fd97-151">**Rotação**: X = 0, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="7fd97-151">**Rotation**: X = 0, Y = 0, Z = 0</span></span>
* <span data-ttu-id="7fd97-152">**Escala**: X = 1,2, Y = 0,01, Z = 1,2</span><span class="sxs-lookup"><span data-stu-id="7fd97-152">**Scale**: X = 1.2, Y = 0.01, Z = 1.2</span></span>

![Unity com o pré-fabricado Tabela recém-adicionado selecionado e posicionado](images/mr-learning-base/base-04-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="7fd97-154">Para exibir a cena conforme mostrado na imagem acima use o <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Utensílio de Cena</a>, localizado no canto superior direito da janela Cena, para ajustar o ângulo de exibição ao longo do eixo Z de avanço, clique duas vezes no objeto MixedRealityPlayspace para colocá-lo em foco na câmera e amplie se necessário.</span><span class="sxs-lookup"><span data-stu-id="7fd97-154">To display your scene as shown in the image above, use the <a href="https://docs.unity3d.com/Manual/SceneViewNavigation.html" target="_blank">Scene Gizmo</a>, located in the top right corner of the Scene window, to adjust the viewing angle to be along the forward Z axis, double-click the MixedRealityPlayspace object to focus on the camera, and zoom in as needed.</span></span>

<span data-ttu-id="7fd97-155">Na janela Projeto, clique e arraste o pré-fabricado **RoverAssembly** para o objeto **RoverExplorer** para torná-lo um filho do objeto RoverExplorer e, em seguida, na janela Inspetor, configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="7fd97-155">From the Project window, click-and-drag the **RoverAssembly** prefab on to the **RoverExplorer** object to make it a child of the RoverExplorer object, then in the Inspector window, configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="7fd97-156">**Posição**: X = -0,1, Y = 0, Z = 0</span><span class="sxs-lookup"><span data-stu-id="7fd97-156">**Position**: X = -0.1, Y = 0, Z = 0</span></span>
* <span data-ttu-id="7fd97-157">**Rotação**: X = 0, Y = -135, Z = 0</span><span class="sxs-lookup"><span data-stu-id="7fd97-157">**Rotation**: X = 0, Y = -135, Z = 0</span></span>
* <span data-ttu-id="7fd97-158">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="7fd97-158">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o pré-fabricado RoverAssembly recém-adicionado selecionado e posicionado](images/mr-learning-base/base-04-section2-step1-3.png)

## <a name="organizing-objects-in-a-collection"></a><span data-ttu-id="7fd97-160">Como organizar objetos em uma coleção</span><span class="sxs-lookup"><span data-stu-id="7fd97-160">Organizing objects in a collection</span></span>

<span data-ttu-id="7fd97-161">Na janela Hierarquia, clique com o botão direito do mouse no objeto **RoverExplorer** e selecione **Criar Vazio** para adicionar um objeto vazio como um filho do RoverExplorer, nomeie o objeto **RoverParts** e configure o componente **Transformar** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="7fd97-161">In the Hierarchy window, right-click on the **RoverExplorer** object and select **Create Empty** to add an empty object as a child of the RoverExplorer, name the object **RoverParts**, and configure the **Transform** component as follows:</span></span>

* <span data-ttu-id="7fd97-162">**Posição**: X = 0, Y = 0,06, Z = 0</span><span class="sxs-lookup"><span data-stu-id="7fd97-162">**Position**: X = 0, Y = 0.06, Z = 0</span></span>
* <span data-ttu-id="7fd97-163">**Rotação**: X = 0, Y = 90, Z = 0</span><span class="sxs-lookup"><span data-stu-id="7fd97-163">**Rotation**: X = 0, Y = 90, Z = 0</span></span>
* <span data-ttu-id="7fd97-164">**Escala**: X = 1, Y = 1, Z = 1</span><span class="sxs-lookup"><span data-stu-id="7fd97-164">**Scale**: X = 1, Y = 1, Z = 1</span></span>

![Unity com o objeto RoverParts recém-criado selecionado e posicionado](images/mr-learning-base/base-04-section3-step1-1.png)

<span data-ttu-id="7fd97-166">Na janela Hierarquia, selecione todos os objetos filhos em RoverExplorer > RoverAssembly > RoverModel > **Parts** clique com o botão direito do mouse neles e selecione **Duplicar** para criar uma cópia de cada uma das peças:</span><span class="sxs-lookup"><span data-stu-id="7fd97-166">In the Hierarchy window, select all the RoverExplorer > RoverAssembly > RoverModel > **Parts** child objects, right-click on them and select **Duplicate** to create a copy of each of the parts:</span></span>

![Unity com todas as Peças selecionadas e o menu pop-up contextual Duplicar](images/mr-learning-base/base-04-section3-step1-2.png)

> [!TIP]
> <span data-ttu-id="7fd97-168">Para selecionar vários objetos adjacentes, pressione e segure a tecla SHIFT enquanto usa o mouse para selecionar o primeiro e o último objeto.</span><span class="sxs-lookup"><span data-stu-id="7fd97-168">To select multiple adjacent objects, press-and-hold the SHIFT key while using the mouse to select the first and last object.</span></span>

<span data-ttu-id="7fd97-169">Com os objetos filho de Peças recentemente duplicados ainda selecionados, clique e arraste-os para o objeto **RoverParts** para torná-los objetos filho do objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="7fd97-169">With the newly duplicated Parts child objects still selected, click-and-drag them on to the **RoverParts** object to make them child objects of the RoverParts object:</span></span>

![Unity com as peças recém-duplicadas como filhos do objeto RoverParts](images/mr-learning-base/base-04-section3-step1-3.png)

<span data-ttu-id="7fd97-171">Para facilitar o trabalho com a sua cena, na janela Hierarquia, clique no ícone de **olho** à esquerda do objeto para desativar a **visibilidade da cena** para o objeto **RoverAssembly**.</span><span class="sxs-lookup"><span data-stu-id="7fd97-171">To make it easier to work with your scene, in the Hierarchy window, click the **eye** icon to the left of the object to toggle the **scene visibility** for the **RoverAssembly** object off.</span></span> <span data-ttu-id="7fd97-172">Isso oculta o objeto na janela Cena sem alterar a visibilidade no jogo:</span><span class="sxs-lookup"><span data-stu-id="7fd97-172">This hides the object in the Scene window without changing its in-game visibility:</span></span>

![Unity com a visibilidade de cena do RoverAssembly desativada](images/mr-learning-base/base-04-section3-step1-4.png)

> [!TIP]
> <span data-ttu-id="7fd97-174">Para saber mais sobre os controles de Visibilidade da Cena e como usá-los para otimizar o fluxo de trabalho e a exibição de cena, você pode consultar a documentação <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Visibilidade da Cena</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="7fd97-174">To learn more about the Scene Visibility controls and how you can use them to optimize your scene view and workflow, you can refer to Unity's <a href="https://docs.unity3d.com/Manual/SceneVisibility.html" target="_blank">Scene Visibility</a> documentation.</span></span>

<span data-ttu-id="7fd97-175">Na janela Hierarquia, limpe os nomes dos objetos filho RoverParts substituindo o **(1)** acrescentado por **_Part**:</span><span class="sxs-lookup"><span data-stu-id="7fd97-175">In the Hierarchy window, clean up the RoverParts child objects' names by replacing the appended **(1)** with **_Part**:</span></span>

![Unity com o nome de peças duplicadas limpo](images/mr-learning-base/base-04-section3-step1-5.png)

<span data-ttu-id="7fd97-177">Na janela Hierarquia, selecione o objeto **RoverParts** e, em seguida, na janela Inspetor, clique no botão **Adicionar Componente** e pesquise e selecione **GridObjectCollection** para adicionar o componente GridObjectCollection ao objeto RoverParts:</span><span class="sxs-lookup"><span data-stu-id="7fd97-177">In the Hierarchy window, select the **RoverParts** object, then in the Inspector window, click the **Add Component** button, and search for and select **GridObjectCollection** to add the GridObjectCollection component to the RoverParts object:</span></span>

![Objeto RoverParts do Unity com a Adição de Coleção de Objetos de Grade de Componentes em andamento](images/mr-learning-base/base-04-section3-step1-6.png)

<span data-ttu-id="7fd97-179">Configure os valores de componente **GridObjectCollection** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="7fd97-179">Configure the **GridObjectCollection** component values as follows:</span></span>

* <span data-ttu-id="7fd97-180">**Tipo de Classificação**: Alfabético</span><span class="sxs-lookup"><span data-stu-id="7fd97-180">**Sort Type**: Alphabetic</span></span>
* <span data-ttu-id="7fd97-181">**Layout**: Horizontal</span><span class="sxs-lookup"><span data-stu-id="7fd97-181">**Layout**: Horizontal</span></span>
* <span data-ttu-id="7fd97-182">**Largura da Célula**: 0,25</span><span class="sxs-lookup"><span data-stu-id="7fd97-182">**Cell Width**: 0.25</span></span>
* <span data-ttu-id="7fd97-183">**Distância do pai**: 0,38</span><span class="sxs-lookup"><span data-stu-id="7fd97-183">**Distance from parent**: 0.38</span></span>

![Unity com o componente GridObjectCollection configurado](images/mr-learning-base/base-04-section3-step1-7.png)

<span data-ttu-id="7fd97-185">Em seguida, clique no botão **Atualizar Coleção** para atualizar a posição dos objetos filho RoverParts:</span><span class="sxs-lookup"><span data-stu-id="7fd97-185">Then click the **Update Collection** button to update the position of the RoverParts child objects:</span></span>

![Unity com o componente GridObjectCollection aplicado](images/mr-learning-base/base-04-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="7fd97-187">Parabéns</span><span class="sxs-lookup"><span data-stu-id="7fd97-187">Congratulations</span></span>

<span data-ttu-id="7fd97-188">Neste tutorial, você aprendeu a posicionar objetos na cena em relação ao usuário e a usar o recurso Coleção de Objetos de Grade do MRTK para organizar objetos em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="7fd97-188">In this tutorial, you learned how to position objects in the scene relative to the user and use MRTK's Grid Object Collection feature to organize objects in a collection.</span></span>

> [!div class="nextstepaction"]
>[<span data-ttu-id="7fd97-189">Próximo tutorial: 5. Criar conteúdo dinâmico usando Solucionadores</span><span class="sxs-lookup"><span data-stu-id="7fd97-189">Next Tutorial: 5. Creating dynamic content using Solvers</span></span>](mr-learning-base-05.md)
