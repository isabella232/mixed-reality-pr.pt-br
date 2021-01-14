---
title: Usando comandos de fala
description: Este curso mostra como configurar, criar e usar comandos de fala em seus aplicativos de realidade misturada com o MRTK (Kit de Ferramentas de Realidade Misturada).
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, comandos de fala, entrada de voz
ms.localizationpriority: high
ms.openlocfilehash: 8aea8ead6416787f2979e0deff46ee5d6d45eb19
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007906"
---
# <a name="9-using-speech-commands"></a><span data-ttu-id="426f3-104">9. Usando comandos de fala</span><span class="sxs-lookup"><span data-stu-id="426f3-104">9. Using speech commands</span></span>

<span data-ttu-id="426f3-105">Neste tutorial, você aprenderá a criar comandos de fala e a controlá-los globalmente.</span><span class="sxs-lookup"><span data-stu-id="426f3-105">In this tutorial, you will learn how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="426f3-106">Você também aprenderá a controlar os comandos de fala locais que exigem que o usuário examine o objeto que controla o comando de fala.</span><span class="sxs-lookup"><span data-stu-id="426f3-106">You will also learn how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

## <a name="objectives"></a><span data-ttu-id="426f3-107">Objetivos</span><span class="sxs-lookup"><span data-stu-id="426f3-107">Objectives</span></span>

* <span data-ttu-id="426f3-108">Saber como criar comandos de fala</span><span class="sxs-lookup"><span data-stu-id="426f3-108">Learn how to create speech commands</span></span>
* <span data-ttu-id="426f3-109">Aprender a controlar comandos de fala globalmente e localmente</span><span class="sxs-lookup"><span data-stu-id="426f3-109">Learn how to control speech commands globally and locally</span></span>

## <a name="ensuring-the-microphone-capability-is-enabled"></a><span data-ttu-id="426f3-110">Garantir que a funcionalidade do Microfone esteja habilitada</span><span class="sxs-lookup"><span data-stu-id="426f3-110">Ensuring the Microphone capability is enabled</span></span>

<span data-ttu-id="426f3-111">No menu do Unity, selecione Kit de Ferramentas de Realidade Misturada > Utilitários > **Configurar Projeto do Unity** para abrir a janela **Configurador de Projeto do MRTK** e, em seguida, na seção **Recursos da UWP**, verifique se a opção **Habilitar Funcionalidade do Microfone** está esmaecida:</span><span class="sxs-lookup"><span data-stu-id="426f3-111">In the Unity menu, select Mixed Reality Toolkit > Utilities > **Configure Unity Project** to open the **MRTK Project Configurator** window, then in the **UWP Capabilities** section, verify that **Enable Microphone Capability** is greyed out:</span></span>

![Habilitar a funcionalidade de microfone](images/mr-learning-base/base-09-section1-step1-1.png)

> [!NOTE]
> <span data-ttu-id="426f3-113">A funcionalidade do Microfone deve ter sido habilitada durante as instruções em [Aplicar as definições do Configurador de Projeto do MRTK](mr-learning-base-02.md#selecting-mrtk-and-project-settings) quando você configurou o projeto do Unity no início desta série de tutoriais.</span><span class="sxs-lookup"><span data-stu-id="426f3-113">The Microphone capability should have been enabled during the [Apply the MRTK Project Configurator settings](mr-learning-base-02.md#selecting-mrtk-and-project-settings) instructions when you configured the Unity project at the beginning of this tutorial series.</span></span> <span data-ttu-id="426f3-114">No entanto, se não estiver habilitada, faça isso agora.</span><span class="sxs-lookup"><span data-stu-id="426f3-114">However, if it is not enabled, make sure you enable it now.</span></span>

## <a name="creating-speech-commands"></a><span data-ttu-id="426f3-115">Criando comandos de fala</span><span class="sxs-lookup"><span data-stu-id="426f3-115">Creating speech commands</span></span>

<span data-ttu-id="426f3-116">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, selecione a guia MixedRealityToolkit > **Entrada** e execute as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="426f3-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the MixedRealityToolkit > **Input** tab and take the following steps:</span></span>

* <span data-ttu-id="426f3-117">Expanda a seção **Fala**</span><span class="sxs-lookup"><span data-stu-id="426f3-117">Expand the **Speech** section</span></span>
* <span data-ttu-id="426f3-118">Clone o **DefaultMixedRealitySpeechCommandsProfile** e dê a ele um nome adequado, por exemplo, _GettingStarted_MixedRealitySpeechCommandsProfile_</span><span class="sxs-lookup"><span data-stu-id="426f3-118">Clone the **DefaultMixedRealitySpeechCommandsProfile** and give it a suitable name, for example, _GettingStarted_MixedRealitySpeechCommandsProfile_</span></span>
* <span data-ttu-id="426f3-119">Verifique se o **Comportamento de Inicialização** está definido como **Iniciar Automaticamente**</span><span class="sxs-lookup"><span data-stu-id="426f3-119">Verify that **Start Behaviour** is set to **Auto Start**</span></span>

![Criando comandos de fala](images/mr-learning-base/base-09-section2-step1-1.png)

> [!TIP]
> <span data-ttu-id="426f3-121">Para lembrar como clonar perfis de MRTK, consulte as instruções em [Configurando os perfis do MRTK](mr-learning-base-03.md).</span><span class="sxs-lookup"><span data-stu-id="426f3-121">For a reminder on how to clone MRTK profiles, you can refer to the [Configuring the MRTK profiles](mr-learning-base-03.md) instructions.</span></span>

<span data-ttu-id="426f3-122">Na seção Fala > **Comandos de Fala**, clique no botão **+ Adicionar um Novo Comando de Fala** quatro vezes para adicionar quatro novos comandos de fala à lista de comandos de fala existentes e, em seguida, nos campos **Palavra-Chave** digite as seguintes frases:</span><span class="sxs-lookup"><span data-stu-id="426f3-122">In the Speech > **Speech Commands** section, click the **+ Add a New Speech Command** button four times to add four new speech commands to the list of the existing speech commands, then in the **Keyword** fields enter the following phrases:</span></span>

* <span data-ttu-id="426f3-123">Habilitar Indicador</span><span class="sxs-lookup"><span data-stu-id="426f3-123">Enable Indicator</span></span>
* <span data-ttu-id="426f3-124">Habilitar Toque para Posicionar</span><span class="sxs-lookup"><span data-stu-id="426f3-124">Enable Tap to Place</span></span>
* <span data-ttu-id="426f3-125">Habilitar Caixa Delimitadora</span><span class="sxs-lookup"><span data-stu-id="426f3-125">Enable Bounding Box</span></span>
* <span data-ttu-id="426f3-126">Desabilitar Caixa Delimitadora</span><span class="sxs-lookup"><span data-stu-id="426f3-126">Disable Bounding Box</span></span>

![Como adicionar novos comandos de fala](images/mr-learning-base/base-09-section2-step1-2.png)

> [!TIP]
> <span data-ttu-id="426f3-128">Se o computador não tiver um microfone, atribua um KeyCode aos comandos de fala, o que lhe permitirá dispará-los quando a tecla correspondente for pressionada.</span><span class="sxs-lookup"><span data-stu-id="426f3-128">If your computer does not have a microphone you can assign a KeyCode to the speech commands, which will let you trigger them when the corresponding key is pressed.</span></span>

## <a name="controlling-speech-commands"></a><span data-ttu-id="426f3-129">Controlar comandos de fala</span><span class="sxs-lookup"><span data-stu-id="426f3-129">Controlling speech commands</span></span>

<span data-ttu-id="426f3-130">Na janela Projeto, navegue até a pasta **Ativos** > **MRTK** > **SDK** > **Recursos** > **UX** > **Pré-fabricados** > **Dica de Ferramenta** para localizar os pré-fabricados de dica de ferramenta:</span><span class="sxs-lookup"><span data-stu-id="426f3-130">In the Project window, navigate to the **Assets** > **MRTK** > **SDK** > **Features** > **UX** > **Prefabs** > **ToolTip** folder to locate the tooltip prefabs:</span></span>

![Como abrir a pasta de dica de ferramenta](images/mr-learning-base/base-09-section3-step1-1.png)

<span data-ttu-id="426f3-132">Na janela Hierarquia, clique com o botão direito do mouse em um ponto vazio e selecione **Criar Vazio** para adicionar um objeto vazio à sua cena.</span><span class="sxs-lookup"><span data-stu-id="426f3-132">In the Hierarchy window, right-click on an empty spot and select **Create Empty** to add an empty object to your scene.</span></span>

<span data-ttu-id="426f3-133">Nomeie o objeto como **SpeechInputHandler_Global** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **SpeechInputHandler** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="426f3-133">Name the object **SpeechInputHandler_Global**, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="426f3-134">**Desmarque** a caixa de seleção **Foco É Necessário** para que os usuários não precisem examinar o objeto com o componente SpeechInputHandler para disparar o comando de fala</span><span class="sxs-lookup"><span data-stu-id="426f3-134">**Uncheck** the **Is Focus Required** checkbox, so the user is not required to look at the object with the SpeechInputHandler component to trigger the speech command</span></span>
* <span data-ttu-id="426f3-135">Na janela Projeto, atribua o pré-fabricado **SpeechConfirmation Tooltip** ao campo **Speech Confirmation Tooltip Prefab**, para que esse pré-fabricado seja exibido quando um comando de fala for reconhecido</span><span class="sxs-lookup"><span data-stu-id="426f3-135">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Como configurar o componente de manipulador de entrada de fala](images/mr-learning-base/base-09-section3-step1-2.png)

<span data-ttu-id="426f3-137">No componente SpeechInputHandler, clique no ícone de pequeno **+** três vezes para adicionar três elementos de palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="426f3-137">On the SpeechInputHandler component, click the small **+** icon three times to add three keyword elements:</span></span>

![Como adicionar elementos de palavra-chave ao manipulador de entrada de fala](images/mr-learning-base/base-09-section3-step1-3.png)

<span data-ttu-id="426f3-139">Expanda **Elemento 0** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="426f3-139">Expand **Element 0** and configure it as follows:</span></span>

* <span data-ttu-id="426f3-140">No campo **Palavra-chave**, digite **Habilitar Indicador** para fazer referência ao comando de fala Habilitar Indicador criado na seção anterior</span><span class="sxs-lookup"><span data-stu-id="426f3-140">In the **Keyword** field, enter **Enable Indicator**, to reference the Enable Indicator speech command you created in the previous section</span></span>
* <span data-ttu-id="426f3-141">Clique no ícone pequeno **+** para adicionar um evento</span><span class="sxs-lookup"><span data-stu-id="426f3-141">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="426f3-142">Na janela Hierarquia, atribua o objeto **Indicador** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="426f3-142">From the Hierarchy window, assign the **Indicator** object to the **None (Object)** field</span></span>
* <span data-ttu-id="426f3-143">Na lista suspensa **Sem Função**, selecione **GameObject** > **SetActive (bool)** para definir essa função como a ação a ser executada quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="426f3-143">From the **No Function** dropdown, select **GameObject** > **SetActive (bool)** to set this function as the action to be executed when the event is triggered</span></span>
* <span data-ttu-id="426f3-144">Verifique se a caixa de seleção de argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="426f3-144">Check the argument checkbox, so it is **checked**</span></span>

![Configurar o elemento de palavra-chave 0](images/mr-learning-base/base-09-section3-step1-4.png)

<span data-ttu-id="426f3-146">Expanda **Elemento 1** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="426f3-146">Expand **Element 1** and configure it as follows:</span></span>

* <span data-ttu-id="426f3-147">No campo **Palavra-chave**, digite **Habilitar Caixa Delimitadora** para fazer referência ao comando de fala Habilitar Caixa Delimitadora criado na seção anterior</span><span class="sxs-lookup"><span data-stu-id="426f3-147">In the **Keyword** field, enter **Enable Bounding Box**, to reference the Enable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="426f3-148">Clique no ícone pequeno **+** para adicionar um evento</span><span class="sxs-lookup"><span data-stu-id="426f3-148">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="426f3-149">Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="426f3-149">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="426f3-150">Na lista suspensa **Sem Função**, selecione **BoundingBox** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="426f3-150">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="426f3-151">Verifique se a caixa de seleção de argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="426f3-151">Check the argument checkbox, so it is **checked**</span></span>
* <span data-ttu-id="426f3-152">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="426f3-152">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="426f3-153">Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="426f3-153">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="426f3-154">Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="426f3-154">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="426f3-155">Verifique se a caixa de seleção de argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="426f3-155">Check the argument checkbox, so it is **checked**</span></span>

![Configurar o elemento de palavra-chave 1](images/mr-learning-base/base-09-section3-step1-5.png)

<span data-ttu-id="426f3-157">Expanda **Elemento 2** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="426f3-157">Expand **Element 2** and configure it as follows:</span></span>

* <span data-ttu-id="426f3-158">No campo **Palavra-chave**, digite **Desabilitar Caixa Delimitadora** para fazer referência ao comando de fala Desabilitar Caixa Delimitadora criado na seção anterior</span><span class="sxs-lookup"><span data-stu-id="426f3-158">In the **Keyword** field, enter **Disable Bounding Box**, to reference the Disable Bounding Box command you created in the previous section</span></span>
* <span data-ttu-id="426f3-159">Clique no ícone pequeno **+** para adicionar um evento</span><span class="sxs-lookup"><span data-stu-id="426f3-159">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="426f3-160">Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="426f3-160">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="426f3-161">Na lista suspensa **Sem Função**, selecione **BoundingBox** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="426f3-161">From the **No Function** dropdown, select **BoundingBox** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="426f3-162">Verifique se a caixa de seleção do argumento está **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="426f3-162">Verify that the argument checkbox is **unchecked**</span></span>
* <span data-ttu-id="426f3-163">Clique no ícone pequeno **+** para adicionar outro evento</span><span class="sxs-lookup"><span data-stu-id="426f3-163">Click the small **+** icon to add another event</span></span>
* <span data-ttu-id="426f3-164">Na janela Hierarquia, atribua o objeto **RoverExplorer** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="426f3-164">From the Hierarchy window, assign the **RoverExplorer** object to the **None (Object)** field</span></span>
* <span data-ttu-id="426f3-165">Na lista suspensa **Sem Função**, selecione **ObjectManipulator** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="426f3-165">From the **No Function** dropdown, select **ObjectManipulator** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="426f3-166">Verifique se a caixa de seleção do argumento está **desmarcada**</span><span class="sxs-lookup"><span data-stu-id="426f3-166">Verify that the argument checkbox is **unchecked**</span></span>

![Configurar o elemento de palavra-chave 2](images/mr-learning-base/base-09-section3-step1-6.png)

<span data-ttu-id="426f3-168">Na janela hierarquia, selecione o objeto RoverExplorer > **RoverAssembly** e, na janela Inspetor, use o botão **Adicionar Componente** para adicionar o componente **SpeechInputHandler** e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="426f3-168">In the Hierarchy window, select the RoverExplorer > **RoverAssembly** object, then in the Inspector window, use the **Add Component** button to add the **SpeechInputHandler** component and configure it as follows:</span></span>

* <span data-ttu-id="426f3-169">Verifique se a caixa de seleção **Foco É Necessário** está **marcada** para que os usuários precisem examinar o objeto com o componente SpeechInputHandler, ou seja, o RoverAssembly, para disparar o comando de fala</span><span class="sxs-lookup"><span data-stu-id="426f3-169">Verify that the **Is Focus Required** checkbox is **check**, so the user is required to look at the object with the SpeechInputHandler component, i.e., the RoverAssembly, to trigger the speech command</span></span>
* <span data-ttu-id="426f3-170">Na janela Projeto, atribua o pré-fabricado **SpeechConfirmation Tooltip** ao campo **Speech Confirmation Tooltip Prefab**, para que esse pré-fabricado seja exibido quando um comando de fala for reconhecido</span><span class="sxs-lookup"><span data-stu-id="426f3-170">From the Project window, assign the **SpeechConfirmation Tooltip** prefab to the **Speech Confirmation Tooltip Prefab** field, to have this prefab appear when a speech command is recognized</span></span>

![Adicionar o manipulador de entrada de fala ao Rover Assembly](images/mr-learning-base/base-09-section3-step1-7.png)

<span data-ttu-id="426f3-172">No componente SpeechInputHandler, clique no ícone pequeno **+** para adicionar um elemento de palavra-chave. Expanda o elemento recém-criado e configure-o da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="426f3-172">On the SpeechInputHandler component, click the small **+** icon to add a keyword element, expand the newly created element, then configure it as follows:</span></span>

* <span data-ttu-id="426f3-173">No campo **Palavra-chave**, digite **Habilitar Toque para Posicionar** para fazer referência ao comando de fala Habilitar Toque para Posicionar criado na seção anterior</span><span class="sxs-lookup"><span data-stu-id="426f3-173">In the **Keyword** field, enter **Enable Tap to Place**, to reference the Enable Tap to Place command you created in the previous section</span></span>
* <span data-ttu-id="426f3-174">Clique no ícone pequeno **+** para adicionar um evento</span><span class="sxs-lookup"><span data-stu-id="426f3-174">Click the small **+** icon to add an event</span></span>
* <span data-ttu-id="426f3-175">Na janela Hierarquia, atribua o objeto em si, ou seja, o mesmo objeto **RoverAssembly** ao campo **Nenhum (Objeto)**</span><span class="sxs-lookup"><span data-stu-id="426f3-175">From the Hierarchy window, assign the object itself, i.e., the same **RoverAssembly** object, to the **None (Object)** field</span></span>
* <span data-ttu-id="426f3-176">Na lista suspensa **Sem Função**, selecione **TapToPlace** > **bool enabled** para atualizar esse valor da propriedade quando o evento for disparado</span><span class="sxs-lookup"><span data-stu-id="426f3-176">From the **No Function** dropdown, select **TapToPlace** > **bool enabled** to update this property value when the event is triggered</span></span>
* <span data-ttu-id="426f3-177">Verifique se a caixa de seleção de argumento está **marcada**</span><span class="sxs-lookup"><span data-stu-id="426f3-177">Check the argument checkbox, so it is **checked**</span></span>

![Configurar o manipulador de entrada de fala no Rover Assembly](images/mr-learning-base/base-09-section3-step1-8.png)

## <a name="congratulations"></a><span data-ttu-id="426f3-179">Parabéns</span><span class="sxs-lookup"><span data-stu-id="426f3-179">Congratulations</span></span>

<span data-ttu-id="426f3-180">Neste tutorial, você aprendeu a criar comandos de fala e a controlá-los globalmente.</span><span class="sxs-lookup"><span data-stu-id="426f3-180">In this tutorial, you learned how to create speech commands and how to control them globally.</span></span> <span data-ttu-id="426f3-181">Você também aprendeu a controlar os comandos de fala locais que exigem que o usuário examine o objeto que controla o comando de fala.</span><span class="sxs-lookup"><span data-stu-id="426f3-181">You also learned how to control local speech commands that require the user to look at the object that controls the speech command.</span></span>

<span data-ttu-id="426f3-182">Isso também conclui a série de [Tutoriais de introdução](mr-learning-base-01.md).</span><span class="sxs-lookup"><span data-stu-id="426f3-182">This also concludes the [Getting started tutorials](mr-learning-base-01.md) series.</span></span> <span data-ttu-id="426f3-183">Por meio desses tutoriais, você criou com êxito uma experiência de realidade misturada completa do zero usando o MRTK.</span><span class="sxs-lookup"><span data-stu-id="426f3-183">Through these tutorials, you have successfully built a complete mixed reality experience from scratch using the MRTK.</span></span>

<span data-ttu-id="426f3-184">Na próxima duas série de tutoriais, [Tutoriais de Âncoras Espaciais do Azure](mr-learning-asa-01.md) e [Tutoriais de funcionalidades de vários usuários](mr-learning-sharing-01.md), você aprenderá primeiro a integrar Âncoras Espaciais do Azure em seu projeto para ancorar a experiência do Rover Explorer criada no mundo real.</span><span class="sxs-lookup"><span data-stu-id="426f3-184">In the next two tutorial series, [Azure Spatial Anchors tutorials](mr-learning-asa-01.md) and [Multi-user capabilities tutorials](mr-learning-sharing-01.md), you will first learn how to integrate Azure Spatial Anchors into your project to anchor the Rover Explorer experience you created in the real world.</span></span> <span data-ttu-id="426f3-185">Em seguida, você aprenderá a adicionar recursos de vários usuários ao seu projeto para compartilhar movimentações de usuários e objetos em tempo real.</span><span class="sxs-lookup"><span data-stu-id="426f3-185">Then, you will learn how to add multi-user capabilities to your project to share user and object movements in real-time.</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="426f3-186">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="426f3-186">Next Development Checkpoint</span></span>

<span data-ttu-id="426f3-187">Se você está seguindo o percurso do ponto de verificação de desenvolvimento do Unity que apresentamos, sua próxima tarefa é conhecer os principais blocos de construção de aplicativos de Realidade Misturada.</span><span class="sxs-lookup"><span data-stu-id="426f3-187">If you're following the Unity development checkpoint journey we've laid out, your next task is to familiarize yourself with core building blocks of Mixed Reality apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="426f3-188">Interações básicas</span><span class="sxs-lookup"><span data-stu-id="426f3-188">Basic interactions</span></span>](../mrtk-101.md)

<span data-ttu-id="426f3-189">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](../unity-development-overview.md#1-getting-started) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="426f3-189">You can always go back to the [Unity development checkpoints](../unity-development-overview.md#1-getting-started) at any time.</span></span>

