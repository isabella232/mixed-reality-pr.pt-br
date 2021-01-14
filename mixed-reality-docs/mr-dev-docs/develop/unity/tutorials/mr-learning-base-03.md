---
title: Como configurar os perfis do MRTK
description: Este curso mostra como configurar perfis do MRTK (Kit de Ferramentas de Realidade Misturada) para seus aplicativos de realidade misturada.
author: jessemcculloch
ms.author: jemccull
ms.date: 07/01/2020
ms.topic: article
keywords: realidade misturada, unity, tutorial, hololens, MRTK, kit de ferramentas de realidade misturada, UWP, reconhecimento espacial
ms.localizationpriority: high
ms.openlocfilehash: 58f9c5f756a12e99fd10b136b2a450c6227b2dad
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98008006"
---
# <a name="3-configuring-the-mrtk-profiles"></a><span data-ttu-id="0b70c-104">3. Como configurar os perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="0b70c-104">3. Configuring the MRTK profiles</span></span>

<span data-ttu-id="0b70c-105">Neste tutorial, você aprenderá a personalizar e configurar os perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b70c-105">In this tutorial, you will learn how to customize and configure the MRTK profiles.</span></span>

<span data-ttu-id="0b70c-106">Os <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">perfis do MRTK</a> são uma árvore de perfis aninhados que compõem as informações de configuração sobre como os sistemas e os recursos do MRTK devem ser inicializados.</span><span class="sxs-lookup"><span data-stu-id="0b70c-106">The <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/Profiles/Profiles.html" target="_blank">MRTK profiles</a> is a tree of nested profiles that make up the configuration information for how the MRTK systems and features should be initialized.</span></span> <span data-ttu-id="0b70c-107">O perfil de nível superior, o Perfil de Configuração, contém perfis aninhados para cada um dos principais sistemas básicos.</span><span class="sxs-lookup"><span data-stu-id="0b70c-107">The top-level profile, the Configuration Profile, contains nested profiles for each of the primary core systems.</span></span> <span data-ttu-id="0b70c-108">Cada perfil aninhado foi projetado para configurar o comportamento do respectivo sistema correspondente.</span><span class="sxs-lookup"><span data-stu-id="0b70c-108">Each nested profile is designed to configure the behavior of their corresponding system.</span></span>

<span data-ttu-id="0b70c-109">Este exemplo específico mostrará como ocultar a malha de reconhecimento espacial alterando as configurações do Observador de Malha Espacial.</span><span class="sxs-lookup"><span data-stu-id="0b70c-109">This particular example will show you how to hide the spatial awareness mesh by changing the settings of the Spatial Mesh Observer.</span></span> <span data-ttu-id="0b70c-110">No entanto, você pode seguir esses mesmos princípios para personalizar qualquer configuração ou valor nos perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b70c-110">However, you may follow these same principles to customize any setting or value in the MRTK profiles.</span></span>

<span data-ttu-id="0b70c-111">Como você experimentou quando implantou seu projeto no HoloLens 2 durante o [tutorial anterior](mr-learning-base-02.md#congratulations), a malha de <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Reconhecimento Espacial</a> é uma coleção de malhas que representa a geometria do ambiente.</span><span class="sxs-lookup"><span data-stu-id="0b70c-111">As you experienced when you deployed your project to your HoloLens 2 during the [previous tutorial](mr-learning-base-02.md#congratulations), the <a href="https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/SpatialAwareness/SpatialAwarenessGettingStarted.html" target="_blank">Spatial Awareness</a> mesh is a collection of meshes representing the geometry of the environment.</span></span> <span data-ttu-id="0b70c-112">É uma visualização útil de ser vista inicialmente, mas em geral, é desativada para evitar a distração visual e o impacto adicional de desempenho da presença dela.</span><span class="sxs-lookup"><span data-stu-id="0b70c-112">It's a helpful visualization to see initially but it's typically turned off to avoid the visual distraction and the additional performance hit of having it on.</span></span>

## <a name="objectives"></a><span data-ttu-id="0b70c-113">Objetivos</span><span class="sxs-lookup"><span data-stu-id="0b70c-113">Objectives</span></span>

* <span data-ttu-id="0b70c-114">Saiba como personalizar e configurar perfis do MRTK</span><span class="sxs-lookup"><span data-stu-id="0b70c-114">Learn how to customize and configure MRTK profiles</span></span>
* <span data-ttu-id="0b70c-115">Ocultar a malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="0b70c-115">Hide the spatial awareness mesh</span></span>

## <a name="changing-the-spatial-awareness-display-option"></a><span data-ttu-id="0b70c-116">Como alterar a opção de exibição de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="0b70c-116">Changing the Spatial Awareness Display Option</span></span>

<span data-ttu-id="0b70c-117">As principais etapas que você seguirá para ocultar a malha de reconhecimento espacial são:</span><span class="sxs-lookup"><span data-stu-id="0b70c-117">The main steps you will take to hide the spatial awareness mesh are:</span></span>

1. <span data-ttu-id="0b70c-118">Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="0b70c-118">Clone the default Configuration Profile</span></span>
2. <span data-ttu-id="0b70c-119">Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="0b70c-119">Enable the Spatial Awareness System</span></span>
3. <span data-ttu-id="0b70c-120">Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="0b70c-120">Clone the default Spatial Awareness System Profile</span></span>
4. <span data-ttu-id="0b70c-121">Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="0b70c-121">Clone the default Spatial Awareness Mesh Observer Profile</span></span>
5. <span data-ttu-id="0b70c-122">Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="0b70c-122">Change the visibility of the spatial awareness mesh</span></span>

> [!NOTE]
> <span data-ttu-id="0b70c-123">Por padrão, os perfis do MRTK não são editáveis.</span><span class="sxs-lookup"><span data-stu-id="0b70c-123">By default, the MRTK profiles are not editable.</span></span> <span data-ttu-id="0b70c-124">Esses são modelos de perfil padrão que você precisa clonar antes que eles possam ser editados.</span><span class="sxs-lookup"><span data-stu-id="0b70c-124">These are default profile templates that you have to clone before they can be edited.</span></span> <span data-ttu-id="0b70c-125">Há várias camadas aninhadas de perfis.</span><span class="sxs-lookup"><span data-stu-id="0b70c-125">There are several nested layers of profiles.</span></span> <span data-ttu-id="0b70c-126">Portanto, é comum clonar e editar vários perfis ao definir uma ou mais configurações.</span><span class="sxs-lookup"><span data-stu-id="0b70c-126">Therefore, it is common to clone and edit several profiles when configuring one or more settings.</span></span>

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="0b70c-127">1. Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="0b70c-127">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="0b70c-128">O perfil de configuração é o perfil de nível superior.</span><span class="sxs-lookup"><span data-stu-id="0b70c-128">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="0b70c-129">Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.</span><span class="sxs-lookup"><span data-stu-id="0b70c-129">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="0b70c-130">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, altere o Perfil de Configuração do **MixedRealityToolkit** para o **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="0b70c-130">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit do Unity com DefaultHoloLens2ConfigurationProfile selecionado](images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="0b70c-132">Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="0b70c-132">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Botão Copiar e Personalizar do componente MixedRealityToolkit do Unity](images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="0b70c-134">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_HoloLens2ConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="0b70c-134">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Janela pop-up Perfil de Configuração do clone de MixedRealityToolkit do Unity](images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="0b70c-136">Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:</span><span class="sxs-lookup"><span data-stu-id="0b70c-136">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit do Unity com o HoloLens2ConfigurationProfile personalizado recém-criado aplicado](images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="0b70c-138">No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.</span><span class="sxs-lookup"><span data-stu-id="0b70c-138">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="0b70c-139">Lembre-se de salvar seu trabalho ao longo dos tutoriais.</span><span class="sxs-lookup"><span data-stu-id="0b70c-139">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="0b70c-140">2. Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="0b70c-140">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="0b70c-141">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:</span><span class="sxs-lookup"><span data-stu-id="0b70c-141">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit do Unity com o Sistema de Reconhecimento Espacial habilitado](images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="0b70c-143">Para projetos futuros, se o seu aplicativo não precisa responder ao ambiente nem interagir com ele, recomendamos manter o reconhecimento espacial desativado para reduzir o custo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="0b70c-143">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="0b70c-144">3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="0b70c-144">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="0b70c-145">Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="0b70c-145">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity com a guia Reconhecimento Espacial selecionada](images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="0b70c-147">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="0b70c-147">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Janela pop-up Perfil do Sistema de Reconhecimento Espacial do clone de MixedRealityToolkit do Unity](images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="0b70c-149">O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:</span><span class="sxs-lookup"><span data-stu-id="0b70c-149">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessSystemProfile personalizado recém-criado aplicado](images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="0b70c-151">4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="0b70c-151">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="0b70c-152">Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality** e clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="0b70c-152">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity com a seção Observador de Malha Espacial do Windows Mixed Reality expandida](images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="0b70c-154">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="0b70c-154">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Janela pop-up Perfil de Observador da Malha Espacial do clone MixedRealityToolkit do Unity](images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="0b70c-156">O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:</span><span class="sxs-lookup"><span data-stu-id="0b70c-156">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessMeshObserverProfile personalizado recém-criado aplicado](images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="0b70c-158">5. Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="0b70c-158">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="0b70c-159">Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:</span><span class="sxs-lookup"><span data-stu-id="0b70c-159">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente MixedRealityToolkit do Unity com a Opção de Exibição de Observador de Malha Espacial definida como Oclusão](images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="0b70c-161">Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional.</span><span class="sxs-lookup"><span data-stu-id="0b70c-161">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="0b70c-162">Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="0b70c-162">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="0b70c-163">Você acabou de aprender como modificar uma configuração do perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b70c-163">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="0b70c-164">Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão.</span><span class="sxs-lookup"><span data-stu-id="0b70c-164">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="0b70c-165">Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="0b70c-165">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="0b70c-166">Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) no [Portal de Documentação do MRTK](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span><span class="sxs-lookup"><span data-stu-id="0b70c-166">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/MixedRealityConfigurationGuide.html) in the [MRTK Documentation Portal](https://microsoft.github.io/MixedRealityToolkit-Unity/README.html).</span></span>

## <a name="congratulations"></a><span data-ttu-id="0b70c-167">Parabéns</span><span class="sxs-lookup"><span data-stu-id="0b70c-167">Congratulations</span></span>

<span data-ttu-id="0b70c-168">Neste tutorial, você aprendeu a clonar, personalizar e definir uma configurações e perfis do MRTK.</span><span class="sxs-lookup"><span data-stu-id="0b70c-168">In this tutorial, you learned how to clone, customize, and configure MRTK profiles and settings.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b70c-169">Próximo tutorial: 4. Como posicionar objetos na cena</span><span class="sxs-lookup"><span data-stu-id="0b70c-169">Next Tutorial: 4. Positioning objects in the scene</span></span>](mr-learning-base-04.md)
