---
title: Como usar o acompanhamento de olho
description: Este curso mostra como usar o acompanhamento com os olhos em seus aplicativos de realidade misturada com o MRTK (Kit de Ferramentas de Realidade Misturada).
author: jessemcculloch
ms.author: jemccull
ms.date: 02/05/2021
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, acompanhamento do olho
ms.localizationpriority: high
ms.openlocfilehash: bf7bd266eb471193979c588d97d14dd37aed175e
ms.sourcegitcommit: 4fb961beeebd158e2f65b7c714c5e471454400a3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/30/2021
ms.locfileid: "105982869"
---
# <a name="8-using-eye-tracking"></a><span data-ttu-id="29cb1-104">8. Como usar o acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="29cb1-104">8. Using eye-tracking</span></span>

<span data-ttu-id="29cb1-105">Neste tutorial, você aprenderá a habilitar o acompanhamento de olho para o HoloLens 2 e a adicionar acompanhamento de olho a objetos para disparar ações quando o usuário examina os objetos.</span><span class="sxs-lookup"><span data-stu-id="29cb1-105">In this tutorial, you will learn how to enable eye-tracking for HoloLens 2 and add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!NOTE]
> <span data-ttu-id="29cb1-106">Se você também estiver implantando esse projeto no HoloLens (1ª geração), observe que o acompanhamento de olho só tem suporte no HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="29cb1-106">If you are also deploying this project to HoloLens (1st generation), note that eye-tracking is only supported on HoloLens 2.</span></span>

## <a name="objectives"></a><span data-ttu-id="29cb1-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="29cb1-107">Objectives</span></span>

* <span data-ttu-id="29cb1-108">Saiba como habilitar o acompanhamento de olho para o HoleLens 2</span><span class="sxs-lookup"><span data-stu-id="29cb1-108">Learn how to enable eye-tracking for HoleLens 2</span></span>
* <span data-ttu-id="29cb1-109">Saiba como usar o acompanhamento de olho para disparar ações</span><span class="sxs-lookup"><span data-stu-id="29cb1-109">Learn how to use eye-tracking to trigger action</span></span>

[!INCLUDE[](includes/ensuring-eye-gaze-capabality.md)]

## <a name="enabling-eye-based-gaze-in-the-gaze-provider"></a><span data-ttu-id="29cb1-110">Como habilitar o foco baseado em olho no provedor de foco</span><span class="sxs-lookup"><span data-stu-id="29cb1-110">Enabling eye based gaze in the gaze provider</span></span>

<span data-ttu-id="29cb1-111">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, selecione a guia MixedRealityToolkit > **Entrada** e execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="29cb1-111">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="29cb1-112">Clone o **DefaultHoloLens2InputSystemProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_HoloLens2InputSystemProfile_</span><span class="sxs-lookup"><span data-stu-id="29cb1-112">Clone the **DefaultHoloLens2InputSystemProfile** and give it a suitable name, for example, _GettingStarted_HoloLens2InputSystemProfile_</span></span>
* <span data-ttu-id="29cb1-113">Expandir a seção **Ponteiros**</span><span class="sxs-lookup"><span data-stu-id="29cb1-113">Expand the **Pointers** section</span></span>
* <span data-ttu-id="29cb1-114">Clone o **DefaultMixedRealityPointerProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealityPointerProfile_</span><span class="sxs-lookup"><span data-stu-id="29cb1-114">Clone the **DefaultMixedRealityPointerProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityPointerProfile_</span></span>
* <span data-ttu-id="29cb1-115">Localize a seção **Configurações de Foco** e marque a caixa de seleção **Acompanhamento de Olho Está Habilitado**</span><span class="sxs-lookup"><span data-stu-id="29cb1-115">Locate the **Gaze Settings** section and check the **Is Eye Tracking Enabled** checkbox</span></span>

![Componente MixedRealityToolkit do Unity com os perfis recém-criados aplicados e o acompanhamento com os olhos habilitado](images/mr-learning-base/base-08-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="29cb1-117">Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="29cb1-117">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

## <a name="enabling-simulated-eye-tracking-for-the-unity-editor"></a><span data-ttu-id="29cb1-118">Como habilitar o controle de olho simulado para o editor do Unity</span><span class="sxs-lookup"><span data-stu-id="29cb1-118">Enabling simulated eye-tracking for the Unity editor</span></span>

<span data-ttu-id="29cb1-119">Na janela hierarquia, selecione o objeto **MixedRealityToolkit** e, em seguida, na janela Inspetor, navegue até a guia **Entrada** e, em seguida:</span><span class="sxs-lookup"><span data-stu-id="29cb1-119">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, navigate to the **Input** tab, then:</span></span>

* <span data-ttu-id="29cb1-120">Expanda a seção **Provedores de Dados de Entrada** > **Serviço de Simulação de Entrada**</span><span class="sxs-lookup"><span data-stu-id="29cb1-120">Expand the **Input Data Providers** > **Input Simulation Service** section</span></span>
* <span data-ttu-id="29cb1-121">Clone o **DefaultMixedRealityInputSimulationProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealityInputSimulationProfile_</span><span class="sxs-lookup"><span data-stu-id="29cb1-121">Clone the **DefaultMixedRealityInputSimulationProfile** and give it a suitable name, for example, _GettingStarted_MixedRealityInputSimulationProfile_</span></span>
* <span data-ttu-id="29cb1-122">Localize a **Simulação de Olhar** e configure o **Modo de Simulação de Olhar Padrão** como **Eixo Dianteiro da Câmera**</span><span class="sxs-lookup"><span data-stu-id="29cb1-122">Locate **Eye Gaze Simulation** and set the **Default Eye Gaze Simulation Mode** to **Camera Forward Axis**</span></span>

![Unity com o objeto TextMeshPro selecionado](images/mr-learning-base/base-08-section3-step1-1.png)

## <a name="adding-eye-tracking-to-objects"></a><span data-ttu-id="29cb1-124">Como adicionar acompanhamento de olho a objetos</span><span class="sxs-lookup"><span data-stu-id="29cb1-124">Adding eye-tracking to objects</span></span>

<span data-ttu-id="29cb1-125">Na janela Hierarquia, expanda **RoverExplorer** > **Botões** e selecione os três objetos do botão filho:</span><span class="sxs-lookup"><span data-stu-id="29cb1-125">In the Hierarchy window, expand the **RoverExplorer** > **Buttons**, then select all three of the child button objects:</span></span>

![Unity com objeto Botão selecionado](images/mr-learning-base/base-08-section4-step1-1.png)

<span data-ttu-id="29cb1-127">Com os três objetos Botão ainda selecionados, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **EyeTrackingTarget** a todos os objetos selecionados:</span><span class="sxs-lookup"><span data-stu-id="29cb1-127">With all three Button objects still selected, in the Inspector window use the **Add Component** button to add the **EyeTrackingTarget** component to all the selected objects:</span></span>

![Unity com o objeto TextMeshPro selecionado e os componentes adicionados](images/mr-learning-base/base-08-section4-step1-2.png)

<span data-ttu-id="29cb1-129">Na janela hierarquia, expanda **RoverExplorer** > **Botões** > **Dicas** > **SeeItSayItLabel** > **TextMeshPro**</span><span class="sxs-lookup"><span data-stu-id="29cb1-129">In the Hierarchy window, expand **RoverExplorer** > **Buttons** > **Hints** > **SeeItSayItLabel** > **TextMeshPro**</span></span>

<span data-ttu-id="29cb1-130">Em seguida, na janela Hierarquia, selecione o objeto de botão **Dicas** e configure o componente **EyeTrackingTarget** da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="29cb1-130">Then in the Hierarchy window, select the **Hints** button object , and configure the **EyeTrackingTarget** component as follows:</span></span>

* <span data-ttu-id="29cb1-131">Na seção de evento **On Look At Start ()**</span><span class="sxs-lookup"><span data-stu-id="29cb1-131">In the **On Look At Start ()** event section</span></span>
  * <span data-ttu-id="29cb1-132">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="29cb1-132">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="29cb1-133">Atribua o objeto **TextMeshPro** do botão **Dicas** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="29cb1-133">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="29cb1-134">Na lista suspensa **Sem Função**, selecione **TextMeshPro** > **float fontSize** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="29cb1-134">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="29cb1-135">Defina o argumento como **0,06** para aumentar o tamanho da fonte atual de 0,04 em 50%</span><span class="sxs-lookup"><span data-stu-id="29cb1-135">Set the argument to **0.06** to increase the current font size of 0.04 by 50%</span></span>
* <span data-ttu-id="29cb1-136">Na seção de evento **On Look Away ()**</span><span class="sxs-lookup"><span data-stu-id="29cb1-136">In the **On Look Away ()** event section</span></span>
  * <span data-ttu-id="29cb1-137">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="29cb1-137">Click the small **+** icon to add another event</span></span>
  * <span data-ttu-id="29cb1-138">Atribua o objeto **TextMeshPro** do botão **Dicas** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="29cb1-138">Assign the  **TextMeshPro** object from the **Hints** button to the **None (Object)** field</span></span>
  * <span data-ttu-id="29cb1-139">Na lista suspensa **Sem Função**, selecione **TextMeshPro** > **float fontSize** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="29cb1-139">From the **No Function** dropdown, select **TextMeshPro** > **float fontSize** to update this property value when the event is triggered</span></span>
  * <span data-ttu-id="29cb1-140">Defina o argumento como **0,04** para redefinir o tamanho da fonte de volta para 0,04</span><span class="sxs-lookup"><span data-stu-id="29cb1-140">Set the argument to **0.04** to reset the font size back to 0.04</span></span>

![Unity com o objeto Hints TextMeshPro selecionado e o componente EyeTrackingTarget configurado](images/mr-learning-base/base-08-section4-step1-3.png)

<span data-ttu-id="29cb1-142">**Repita** essa etapa para o objeto de botão **Detalhar** e **Redefinir** para configurar o acompanhamento ocular para os botões restantes.</span><span class="sxs-lookup"><span data-stu-id="29cb1-142">**Repeat** this step for **Explode** and **Reset** button object to configure eye tracking for remaining buttons.</span></span>

<span data-ttu-id="29cb1-143">Se agora você entrar no modo de Jogo e pressionar e manter o botão direito do mouse enquanto move o mouse até que o foco atinja um dos botões, verá o tamanho da fonte do texto aumentar em 50% e ser redefinido de volta ao seu tamanho original ao desviar o olhar:</span><span class="sxs-lookup"><span data-stu-id="29cb1-143">If you now enter Game mode and then press-and-hold the right mouse button while moving your mouse until the gaze hit's one of the buttons, you will see the text font size increase by 50% and reset back to its original size when looking away:</span></span>

![Modo de exibição dividida do Modo de reprodução do Unity com o foco sobre o rótulo do botão Detalhar do destino de acompanhamento com os olhos](images/mr-learning-base/base-08-section4-step1-4.png)

## <a name="congratulations"></a><span data-ttu-id="29cb1-145">Parabéns</span><span class="sxs-lookup"><span data-stu-id="29cb1-145">Congratulations</span></span>

<span data-ttu-id="29cb1-146">Neste tutorial, você aprendeu a habilitar o acompanhamento de olho para o HoloLens 2 e a adicionar acompanhamento de olho a objetos para disparar ações quando o usuário examina os objetos.</span><span class="sxs-lookup"><span data-stu-id="29cb1-146">In this tutorial, you learned how to enable eye-tracking for HoloLens 2 and how to add eye-tracking to objects to trigger actions when the user looks at the objects.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="29cb1-147">Próximo tutorial: 9. Usando comandos de fala</span><span class="sxs-lookup"><span data-stu-id="29cb1-147">Next Tutorial: 9. Using speech commands</span></span>](mr-learning-base-09.md)
