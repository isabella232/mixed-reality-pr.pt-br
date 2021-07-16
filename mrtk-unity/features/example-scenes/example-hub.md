---
title: Hub de exemplos do MRTK
description: Visão geral sobre cenas de exemplo no MRTK
author: polar-kev
ms.author: kesemple
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: b7a55e46b2c283b5a75395b9e99874af6020a171
ms.sourcegitcommit: 912fa204ef79e9b973eab9b862846ba5ed5cd69f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282002"
---
# <a name="mrtk-examples-hub"></a><span data-ttu-id="c57e3-104">Hub de exemplos do MRTK</span><span class="sxs-lookup"><span data-stu-id="c57e3-104">MRTK Examples Hub</span></span>

![Hub de exemplos do MRTK](../images/examples-hub/MRTK_ExamplesHub.png)

<span data-ttu-id="c57e3-106">O Hub de Exemplos do MRTK é uma cena do Unity que facilita a experiência de várias cenas.</span><span class="sxs-lookup"><span data-stu-id="c57e3-106">MRTK Examples Hub is a Unity scene that makes it easy to experience multiple scenes.</span></span> <span data-ttu-id="c57e3-107">Ele usa o Sistema de Cena do MRTK para carregar & descarregar as cenas.</span><span class="sxs-lookup"><span data-stu-id="c57e3-107">It uses MRTK's Scene System to load & unload the scenes.</span></span>

<span data-ttu-id="c57e3-108">**MRTKExamplesHub.unity é** a cena de contêiner que tem componentes compartilhados, incluindo ``MixedRealityToolkit`` e ``MixedRealityPlayspace`` .</span><span class="sxs-lookup"><span data-stu-id="c57e3-108">**MRTKExamplesHub.unity** is the container scene that has shared components including ``MixedRealityToolkit`` and ``MixedRealityPlayspace``.</span></span> <span data-ttu-id="c57e3-109">**A cena MRTKExamplesHubMainMenu.unity** tem os botões de cubo.</span><span class="sxs-lookup"><span data-stu-id="c57e3-109">**MRTKExamplesHubMainMenu.unity** scene has the cube buttons.</span></span>

## <a name="prerequisite"></a><span data-ttu-id="c57e3-110">Pré-requisito</span><span class="sxs-lookup"><span data-stu-id="c57e3-110">Prerequisite</span></span>

<span data-ttu-id="c57e3-111">O Hub de Exemplos do MRTK usa [o Serviço de Transição de Cena](../extensions/scene-transition-service.md) e scripts relacionados.</span><span class="sxs-lookup"><span data-stu-id="c57e3-111">MRTK Examples Hub uses [Scene Transition Service](../extensions/scene-transition-service.md) and related scripts.</span></span> <span data-ttu-id="c57e3-112">Se você estiver usando o MRTK por meio de pacotes do Unity, importe **Microsoft.MixedReality.Toolkit. Unity.Extensions.x.x.x.unitypackage** que faz parte dos pacotes [de lançamento.](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="c57e3-112">If you are using MRTK through Unity packages, please import **Microsoft.MixedReality.Toolkit.Unity.Extensions.x.x.x.unitypackage** which is part of the [release packages](https://github.com/microsoft/MixedRealityToolkit-Unity/releases).</span></span> <span data-ttu-id="c57e3-113">Se você estiver usando o MRTK por meio do clone do repositório, já deverá ter a pasta **MRTK/Extensões** em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="c57e3-113">If you are using MRTK through the repository clone, you should already have the **MRTK/Extensions** folder in your project.</span></span>

## <a name="mrtkexampleshub-scene-and-the-scene-system"></a><span data-ttu-id="c57e3-114">MRTKExamples Cena doHub e o sistema de cena</span><span class="sxs-lookup"><span data-stu-id="c57e3-114">MRTKExamplesHub scene and the scene system</span></span>

<span data-ttu-id="c57e3-115">Abra **MRTKExamplesHub.unity,** que está localizado em É uma cena vazia com `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` MixedRealityToolkit, MixedRealityPlayspace e LoadHubOnStartup.</span><span class="sxs-lookup"><span data-stu-id="c57e3-115">Open **MRTKExamplesHub.unity** which is located at `MRTK/Examples/Experimental/Demos/ExamplesHub/Scenes/` It is an empty scene with MixedRealityToolkit, MixedRealityPlayspace and LoadHubOnStartup.</span></span> <span data-ttu-id="c57e3-116">Esta cena está configurada para usar o Sistema de Cena do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c57e3-116">This scene is configured to use MRTK's Scene System.</span></span> <span data-ttu-id="c57e3-117">Clique `MixedRealitySceneSystem` em MixedRealityToolkit.</span><span class="sxs-lookup"><span data-stu-id="c57e3-117">Click `MixedRealitySceneSystem` under MixedRealityToolkit.</span></span> <span data-ttu-id="c57e3-118">Ele exibirá as informações do Sistema de Cena no painel Inspetor.</span><span class="sxs-lookup"><span data-stu-id="c57e3-118">It will display the Scene System's information in the Inspector panel.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Hierarchy.png" width="300" alt="Example Hub Hierarchy">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector1.png" width="450" alt="Inspector 1">

<span data-ttu-id="c57e3-119">Na parte inferior do Inspetor, ele exibe a lista das cenas definidas no Perfil do Sistema de Cena.</span><span class="sxs-lookup"><span data-stu-id="c57e3-119">On the bottom of the Inspector, it displays the list of the scenes defined in the Scene System Profile.</span></span> <span data-ttu-id="c57e3-120">Você pode clicar nos nomes de cena para carregá-los/descarregá-los.</span><span class="sxs-lookup"><span data-stu-id="c57e3-120">You can click the scene names to load/unload them.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_Inspector2.png" width="550" alt="Inspector 2">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem3.png" alt="Scene system 3"><span data-ttu-id="c57e3-121">Exemplo de carregamento _da cena MRTKExamplesHub_ clicando no nome da cena na lista.</span><span class="sxs-lookup"><span data-stu-id="c57e3-121">Example of loading _MRTKExamplesHub_ scene by clicking the scene name in the list.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem4.png" alt="Scene system 4"><span data-ttu-id="c57e3-122">Exemplo de carregamento _da cena HandInteractionExamples._</span><span class="sxs-lookup"><span data-stu-id="c57e3-122">Example of loading _HandInteractionExamples_ scene.</span></span>
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem5.png" alt="Scene system 5">
<span data-ttu-id="c57e3-123">Exemplo de carregamento de várias cenas.</span><span class="sxs-lookup"><span data-stu-id="c57e3-123">Example of loading multiple scenes.</span></span>

## <a name="running-the-scene"></a><span data-ttu-id="c57e3-124">Executando a cena</span><span class="sxs-lookup"><span data-stu-id="c57e3-124">Running the scene</span></span>

<span data-ttu-id="c57e3-125">A cena funciona no modo de jogo do Unity e no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="c57e3-125">The scene works in both Unity's game mode and on device.</span></span> <span data-ttu-id="c57e3-126">Execute a **cena MRTKExamplesHub** no editor do Unity e use a simulação de entrada do MRTK para interagir com o conteúdo da cena.</span><span class="sxs-lookup"><span data-stu-id="c57e3-126">Run the **MRTKExamplesHub** scene in the Unity editor and use MRTK's input simulation to interact with the scene contents.</span></span> <span data-ttu-id="c57e3-127">Para criar e implantar, basta criar a cena **MRTKExamplesHub** com outras cenas incluídas na lista do Sistema de Cena.</span><span class="sxs-lookup"><span data-stu-id="c57e3-127">To build and deploy, simply build **MRTKExamplesHub** scene with other scenes that are included in the Scene System's list.</span></span> <span data-ttu-id="c57e3-128">O inspetor também facilita adicionar cenas ao build Configurações.</span><span class="sxs-lookup"><span data-stu-id="c57e3-128">The inspector also makes it easy to add scenes to the Build Settings.</span></span> <span data-ttu-id="c57e3-129">Na cena Configurações, certifique-se de que **MRTKExamplesHub** está na parte superior da lista no índice 0.</span><span class="sxs-lookup"><span data-stu-id="c57e3-129">In the Building Settings, make sure **MRTKExamplesHub** scene is on the top of the list at index 0.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHub_BuildSettings.png" width="450" alt="Build settings">

## <a name="how-mrtkexampleshub-loads-a-scene"></a><span data-ttu-id="c57e3-130">Como MRTKExamplesHub carrega uma cena</span><span class="sxs-lookup"><span data-stu-id="c57e3-130">How MRTKExamplesHub loads a scene</span></span>

<span data-ttu-id="c57e3-131">Na cena **MRTKExamplesHub,** você pode encontrar o ``ExamplesHubButton`` pré-fab.</span><span class="sxs-lookup"><span data-stu-id="c57e3-131">In the **MRTKExamplesHub** scene, you can find the ``ExamplesHubButton`` prefab.</span></span>
<span data-ttu-id="c57e3-132">Há um **objeto FrontPlate** no pré-fab que contém ``Interactable`` .</span><span class="sxs-lookup"><span data-stu-id="c57e3-132">There is a **FrontPlate** object in the prefab which contains ``Interactable``.</span></span>
<span data-ttu-id="c57e3-133">Usando o e o evento Interactable, ele dispara a função ``OnClick()`` ``OnTouch()`` **LoadContentScene** do script **LoadContent().**</span><span class="sxs-lookup"><span data-stu-id="c57e3-133">Using the Interactable's ``OnClick()`` and ``OnTouch()`` event, it triggers the **LoadContentScene** script's **LoadContent()** function.</span></span>
<span data-ttu-id="c57e3-134">No Inspetor do script **LoadContentScene,** você pode definir o nome da cena a ser carregada.</span><span class="sxs-lookup"><span data-stu-id="c57e3-134">In the **LoadContentScene** script's Inspector, you can define the scene name to load.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem6.png" alt="Scene system 6">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem8.png" width="450" alt="Scene System 8">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem7.png" width="450" alt="Scene System 7">

<span data-ttu-id="c57e3-135">O script usa a função LoadContent() do Sistema de Cena para carregar a cena.</span><span class="sxs-lookup"><span data-stu-id="c57e3-135">The script uses the Scene System's LoadContent() function to load the scene.</span></span>
<span data-ttu-id="c57e3-136">Consulte a página Sistema [de Cena](../scene-system/scene-system-getting-started.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="c57e3-136">Please refer to the [Scene System](../scene-system/scene-system-getting-started.md) page for more details.</span></span>

```c#
MixedRealityToolkit.SceneSystem.LoadContent(contentName, loadSceneMode);
```

## <a name="returning-to-the-main-menu-scene"></a><span data-ttu-id="c57e3-137">Retornando à cena do menu principal</span><span class="sxs-lookup"><span data-stu-id="c57e3-137">Returning to the main menu scene</span></span>

<span data-ttu-id="c57e3-138">Para retornar à cena do menu principal (cena MRTKExamplesHubMainMenu), você pode usar o mesmo método sistema de `LoadContent()` cena.</span><span class="sxs-lookup"><span data-stu-id="c57e3-138">To return to the main menu scene (MRTKExamplesHubMainMenu scene), you can use the same Scene System `LoadContent()` method.</span></span> <span data-ttu-id="c57e3-139">O **ToggleFeaturesPanelExamplesHub.prefab** fornece o botão "Página Inicial", que contém o script **LoadContentScene.**</span><span class="sxs-lookup"><span data-stu-id="c57e3-139">The **ToggleFeaturesPanelExamplesHub.prefab** provides the 'Home' button which contains the **LoadContentScene** script.</span></span> <span data-ttu-id="c57e3-140">Use esse pré-fab ou forneça um botão home personalizado em cada cena para permitir que o usuário retorne à cena principal.</span><span class="sxs-lookup"><span data-stu-id="c57e3-140">Use this prefab or provide a custom home button in each scene to allow the user to return to the main scene.</span></span> <span data-ttu-id="c57e3-141">É possível colocar **ToggleFeaturesPanelExamplesHub.prefab** na cena **MRTKExamplesHub** para torná-la sempre visível, pois **MRTKExamplesHub** é uma cena de contêiner compartilhado.</span><span class="sxs-lookup"><span data-stu-id="c57e3-141">One can put the **ToggleFeaturesPanelExamplesHub.prefab** in the **MRTKExamplesHub** scene to make it always visible since **MRTKExamplesHub** is a shared container scene.</span></span> <span data-ttu-id="c57e3-142">Certifique-se de ocultar/desativar **ToggleFeaturesPanel.prefab** em cada cena de exemplo.</span><span class="sxs-lookup"><span data-stu-id="c57e3-142">Make sure to hide/deactivate **ToggleFeaturesPanel.prefab** in each example scene.</span></span>

<img src="../images/examples-hub/MRTK_ExamplesHubToggleFeaturesPanel.png" alt="Toggle feature Panel">

<img src="../images/examples-hub/MRTK_ExamplesHubHomeButton.png" width="450" alt="Example Hub home button">

## <a name="adding-additional-buttons"></a><span data-ttu-id="c57e3-143">Adicionando botões adicionais</span><span class="sxs-lookup"><span data-stu-id="c57e3-143">Adding additional buttons</span></span>

<span data-ttu-id="c57e3-144">No objeto **CubeCollection,** duplique (ou adicione) os pré-fabs _ExampleHubButton_ e clique em Atualizar **Coleção** no `GridObjectCollection` .</span><span class="sxs-lookup"><span data-stu-id="c57e3-144">In the **CubeCollection** object, duplicate (or add) _ExampleHubButton_ prefabs and click **Update Collection** in the `GridObjectCollection`.</span></span>
<span data-ttu-id="c57e3-145">Isso atualizará o layout do cilindro com base no novo número total de botões.</span><span class="sxs-lookup"><span data-stu-id="c57e3-145">This will update the cylinder layout based on the new total number of buttons.</span></span>
<span data-ttu-id="c57e3-146">Consulte a página [Coleção de Objetos](../ux-building-blocks/object-collection.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="c57e3-146">Please refer to the [Object Collection](../ux-building-blocks/object-collection.md) page for more details.</span></span>

<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem9.png" alt="Scene System 9">
<br/><br/><img src="../images/examples-hub/MRTK_ExamplesHub_SceneSystem10.png" alt="Scene System 10">

<span data-ttu-id="c57e3-147">Depois de adicionar os botões, atualize o nome da cena no script **LoadContentScene** (explicado acima).</span><span class="sxs-lookup"><span data-stu-id="c57e3-147">After adding the buttons, update the scene name in the **LoadContentScene** script(explained above).</span></span>
<span data-ttu-id="c57e3-148">Adicione cenas adicionais ao perfil do Sistema de Cena.</span><span class="sxs-lookup"><span data-stu-id="c57e3-148">Add additional scenes to the Scene System's profile.</span></span>
