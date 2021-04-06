---
title: Como interagir com objetos 3D
description: Este curso mostra como usar o MRTK (Kit de Ferramentas de Realidade Misturada) para manipular objetos 3D em aplicativos de realidade misturada e interagir com eles.
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, interações de objetos, Controles de Limites
ms.localizationpriority: high
ms.openlocfilehash: c2cca67afe19665ea899eb56140011bd9c756a7f
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982859"
---
# <a name="7-interacting-with-3d-objects"></a><span data-ttu-id="db98b-104">7. Como interagir com objetos 3D</span><span class="sxs-lookup"><span data-stu-id="db98b-104">7. Interacting with 3D objects</span></span>

<span data-ttu-id="db98b-105">Neste tutorial, você aprenderá a habilitar a manipulação próxima e distante de objetos 3D e limitar os tipos de manipulação permitidos.</span><span class="sxs-lookup"><span data-stu-id="db98b-105">In this tutorial, you will learn how to enable near and far manipulation of 3D objects and limit the allowed types of manipulation.</span></span> <span data-ttu-id="db98b-106">Você também aprenderá a adicionar o controle de limites em objetos 3D para facilitar o controle da manipulação de objetos.</span><span class="sxs-lookup"><span data-stu-id="db98b-106">You will also learn how to add bounds control around 3D objects to make it easier to control the object manipulation.</span></span>

## <a name="objectives"></a><span data-ttu-id="db98b-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="db98b-107">Objectives</span></span>

* <span data-ttu-id="db98b-108">Saber como configurar objetos 3D para interagir com eles</span><span class="sxs-lookup"><span data-stu-id="db98b-108">Learn how to configure 3D objects so they can be interacted with</span></span>
* <span data-ttu-id="db98b-109">Saiba como adicionar o controle de limites em objetos 3D</span><span class="sxs-lookup"><span data-stu-id="db98b-109">Learn how to add bounds control to 3D objects</span></span>

## <a name="manipulating-3d-objects"></a><span data-ttu-id="db98b-110">Como manipular objetos 3D</span><span class="sxs-lookup"><span data-stu-id="db98b-110">Manipulating 3D objects</span></span>

<span data-ttu-id="db98b-111">Nesta seção, você adicionará a capacidade de manipular todas as peças do Rover organizadas na tabela durante o tutorial [Como posicionar objetos na cena](mr-learning-base-04.md).</span><span class="sxs-lookup"><span data-stu-id="db98b-111">In this section, you will add the ability to manipulate all the Rover parts you organized on the table during the [Positioning objects in the scene](mr-learning-base-04.md) tutorial.</span></span>

<span data-ttu-id="db98b-112">As principais etapas que você seguirá para conseguir isso são:</span><span class="sxs-lookup"><span data-stu-id="db98b-112">The main steps you will take to achieve this are:</span></span>

1. <span data-ttu-id="db98b-113">Adicionar o componente Object Manipulator (Script) a todos os objetos de peças</span><span class="sxs-lookup"><span data-stu-id="db98b-113">Add the Object Manipulator (Script) component to all the part objects</span></span>
2. <span data-ttu-id="db98b-114">Adicionar o componente NearInteractionGrabbable a todos os objetos de peças</span><span class="sxs-lookup"><span data-stu-id="db98b-114">Add the NearInteractionGrabbable component to all the part objects</span></span>
3. <span data-ttu-id="db98b-115">Configurar o componente Object Manipulator (Script)</span><span class="sxs-lookup"><span data-stu-id="db98b-115">Configure the Object Manipulator (Script) component</span></span>

> [!NOTE]
> <span data-ttu-id="db98b-116">Para poder **manipular um objeto**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="db98b-116">To be able to **manipulate an object**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="db98b-117">Componente **Colisor**, por exemplo, um Colisor de Caixa</span><span class="sxs-lookup"><span data-stu-id="db98b-117">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="db98b-118">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="db98b-118">**Object Manipulator (Script)** component</span></span>
>
> <span data-ttu-id="db98b-119">Para poder **manipular** e **capturar um objeto com as mãos acompanhadas**, o objeto deve ter os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="db98b-119">To be able to **manipulate** and **grab an object with tracked hands**, the object must have the following components:</span></span>
>
> * <span data-ttu-id="db98b-120">Componente **Colisor**, por exemplo, um Colisor de Caixa</span><span class="sxs-lookup"><span data-stu-id="db98b-120">**Collider** component, for example, a Box Collider</span></span>
> * <span data-ttu-id="db98b-121">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="db98b-121">**Object Manipulator (Script)** component</span></span>
> * <span data-ttu-id="db98b-122">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="db98b-122">**NearInteractionGrabbable** component</span></span>

<span data-ttu-id="db98b-123">Além disso, você vai configurar o Rover Explorer para poder colocar as peças no Rover e montá-lo completamente.</span><span class="sxs-lookup"><span data-stu-id="db98b-123">Additionally, you will configure the Rover Explorer so that you can place the rover parts on to the Rover to make it a complete rover assembly.</span></span>

<span data-ttu-id="db98b-124">Na janela Hierarquia, expanda o objeto RoverExplorer > **RoverParts** e selecione todos os seus objetos filho peças do Rover e o objeto **RoverAssembly**; em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes a todos os objetos selecionados:</span><span class="sxs-lookup"><span data-stu-id="db98b-124">In the Hierarchy window, expand the RoverExplorer > **RoverParts** object and select all its child rover part objects and the **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the following components to all the selected objects:</span></span>

* <span data-ttu-id="db98b-125">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="db98b-125">**Object Manipulator (Script)** component</span></span>
* <span data-ttu-id="db98b-126">Componente **NearInteractionGrabbable**</span><span class="sxs-lookup"><span data-stu-id="db98b-126">**NearInteractionGrabbable** component</span></span>
* <span data-ttu-id="db98b-127">Componente **Part Assembly Controller (Script)**</span><span class="sxs-lookup"><span data-stu-id="db98b-127">**Part Assembly Controller (Script)** component</span></span>

![Unity com RoverAssembly e todos os objetos de partes da sonda selecionados e os componentes adicionados](images/mr-learning-base/base-07-section1-step1-1.png)

> [!TIP]
> <span data-ttu-id="db98b-129">Para selecionar vários objetos que não estão próximos uns dos outros, mantenha a tecla CTRL pressionada e use o mouse para selecionar qualquer objeto.</span><span class="sxs-lookup"><span data-stu-id="db98b-129">To select multiple objects that are not next to each other, press-and-hold the CTRL key while using the mouse to select any object.</span></span>

> [!NOTE]
> <span data-ttu-id="db98b-130">Quando você adiciona um Object Manipulator (Script), nesse caso, o Constraint Manager (Script) é adicionado automaticamente porque o Object Manipulator (Script) depende dele.</span><span class="sxs-lookup"><span data-stu-id="db98b-130">When you add a Object Manipulator (Script), in this case, the Constraint Manager (Script) is automatically added because Object Manipulator (Script) depends on it.</span></span>

> [!NOTE]
> <span data-ttu-id="db98b-131">Para os fins deste tutorial, os colisores já foram adicionados às peças do Rover.</span><span class="sxs-lookup"><span data-stu-id="db98b-131">For the purpose of this tutorial, colliders have already been added to the rover parts.</span></span> <span data-ttu-id="db98b-132">Para saber mais sobre os colisores, acesse a documentação do <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Colisor</a> do Unity.</span><span class="sxs-lookup"><span data-stu-id="db98b-132">To learn more about colliders, you can visit Unity's <a href="https://docs.unity3d.com/Manual/CollidersOverview.html" target="_blank">Collider</a> documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="db98b-133">O Part Assembly Controller (Script) não faz parte do MRTK, mas foi incluído nos ativos do tutorial.</span><span class="sxs-lookup"><span data-stu-id="db98b-133">The Part Assembly Controller (Script) is not part of the MRTK but was included with the tutorial assets.</span></span>

<span data-ttu-id="db98b-134">Com todos os objetos de peças do Rover e o objeto RoverAssembly ainda selecionados, na janela Inspetor, configure o componente **Object Manipulator (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="db98b-134">With all the rover part objects and the RoverAssembly object still selected, in the Inspector window, configure the **Object Manipulator (Script)** component as follows:</span></span>

* <span data-ttu-id="db98b-135">Na lista suspensa **Tipo de Manipulação de Duas Mãos**, desmarque a Escala, deixando somente **Mover** e **Girar** habilitados</span><span class="sxs-lookup"><span data-stu-id="db98b-135">From the **Two Handed Manipulation Type** dropdown, uncheck the Scale, so only **Move** and **Rotate** is enabled</span></span>

![Unity com Tipo de Manipulação de Duas Mãos configurado](images/mr-learning-base/base-07-section1-step1-2.png)

> [!NOTE]
> <span data-ttu-id="db98b-137">Até agora você habilitou a manipulação de objetos para todos os objetos de peças do Rover e o objeto RoverAssembly.</span><span class="sxs-lookup"><span data-stu-id="db98b-137">At this point, you have enabled object manipulation for all the rover part objects and the RoverAssembly object.</span></span>

<span data-ttu-id="db98b-138">Na janela Projeto, navegue até a pasta **Pacotes** > **Mixed Reality Toolkit Standard Assets** > **Áudio** para localizar os clipes de áudio:</span><span class="sxs-lookup"><span data-stu-id="db98b-138">In the Project window, navigate to **Packages** > **Mixed Reality Toolkit Standard Assets** > **Audio** folder to locate the audio clips:</span></span>

![Janela Projeto do Unity com a pasta Áudio selecionada](images/mr-learning-base/base-07-section1-step1-3.png)

<span data-ttu-id="db98b-140">Na janela Hierarquia, selecione novamente todos os **objetos de peças do Rover** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **Audio Sources**, configurando-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="db98b-140">In the Hierarchy window, reselect all the **rover part objects**, then in the Inspector window, use the **Add Component** button to add the **Audio Sources** component and configure it as follows:</span></span>

* <span data-ttu-id="db98b-141">Atribua o clipe de áudio **MRTK_Scale_Start** ao campo **AudioClip**</span><span class="sxs-lookup"><span data-stu-id="db98b-141">Assign the **MRTK_Scale_Start** audio clip to the **AudioClip** field</span></span>
* <span data-ttu-id="db98b-142">Desmarque a caixa de seleção **Reproduzir ao Ativar**</span><span class="sxs-lookup"><span data-stu-id="db98b-142">Uncheck the **Play On Awake** checkbox</span></span>
* <span data-ttu-id="db98b-143">Altere **Spatial Blend** para 1</span><span class="sxs-lookup"><span data-stu-id="db98b-143">Change **Spatial Blend** to 1</span></span>

![Unity com todas as partes da sonda selecionadas e o componente Fonte de Áudio adicionado e configurado](images/mr-learning-base/base-07-section1-step1-4.png)

<span data-ttu-id="db98b-145">Na janela Hierarquia, expanda o objeto RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** para revelar todos os objetos de dica de posicionamento e, em seguida, selecione a primeira peça do Rover, RoverParts > **Camera_Part** e configure o componente **Part Assembly Controller (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="db98b-145">In the Hierarchy window, expand the RoverAssembly > RoverModel_PlacementHints_XRay > **Parts_PlacementHints** object to reveal all of the placement hint objects, then select the first rover part, RoverParts > **Camera_Part**, and configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="db98b-146">Atribua o objeto **Camera_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="db98b-146">Assign the **Camera_PlacementHint** object to the **Location To Place** field</span></span>

![Unity com o componente Camera_Part de PartAssemblyController configurado](images/mr-learning-base/base-07-section1-step1-5.png)

<span data-ttu-id="db98b-148">**Repita** esta etapa para cada um dos objetos de peças do Rover restantes e o objeto RoverAssembly para configurar o componente **Part Assembly Controller (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="db98b-148">**Repeat** this step for each of the remaining rover part objects and the RoverAssembly object to configure the **Part Assembly Controller (Script)** component as follows:</span></span>

* <span data-ttu-id="db98b-149">Para o **Generator_Part**, atribua o objeto **Generator_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="db98b-149">For the **Generator_Part**, assign the **Generator_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="db98b-150">Para o **Lights_Part**, atribua o objeto **Lights_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="db98b-150">For the **Lights_Part**, assign the **Lights_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="db98b-151">Para o **UHFAntenna_Part**, atribua o objeto **UHFAntenna_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="db98b-151">For the **UHFAntenna_Part**, assign the **UHFAntenna_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="db98b-152">Para o **Spectrometer_Part**, atribua o objeto **Spectrometer_PlacementHint** ao campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="db98b-152">For the **Spectrometer_Part**, assign the **Spectrometer_PlacementHint** object to the **Location To Place** field</span></span>
* <span data-ttu-id="db98b-153">Para o **RoverAssembly**, atribua o objeto em si, ou seja, o mesmo objeto **RoverAssembly**, para o campo **Location To Place**</span><span class="sxs-lookup"><span data-stu-id="db98b-153">For the **RoverAssembly**, assign the object itself, i.e. the same **RoverAssembly** object, to the **Location To Place** field</span></span>

<span data-ttu-id="db98b-154">Na janela Hierarquia, selecione o botão RoverExplorer > Botões > **Redefinir** e, na janela Inspetor, configure o evento **OnClick ()** interativo da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="db98b-154">In the Hierarchy window, select the RoverExplorer > Buttons > **Reset** button object, then in the Inspector window, configure the Interactable **OnClick ()** event as follows:</span></span>

* <span data-ttu-id="db98b-155">Atribua o objeto **RoverAssembly** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="db98b-155">Assign the **RoverAssembly** object to the **None (Object)** field</span></span>
* <span data-ttu-id="db98b-156">Na lista suspensa **Sem Função**, selecione **PartAssemblyController** > **ResetPlacement ()** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="db98b-156">From the **No Function** dropdown, select **PartAssemblyController** > **ResetPlacement ()** to set this function as the action to be executed when the event is triggered</span></span>

![Unity com o evento OnClick do objeto de botão Redefinir configurado](images/mr-learning-base/base-07-section1-step1-6.png)

<span data-ttu-id="db98b-158">Se agora você entrar no modo de Jogo, poderá usar a interação próxima ou distante para posicionar as peças no Rover.</span><span class="sxs-lookup"><span data-stu-id="db98b-158">If you now enter Game mode, you can use near or far interaction to place the rover parts on to the Rover.</span></span> <span data-ttu-id="db98b-159">Depois que a parte estiver próxima da dica de posicionamento correspondente, ela será encaixada no local e se tornará parte do Rover.</span><span class="sxs-lookup"><span data-stu-id="db98b-159">Once the part is close to the corresponding placement hint, it will snap into place and become part of the Rover.</span></span> <span data-ttu-id="db98b-160">Para redefinir os posicionamentos, pressione o botão Reset:</span><span class="sxs-lookup"><span data-stu-id="db98b-160">To reset the placements, you can press the Reset button:</span></span>

![Modo de exibição dividida do Modo de reprodução do Unity com o botão Redefinir recebendo um clique](images/mr-learning-base/base-07-section1-step1-7.png)

<span data-ttu-id="db98b-162">Para saber mais sobre o componente Object Manipulator e suas propriedades associadas, acesse o guia [Manipulador de Objeto](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/).</span><span class="sxs-lookup"><span data-stu-id="db98b-162">To learn more about the Object Manipulator component and its associated properties, you can visit the [Object Manipulator](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_ObjectManipulator.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/).</span></span>

## <a name="adding-bounds-control"></a><span data-ttu-id="db98b-163">Como adicionar o Controle de Limites</span><span class="sxs-lookup"><span data-stu-id="db98b-163">Adding Bounds Control</span></span>

<span data-ttu-id="db98b-164">O Controle de Limites torna mais fácil e mais intuitivo manipular objetos com uma mão tanto em interações próximas como em distantes fornecendo alças que podem ser usadas para escala e rotação.</span><span class="sxs-lookup"><span data-stu-id="db98b-164">Bounds Control makes it easier and more intuitive to manipulate objects with one hand for both near and far interaction by providing handles that can be used for scaling and rotating.</span></span>

<span data-ttu-id="db98b-165">Neste exemplo, você adicionará um BoundsControl ao objeto RoverExplorer para que toda a experiência seja facilmente movida, girada e escalonada.</span><span class="sxs-lookup"><span data-stu-id="db98b-165">In this example, you will add a BoundsControl to the RoverExplorer object so the whole experience can easily be moved, rotated, and scaled.</span></span> <span data-ttu-id="db98b-166">Além disso, você vai configurar o Menu para poder ativar e desativar o Controle de Limites.</span><span class="sxs-lookup"><span data-stu-id="db98b-166">Additionally, you will configure the Menu so you can turn the Bounds Control on and off.</span></span>

<span data-ttu-id="db98b-167">Na janela Hierarquia, selecione o objeto **RoverExplorer** e, em seguida, na janela Inspetor, use o botão **Adicionar Componente** para adicionar os seguintes componentes:</span><span class="sxs-lookup"><span data-stu-id="db98b-167">In the Hierarchy window, select the **RoverExplorer** object, then in the Inspector window, use the **Add Component** button to add the following components:</span></span>

* <span data-ttu-id="db98b-168">Componente **BoundsControl**</span><span class="sxs-lookup"><span data-stu-id="db98b-168">**BoundsControl** component</span></span>
* <span data-ttu-id="db98b-169">Componente **Object Manipulator (Script)**</span><span class="sxs-lookup"><span data-stu-id="db98b-169">**Object Manipulator (Script)** component</span></span>

<span data-ttu-id="db98b-170">Em seguida, **desmarque** a caixa de seleção próxima a todos os componentes para deixá-los **desabilitados** por padrão:</span><span class="sxs-lookup"><span data-stu-id="db98b-170">Then **uncheck** the checkbox next to all the components to make them **disabled** by default:</span></span>

![Unity com o objeto RoverExplorer selecionado e os componentes adicionados e desabilitados](images/mr-learning-base/base-07-section2-step1-1.png)

> [!NOTE]
> <span data-ttu-id="db98b-172">A visualização do Controle de Limites é criada no runtime e, portanto, não fica visível até que você entre no modo de Jogo.</span><span class="sxs-lookup"><span data-stu-id="db98b-172">The Bounds Control visualization is created at runtime and, therefore, not visible before you enter Game mode.</span></span>

> [!NOTE]
><span data-ttu-id="db98b-173">O Object Manipulator (Script) adiciona automaticamente o Constraint Manager (Script)</span><span class="sxs-lookup"><span data-stu-id="db98b-173">The Object Manipulator (Script) automatically adds Constraint Manager (Script)</span></span>

<span data-ttu-id="db98b-174">Na janela Hierarquia, expanda o objeto Menu > **ButtonCollection** para revelar os quatro botões e renomeie o terceiro botão como **BoundsControl_Enable**. Em seguida, na janela Inspetor, configure o componente **Button Config Helper (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="db98b-174">In the Hierarchy window, expand the Menu > **ButtonCollection** object to reveal the four buttons and rename the third button to **BoundsControl_Enable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="db98b-175">Altere o **Texto do Rótulo Principal** para **Habilitado**</span><span class="sxs-lookup"><span data-stu-id="db98b-175">Change the **Main Label Text** to **Enable**</span></span>
* <span data-ttu-id="db98b-176">Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="db98b-176">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="db98b-177">Na lista suspensa **Sem Função**, selecione **BoundsControl** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="db98b-177">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="db98b-178">Verifique se a caixa de seleção do argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="db98b-178">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="db98b-179">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="db98b-179">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="db98b-180">Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="db98b-180">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="db98b-181">Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="db98b-181">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="db98b-182">Verifique se a caixa de seleção do argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="db98b-182">Verify that the argument checkbox is **checked**</span></span>
* <span data-ttu-id="db98b-183">Deixe o **Ícone** como o ícone 'cubo com o controle de limites'</span><span class="sxs-lookup"><span data-stu-id="db98b-183">Leave the **Icon** as the 'cube with bounds control' icon</span></span>

![Unity com o objeto de botão BoundsControl_Enable selecionado e o componente Button Config Helper configurado](images/mr-learning-base/base-07-section2-step1-2.png)

<span data-ttu-id="db98b-185">Renomeie o quarto e último botão como **BoundsControl_Disable** e, na janela Inspetor, configure o componente **Button Config Helper (Script)** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="db98b-185">Rename the forth and last button to **BoundsControl_Disable**, then in the Inspector window, configure the **Button Config Helper (Script)** component as follows:</span></span>

* <span data-ttu-id="db98b-186">Altere o **Texto do Rótulo Principal** para **Desabilitado**</span><span class="sxs-lookup"><span data-stu-id="db98b-186">Change the **Main Label Text** to **Disable**</span></span>
* <span data-ttu-id="db98b-187">Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="db98b-187">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="db98b-188">Na lista suspensa **Sem Função**, selecione **BoundsControl** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="db98b-188">From the **No Function** dropdown, select **BoundsControl** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="db98b-189">Verifique se a caixa de seleção do argumento está **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="db98b-189">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="db98b-190">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="db98b-190">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="db98b-191">Atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="db98b-191">Assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="db98b-192">Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool Enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="db98b-192">From the **No Function** dropdown, select **ObjectManipulator** > **bool Enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="db98b-193">Verifique se a caixa de seleção do argumento está **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="db98b-193">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="db98b-194">Altere o **Ícone** para o ícone 'cubo com o controle de limites'</span><span class="sxs-lookup"><span data-stu-id="db98b-194">Change the **Icon** to the 'cube with bounds control" icon</span></span>

![Unity com o objeto de botão BoundsControl_Disable selecionado e o componente Button Config Helper configurado](images/mr-learning-base/base-07-section2-step1-3.png)

<span data-ttu-id="db98b-196">Se agora você entrar no modo de Jogo e habilitar o Controle de Limites clicando no botão Habilitar, poderá usar a interação próxima ou distante para mover, girar e escalar o Controle de Limites e usar o botão Desabilitar para desabilitar o Controle de Limites novamente:</span><span class="sxs-lookup"><span data-stu-id="db98b-196">If you now enter Game mode and enable the Bounds Control by clicking the Enable button, you can use near or far interaction to move, rotate, and scale the Bounds Control, and use the Disable button to disable the Bounds Control again:</span></span>

![Modo de exibição dividida do Modo de Jogo do Unity com o Controle de Limites sendo manipulado](images/mr-learning-base/base-07-section2-step1-4.png)

<span data-ttu-id="db98b-198">Para saber mais sobre o componente de Controle de Limites e as propriedades associadas a ele, acesse o guia da [Controle de Limites](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/).</span><span class="sxs-lookup"><span data-stu-id="db98b-198">To learn more about the Bounds Control component and its associated properties, you can visit the [Bounds Control](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundsControl.html) guide in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/).</span></span>

## <a name="congratulations"></a><span data-ttu-id="db98b-199">Parabéns</span><span class="sxs-lookup"><span data-stu-id="db98b-199">Congratulations</span></span>

<span data-ttu-id="db98b-200">Neste tutorial, você aprendeu como habilitar a manipulação próxima e distante de objetos 3D e como limitar os tipos de manipulação permitidos.</span><span class="sxs-lookup"><span data-stu-id="db98b-200">In this tutorial, you learned how to enable near and far manipulation for 3D objects and how to limit the allowed types of manipulation.</span></span> <span data-ttu-id="db98b-201">Você também aprendeu a adicionar o Controle de Limites em objetos 3D para facilitar o controle da manipulação de objetos.</span><span class="sxs-lookup"><span data-stu-id="db98b-201">You also learned how to add Bounds Control around 3D objects to make it easier to control the object manipulation.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="db98b-202">Próximo tutorial: 8. Como usar o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="db98b-202">Next Tutorial: 8. Using eye-tracking</span></span>](mr-learning-base-08.md)
