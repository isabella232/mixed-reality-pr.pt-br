---
ms.openlocfilehash: 5d3f5b1dd0600404e534023e3bf7b6fcaf7fe8f6
ms.sourcegitcommit: 8d386bf6c82ec9860815e873e1f2870ea410f40f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106098066"
---
# <a name="unity-20192020--windows-xr-plugin"></a>[<span data-ttu-id="1f74f-101">Unity 2019/2020 + Plug-in do Windows XR</span><span class="sxs-lookup"><span data-stu-id="1f74f-101">Unity 2019/2020 + Windows XR Plugin</span></span>](#tab/winxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="1f74f-102">1. Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-102">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="1f74f-103">O perfil de configuração é o perfil de nível superior.</span><span class="sxs-lookup"><span data-stu-id="1f74f-103">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="1f74f-104">Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.</span><span class="sxs-lookup"><span data-stu-id="1f74f-104">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="1f74f-105">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, verifique se o Perfil de Configuração do **MixedRealityToolkit** está configurado como **DefaultXRSDKConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-105">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultXRSDKConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit do Unity com DefaultHoloLens2ConfigurationProfile selecionado](../images/mr-learning-base/base-03-section1-step1-1xrsdk.png)

<span data-ttu-id="1f74f-107">Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-107">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Botão Copiar e Personalizar do componente MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step1-2xrsdk.png)

<span data-ttu-id="1f74f-109">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_XRSDKConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultXRSDKConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-109">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKConfigurationProfile**:</span></span>

![Janela pop-up Perfil de Configuração do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step1-3xrsdk.png)

<span data-ttu-id="1f74f-111">Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:</span><span class="sxs-lookup"><span data-stu-id="1f74f-111">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit do Unity com o HoloLens2ConfigurationProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step1-4xrsdk.png)

<span data-ttu-id="1f74f-113">No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.</span><span class="sxs-lookup"><span data-stu-id="1f74f-113">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="1f74f-114">Lembre-se de salvar seu trabalho ao longo dos tutoriais.</span><span class="sxs-lookup"><span data-stu-id="1f74f-114">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="1f74f-115">2. Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="1f74f-115">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="1f74f-116">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-116">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit do Unity com o Sistema de Reconhecimento Espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="1f74f-118">Para projetos futuros, se o seu aplicativo não precisa responder ao ambiente nem interagir com ele, recomendamos manter o reconhecimento espacial desativado para reduzir o custo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="1f74f-118">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="1f74f-119">3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-119">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="1f74f-120">Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-120">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity com a guia Reconhecimento Espacial selecionada](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="1f74f-122">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, e clique no botão **Clonar** para criar uma cópia editável do **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-122">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_XRSDKSpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Janela pop-up Perfil do Sistema de Reconhecimento Espacial do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="1f74f-124">O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:</span><span class="sxs-lookup"><span data-stu-id="1f74f-124">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessSystemProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="1f74f-126">4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-126">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="1f74f-127">Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality do SDK do XR** e clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-127">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity com a seção Observador de Malha Espacial do Windows Mixed Reality expandida](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="1f74f-129">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-129">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Janela pop-up Perfil de Observador da Malha Espacial do clone MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="1f74f-131">O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:</span><span class="sxs-lookup"><span data-stu-id="1f74f-131">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessMeshObserverProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="1f74f-133">5. Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="1f74f-133">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="1f74f-134">Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:</span><span class="sxs-lookup"><span data-stu-id="1f74f-134">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente MixedRealityToolkit do Unity com a Opção de Exibição de Observador de Malha Espacial definida como Oclusão](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="1f74f-136">Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional.</span><span class="sxs-lookup"><span data-stu-id="1f74f-136">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="1f74f-137">Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="1f74f-137">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="1f74f-138">Você acabou de aprender como modificar uma configuração do perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="1f74f-138">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="1f74f-139">Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão.</span><span class="sxs-lookup"><span data-stu-id="1f74f-139">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="1f74f-140">Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="1f74f-140">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="1f74f-141">Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="1f74f-141">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>

# <a name="unity-2020--openxr"></a>[<span data-ttu-id="1f74f-142">Unity 2020 + OpenXR</span><span class="sxs-lookup"><span data-stu-id="1f74f-142">Unity 2020 + OpenXR</span></span>](#tab/openxr)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="1f74f-143">1. Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-143">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="1f74f-144">O perfil de configuração é o perfil de nível superior.</span><span class="sxs-lookup"><span data-stu-id="1f74f-144">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="1f74f-145">Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.</span><span class="sxs-lookup"><span data-stu-id="1f74f-145">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="1f74f-146">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit** e, na janela Inspetor, verifique se o Perfil de Configuração do **MixedRealityToolkit** está configurado como **DefaultOpenXRConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-146">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, verify that the **MixedRealityToolkit** Configuration Profile is set to the **DefaultOpenXRConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit do Unity com perfil padrão do OpenXR selecionado](../images/mr-learning-base/base-03-section1-step1-1openxr.png)

<span data-ttu-id="1f74f-148">Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-148">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity, botão Copiar e Personalizar para o perfil do OpenXR](../images/mr-learning-base/base-03-section1-step1-2openxr.png)

<span data-ttu-id="1f74f-150">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_OpenXRConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultOpenXRConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-150">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_OpenXRConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultOpenXRConfigurationProfile**:</span></span>

![Janela pop-up Perfil de Configuração do clone de MixedRealityToolkit do Unity para o perfil do OpenXR](../images/mr-learning-base/base-03-section1-step1-3openxr.png)

<span data-ttu-id="1f74f-152">Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:</span><span class="sxs-lookup"><span data-stu-id="1f74f-152">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit do Unity com o OpenXR recém-criado e personalizado aplicado](../images/mr-learning-base/base-03-section1-step1-4openxr.png)

<span data-ttu-id="1f74f-154">No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.</span><span class="sxs-lookup"><span data-stu-id="1f74f-154">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="1f74f-155">Lembre-se de salvar seu trabalho ao longo dos tutoriais.</span><span class="sxs-lookup"><span data-stu-id="1f74f-155">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="1f74f-156">2. Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="1f74f-156">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="1f74f-157">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-157">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit do Unity com o Sistema de Reconhecimento Espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="1f74f-159">Para projetos futuros, se o seu aplicativo não precisa responder ao ambiente nem interagir com ele, recomendamos manter o reconhecimento espacial desativado para reduzir o custo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="1f74f-159">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="1f74f-160">3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-160">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="1f74f-161">Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-161">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity com a guia Reconhecimento Espacial selecionada](../images/mr-learning-base/base-03-section1-step3-1xrsdk.png)

<span data-ttu-id="1f74f-163">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, GettingStarted_OpenXRSpatialAwarenessSystemProfile e clique no botão **Clonar** para criar uma cópia editável do **DefaultXRSDKSpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-163">In the Clone Profile window, enter a suitable **Profile Name**, for example, GettingStarted_OpenXRSpatialAwarenessSystemProfile, then click the **Clone** button to create an editable copy of the **DefaultXRSDKSpatialAwarenessSystemProfile**:</span></span>

![Janela pop-up Perfil do Sistema de Reconhecimento Espacial do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step3-2xrsdk.png)

<span data-ttu-id="1f74f-165">O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:</span><span class="sxs-lookup"><span data-stu-id="1f74f-165">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessSystemProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step3-3xrsdk.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="1f74f-167">4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-167">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="1f74f-168">Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality do SDK do XR** e clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-168">With the **Spatial Awareness** tab still selected, expand the **XR SDK Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity com a seção Observador de Malha Espacial do Windows Mixed Reality expandida](../images/mr-learning-base/base-03-section1-step4-1xrsdk.png)

<span data-ttu-id="1f74f-170">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-170">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Janela pop-up Perfil de Observador da Malha Espacial do clone MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step4-2xrsdk.png)

<span data-ttu-id="1f74f-172">O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:</span><span class="sxs-lookup"><span data-stu-id="1f74f-172">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessMeshObserverProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step4-3xrsdk.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="1f74f-174">5. Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="1f74f-174">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="1f74f-175">Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:</span><span class="sxs-lookup"><span data-stu-id="1f74f-175">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente MixedRealityToolkit do Unity com a Opção de Exibição de Observador de Malha Espacial definida como Oclusão](../images/mr-learning-base/base-03-section1-step5-1xrsdk.png)

> [!NOTE]
> <span data-ttu-id="1f74f-177">Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional.</span><span class="sxs-lookup"><span data-stu-id="1f74f-177">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="1f74f-178">Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="1f74f-178">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="1f74f-179">Você acabou de aprender como modificar uma configuração do perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="1f74f-179">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="1f74f-180">Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão.</span><span class="sxs-lookup"><span data-stu-id="1f74f-180">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="1f74f-181">Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="1f74f-181">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="1f74f-182">Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="1f74f-182">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>


# <a name="legacy-wsa"></a>[<span data-ttu-id="1f74f-183">WSA herdado</span><span class="sxs-lookup"><span data-stu-id="1f74f-183">Legacy WSA</span></span>](#tab/wsa)

### <a name="1-clone-the-default-configuration-profile"></a><span data-ttu-id="1f74f-184">1. Clonar o perfil de configuração padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-184">1. Clone the default Configuration Profile</span></span>

> [!NOTE]
> <span data-ttu-id="1f74f-185">O perfil de configuração é o perfil de nível superior.</span><span class="sxs-lookup"><span data-stu-id="1f74f-185">The Configuration Profile is the top-level profile.</span></span> <span data-ttu-id="1f74f-186">Assim, para poder editar outros perfis, primeiro você precisa clonar o perfil de configuração.</span><span class="sxs-lookup"><span data-stu-id="1f74f-186">Consequently, to be able to edit any other profiles, you first have to clone the Configuration Profile.</span></span>

<span data-ttu-id="1f74f-187">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, altere o Perfil de Configuração do **MixedRealityToolkit** para o **DefaultHoloLens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-187">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, change the **MixedRealityToolkit** Configuration Profile to the **DefaultHoloLens2ConfigurationProfile**:</span></span>

![Componente MixedRealityToolkit do Unity com DefaultHoloLens2ConfigurationProfile selecionado](../images/mr-learning-base/base-03-section1-step1-1.png)

<span data-ttu-id="1f74f-189">Com o objeto **MixedRealityToolkit** ainda selecionado, na janela Inspetor, clique no botão **Copiar e Personalizar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-189">With the **MixedRealityToolkit** object still selected, in the Inspector window, click the **Copy & Customize** button to open the Clone Profile window:</span></span>

![Botão Copiar e Personalizar do componente MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step1-2.png)

<span data-ttu-id="1f74f-191">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_HoloLens2ConfigurationProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultHololens2ConfigurationProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-191">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_HoloLens2ConfigurationProfile_, then click the **Clone** button to create an editable copy of the **DefaultHololens2ConfigurationProfile**:</span></span>

![Janela pop-up Perfil de Configuração do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step1-3.png)

<span data-ttu-id="1f74f-193">Agora, o Perfil de Configuração recém-criado é atribuído como o Perfil de Configuração para sua cena:</span><span class="sxs-lookup"><span data-stu-id="1f74f-193">The newly created Configuration Profile is now assigned as the Configuration Profile for your scene:</span></span>

![Componente MixedRealityToolkit do Unity com o HoloLens2ConfigurationProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step1-4.png)

<span data-ttu-id="1f74f-195">No menu do Unity, selecione **Arquivo** > **Salvar** para salvar sua cena.</span><span class="sxs-lookup"><span data-stu-id="1f74f-195">In the Unity menu, select **File** > **Save** to save your scene.</span></span>

> [!TIP]
> <span data-ttu-id="1f74f-196">Lembre-se de salvar seu trabalho ao longo dos tutoriais.</span><span class="sxs-lookup"><span data-stu-id="1f74f-196">Remember to save your work throughout the tutorials.</span></span>

### <a name="2-enable-the-spatial-awareness-system"></a><span data-ttu-id="1f74f-197">2. Habilitar o Sistema de Reconhecimento Espacial</span><span class="sxs-lookup"><span data-stu-id="1f74f-197">2. Enable the Spatial Awareness System</span></span>

<span data-ttu-id="1f74f-198">Na janela Hierarquia, selecione o objeto **MixedRealityToolkit**, então, na janela Inspetor, selecione a guia **Reconhecimento Espacial** e marque a caixa de seleção **Habilitar o Sistema de Reconhecimento Espacial**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-198">In the Hierarchy window, select the **MixedRealityToolkit** object, then in the Inspector window, select the **Spatial Awareness** tab, and then check the **Enable Spatial Awareness System** checkbox:</span></span>

![Componente MixedRealityToolkit do Unity com o Sistema de Reconhecimento Espacial habilitado](../images/mr-learning-base/base-03-section1-step2-1.png)

> [!NOTE]
> <span data-ttu-id="1f74f-200">Para projetos futuros, se o seu aplicativo não precisa responder ao ambiente nem interagir com ele, recomendamos manter o reconhecimento espacial desativado para reduzir o custo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="1f74f-200">For future projects, if your app doesn't need to respond to or interact with the environment, it's recommended to keep the spatial awareness turned off to reduce performance cost.</span></span>

### <a name="3-clone-the-default-spatial-awareness-system-profile"></a><span data-ttu-id="1f74f-201">3. Clonar o perfil do Sistema de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-201">3. Clone the default Spatial Awareness System Profile</span></span>

<span data-ttu-id="1f74f-202">Na guia **Reconhecimento Espacial**, clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-202">In the **Spatial Awareness** tab, click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity com a guia Reconhecimento Espacial selecionada](../images/mr-learning-base/base-03-section1-step3-1.png)

<span data-ttu-id="1f74f-204">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-204">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessSystemProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessSystemProfile**:</span></span>

![Janela pop-up Perfil do Sistema de Reconhecimento Espacial do clone de MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step3-2.png)

<span data-ttu-id="1f74f-206">O Perfil do Sistema de Reconhecimento Espacial recém-criado agora é atribuído automaticamente ao seu Perfil de Configuração:</span><span class="sxs-lookup"><span data-stu-id="1f74f-206">The newly created Spatial Awareness System Profile is now automatically assigned to your Configuration Profile:</span></span>

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessSystemProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step3-3.png)

### <a name="4-clone-the-default-spatial-awareness-mesh-observer-profile"></a><span data-ttu-id="1f74f-208">4. Clonar o Perfil de Observador de Malha de Reconhecimento Espacial padrão</span><span class="sxs-lookup"><span data-stu-id="1f74f-208">4. Clone the default Spatial Awareness Mesh Observer Profile</span></span>

<span data-ttu-id="1f74f-209">Com a guia **Reconhecimento Espacial** ainda selecionada, expanda a seção **Observador de Malha Espacial do Windows Mixed Reality** e clique no botão **Clonar** para abrir a janela Clonar Perfil:</span><span class="sxs-lookup"><span data-stu-id="1f74f-209">With the **Spatial Awareness** tab still selected, expand the **Windows Mixed Reality Spatial Mesh Observer** section, then click the **Clone** button to open the Clone Profile window:</span></span>

![Componente MixedRealityToolkit do Unity com a seção Observador de Malha Espacial do Windows Mixed Reality expandida](../images/mr-learning-base/base-03-section1-step4-1.png)

<span data-ttu-id="1f74f-211">Na janela Clonar Perfil, insira um **Nome de Perfil** adequado, por exemplo, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_ e clique no botão **Clonar** para criar uma cópia editável do **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span><span class="sxs-lookup"><span data-stu-id="1f74f-211">In the Clone Profile window, enter a suitable **Profile Name**, for example, _GettingStarted_MixedRealitySpatialAwarenessMeshObserverProfile_, then click the **Clone** button to create an editable copy of the **DefaultMixedRealitySpatialAwarenessMeshObserverProfile**:</span></span>

![Janela pop-up Perfil de Observador da Malha Espacial do clone MixedRealityToolkit do Unity](../images/mr-learning-base/base-03-section1-step4-2.png)

<span data-ttu-id="1f74f-213">O Perfil de Observador de Malha de Reconhecimento Espacial recém-criado agora é automaticamente atribuído ao seu Perfil do Sistema de Reconhecimento Espacial:</span><span class="sxs-lookup"><span data-stu-id="1f74f-213">The newly created Spatial Awareness Mesh Observer Profile is now automatically assigned to your Spatial Awareness System Profile:</span></span>

![Componente MixedRealityToolkit do Unity com o MixedRealitySpatialAwarenessMeshObserverProfile personalizado recém-criado aplicado](../images/mr-learning-base/base-03-section1-step4-3.png)

### <a name="5-change-the-visibility-of-the-spatial-awareness-mesh"></a><span data-ttu-id="1f74f-215">5. Altere a visibilidade da malha de reconhecimento espacial</span><span class="sxs-lookup"><span data-stu-id="1f74f-215">5. Change the visibility of the spatial awareness mesh</span></span>

<span data-ttu-id="1f74f-216">Em **Configurações do Observador de Malha Espacial**, altere a **Opção de Exibição** para **Oclusão** para tornar a malha de mapeamento espacial invisível, mas ainda funcional:</span><span class="sxs-lookup"><span data-stu-id="1f74f-216">In the **Spatial Mesh Observer Settings**, change the **Display Option** to **Occlusion** to make the spatial mapping mesh invisible while still functional:</span></span>

![Componente MixedRealityToolkit do Unity com a Opção de Exibição de Observador de Malha Espacial definida como Oclusão](../images/mr-learning-base/base-03-section1-step5-1.png)

> [!NOTE]
> <span data-ttu-id="1f74f-218">Embora a malha de mapeamento espacial não esteja visível, ela ainda está presente e funcional.</span><span class="sxs-lookup"><span data-stu-id="1f74f-218">Although the spatial mapping mesh is not visible, it is still present and functional.</span></span> <span data-ttu-id="1f74f-219">Por exemplo, os hologramas por trás da malha de mapeamento espacial, como um holograma por trás de uma parede física, não estarão visíveis.</span><span class="sxs-lookup"><span data-stu-id="1f74f-219">For example, any holograms behind the spatial mapping mesh, such as a hologram behind a physical wall, will not be visible.</span></span>

<span data-ttu-id="1f74f-220">Você acabou de aprender como modificar uma configuração do perfil do MRTK.</span><span class="sxs-lookup"><span data-stu-id="1f74f-220">You just learned how to modify a setting in the MRTK profile.</span></span> <span data-ttu-id="1f74f-221">Como você pode ver, para personalizar as configurações de MRTK, primeiro é necessário criar cópias dos perfis padrão.</span><span class="sxs-lookup"><span data-stu-id="1f74f-221">As you can see, to customize the MRTK settings, you first need to create copies of the default profiles.</span></span> <span data-ttu-id="1f74f-222">Como os perfis padrão não são editáveis, você sempre os terá como referência se quiser reverter para as configurações padrão.</span><span class="sxs-lookup"><span data-stu-id="1f74f-222">Because the default profiles are not editable, you will always have them as references if you want to revert to the default settings.</span></span> <span data-ttu-id="1f74f-223">Para saber mais sobre os perfis do MRTK e sua arquitetura, você pode consultar o [Guia de configuração do perfil do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) no [Portal de Documentação do MRTK](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span><span class="sxs-lookup"><span data-stu-id="1f74f-223">To learn more about MRTK profiles and their architecture, you can refer to the [MRTK profile configuration guide](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/configuration/mixed-reality-configuration-guide) in the [MRTK Documentation Portal](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity).</span></span>
