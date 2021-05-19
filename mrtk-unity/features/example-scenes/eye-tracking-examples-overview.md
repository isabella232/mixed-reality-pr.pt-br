---
title: Visão geral do exemplo de acompanhamento de olho
description: Exemplo para criar eyetracking em MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: b5fd3ee35e54c54f2f6b21dc1ce53625c68f65b4
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144684"
---
# <a name="eye-tracking-examples"></a><span data-ttu-id="965a6-104">Exemplos de acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="965a6-104">Eye tracking examples</span></span>

<span data-ttu-id="965a6-105">Este tópico descreve como começar rapidamente a usar o controle de olho no MRTK criando exemplos de acompanhamento de olho do MRTK (ativos/MRTK/exemplos/demos/EyeTracking).</span><span class="sxs-lookup"><span data-stu-id="965a6-105">This topic describes how to quickly get started with eye tracking in MRTK by building on MRTK eye tracking examples (Assets/MRTK/Examples/Demos/EyeTracking).</span></span>
<span data-ttu-id="965a6-106">Esses exemplos permitem que você experimente um de nossos novos recursos de entrada do mágico: **acompanhamento ocular**!</span><span class="sxs-lookup"><span data-stu-id="965a6-106">These samples let you experience one of our new magical input capabilities: **Eye tracking**!</span></span>
<span data-ttu-id="965a6-107">A demonstração inclui vários casos de uso, variando de ativações implícitas com base em olhos para como combinar diretamente as informações sobre o que você está vendo com a entrada de **voz** e **mão** .</span><span class="sxs-lookup"><span data-stu-id="965a6-107">The demo includes various use cases, ranging from implicit eye-based activations to how to seamlessly combine information about what you are looking at with **voice** and **hand** input.</span></span>
<span data-ttu-id="965a6-108">Isso permite que os usuários selecionem e movam com rapidez e facilidade o conteúdo do Holographic em sua exibição simplesmente examinando um destino e dizendo _' Select '_ ou executando um gesto de mão.</span><span class="sxs-lookup"><span data-stu-id="965a6-108">This enables users to quickly and effortlessly select and move holographic content across their view simply by looking at a target and saying _'Select'_ or performing a hand gesture.</span></span>
<span data-ttu-id="965a6-109">As demonstrações também incluem um exemplo de rolagem direcionada olhar, panorâmica e zoom de texto e imagens em um Slate.</span><span class="sxs-lookup"><span data-stu-id="965a6-109">The demos also include an example for eye-gaze-directed scroll, pan and zoom of text and images on a slate.</span></span>
<span data-ttu-id="965a6-110">Por fim, um exemplo é fornecido para gravar e visualizar a atenção visual do usuário em um Tablet 2D.</span><span class="sxs-lookup"><span data-stu-id="965a6-110">Finally, an example is provided for recording and visualizing the user's visual attention on a 2D slate.</span></span>
<span data-ttu-id="965a6-111">Na seção a seguir, você encontrará mais detalhes sobre o que cada um dos diferentes exemplos no pacote de exemplo de acompanhamento de olho MRTK (assets/MRTK/examples/demos/EyeTracking) inclui:</span><span class="sxs-lookup"><span data-stu-id="965a6-111">In the following section, you will find more details on what each of the different samples in the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking) includes:</span></span>

![Lista de cenas de acompanhamento de olho](../images/eye-tracking/mrtk_et_list_et_scenes.jpg)

<span data-ttu-id="965a6-113">A seção a seguir é uma rápida visão geral do que são os bastidores da demonstração de controle de olho individual.</span><span class="sxs-lookup"><span data-stu-id="965a6-113">The following section is a quick overview of what the individual eye tracking demo scenes are about.</span></span>
<span data-ttu-id="965a6-114">Os bastidores de demonstração de acompanhamento de olho MRTK são carregados de forma [aditiva](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), o que explicaremos abaixo de como configurar.</span><span class="sxs-lookup"><span data-stu-id="965a6-114">The MRTK eye tracking demo scenes are [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html), which we will explain below how to set up.</span></span>

## <a name="overview-of-the-eye-tracking-demo-samples"></a><span data-ttu-id="965a6-115">Visão geral dos exemplos de demonstração de acompanhamento de olho</span><span class="sxs-lookup"><span data-stu-id="965a6-115">Overview of the eye tracking demo samples</span></span>

### <a name="eye-supported-target-selection"></a>[<span data-ttu-id="965a6-116">**Seleção de destino com suporte de olho**</span><span class="sxs-lookup"><span data-stu-id="965a6-116">**Eye-Supported Target Selection**</span></span>](../input/eye-tracking/eye-tracking-target-selection.md)

<span data-ttu-id="965a6-117">Este tutorial demonstra a facilidade de acessar dados de olhar de olho para selecionar destinos.</span><span class="sxs-lookup"><span data-stu-id="965a6-117">This tutorial showcases the ease of accessing eye gaze data to select targets.</span></span>
<span data-ttu-id="965a6-118">Ele inclui um exemplo para um feedback sutil, mas poderoso, para fornecer ao usuário a confiança de que um alvo está concentrado sem ser impressionante.</span><span class="sxs-lookup"><span data-stu-id="965a6-118">It includes an example for subtle yet powerful feedback to provide the user with the confidence that a target is focused without being overwhelming.</span></span>
<span data-ttu-id="965a6-119">Além disso, há um exemplo simples de notificações inteligentes que desaparecem automaticamente após serem lidas.</span><span class="sxs-lookup"><span data-stu-id="965a6-119">In addition, there is a simple example of smart notifications that automatically disappear after being read.</span></span>

<span data-ttu-id="965a6-120">**Resumo**: seleções de destino rápidas e sem esforço usando uma combinação de olhos, entrada de voz e mão.</span><span class="sxs-lookup"><span data-stu-id="965a6-120">**Summary**: Fast and effortless target selections using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-navigation"></a>[<span data-ttu-id="965a6-121">**Navegação com suporte ocular**</span><span class="sxs-lookup"><span data-stu-id="965a6-121">**Eye-Supported Navigation**</span></span>](../input/eye-tracking/eye-tracking-navigation.md)

<span data-ttu-id="965a6-122">Imagine que você esteja lendo algumas informações em uma exibição distante ou em seu leitor de email e, quando chegar ao final do texto exibido, o texto rolará automaticamente para cima para revelar mais conteúdo.</span><span class="sxs-lookup"><span data-stu-id="965a6-122">Imagine that you are reading some information on a distant display or your e-reader and when you reach the end of the displayed text, the text automatically scrolls up to reveal more content.</span></span>
<span data-ttu-id="965a6-123">Ou que tal ampliar magicamente diretamente para onde você estava olhando?</span><span class="sxs-lookup"><span data-stu-id="965a6-123">Or how about magically zooming directly toward where you were looking at?</span></span>
<span data-ttu-id="965a6-124">Estes são alguns dos exemplos apresentados neste tutorial sobre navegação com suporte ocular.</span><span class="sxs-lookup"><span data-stu-id="965a6-124">These are some of the examples showcased in this tutorial regarding eye-supported navigation.</span></span>
<span data-ttu-id="965a6-125">Além disso, há um exemplo de rotação de mãos livres de hologramas 3D, fazendo com que eles girem automaticamente com base no foco atual.</span><span class="sxs-lookup"><span data-stu-id="965a6-125">In addition, there is an example for hands-free rotation of 3D holograms by making them automatically rotate based on your current focus.</span></span>

<span data-ttu-id="965a6-126">**Resumo:** role, pan, zoom, rotação 3D usando uma combinação de olhos, voz e entrada à mão.</span><span class="sxs-lookup"><span data-stu-id="965a6-126">**Summary**: Scroll, pan, zoom, 3D rotation using a combination of eyes, voice and hand input.</span></span>

### <a name="eye-supported-positioning"></a>[<span data-ttu-id="965a6-127">**Posicionamento com suporte ocular**</span><span class="sxs-lookup"><span data-stu-id="965a6-127">**Eye-Supported Positioning**</span></span>](../input/eye-tracking/eye-tracking-eyes-and-hands.md)

<span data-ttu-id="965a6-128">Este tutorial mostra um cenário de entrada chamado [Put-That-There](https://youtu.be/CbIn8p4_4CQ) voltando à pesquisa do MIT Media Lab no início dos anos 1980 com entrada de olho, mão e voz.</span><span class="sxs-lookup"><span data-stu-id="965a6-128">This tutorial shows an input scenario called [Put-That-There](https://youtu.be/CbIn8p4_4CQ) dating back to research from the MIT Media Lab in the early 1980's with eye, hand and voice input.</span></span>
<span data-ttu-id="965a6-129">A ideia é simples: beneficie-se de seus olhos para seleção e posicionamento rápidos de destino.</span><span class="sxs-lookup"><span data-stu-id="965a6-129">The idea is simple: Benefit from your eyes for fast target selection and positioning.</span></span>
<span data-ttu-id="965a6-130">Basta olhar para um holograma e dizer _"coloque_ isso", veja onde você deseja colocá-lo e diga _"lá!"._</span><span class="sxs-lookup"><span data-stu-id="965a6-130">Simply look at a hologram and say _'put this'_, look over where you want to place it and say _'there!'_.</span></span>
<span data-ttu-id="965a6-131">Para posicionar seu holograma com mais precisão, você pode usar entradas adicionais de suas mãos, voz ou controladores.</span><span class="sxs-lookup"><span data-stu-id="965a6-131">For more precisely positioning your hologram, you can use additional input from your hands, voice or controllers.</span></span>

<span data-ttu-id="965a6-132">**Resumo:** Posicionando hologramas usando os olhos, a voz e a entrada de mão *(arrastar e soltar*).</span><span class="sxs-lookup"><span data-stu-id="965a6-132">**Summary**: Positioning holograms using eyes, voice and hand input (*drag-and-drop*).</span></span> <span data-ttu-id="965a6-133">Controles deslizantes com suporte ocular usando olhos + mãos.</span><span class="sxs-lookup"><span data-stu-id="965a6-133">Eye-supported sliders using eyes + hands.</span></span>

### <a name="visualization-of-visual-attention"></a><span data-ttu-id="965a6-134">**Visualização da atenção visual**</span><span class="sxs-lookup"><span data-stu-id="965a6-134">**Visualization of visual attention**</span></span>

<span data-ttu-id="965a6-135">Os dados com base na aparência dos usuários fazem uma ferramenta extremamente poderosa para avaliar a usabilidade de um design e identificar problemas em fluxos de trabalho eficientes.</span><span class="sxs-lookup"><span data-stu-id="965a6-135">Data based on where users look makes an immensely powerful tool to assess usability of a design and to identify problems in efficient work streams.</span></span>
<span data-ttu-id="965a6-136">Este tutorial aborda diferentes visualizações de acompanhamento ocular e como elas se ajustam a diferentes necessidades.</span><span class="sxs-lookup"><span data-stu-id="965a6-136">This tutorial discusses different eye tracking visualizations and how they fit different needs.</span></span>
<span data-ttu-id="965a6-137">Fornecemos exemplos básicos para registro em log e carregamento de dados de acompanhamento ocular e exemplos de como visualizá-los.</span><span class="sxs-lookup"><span data-stu-id="965a6-137">We provide basic examples for logging and loading eye tracking data and examples for how to visualize them.</span></span>

<span data-ttu-id="965a6-138">**Resumo:** mapa de atenção bidimensional (mapas de calor) em slates.</span><span class="sxs-lookup"><span data-stu-id="965a6-138">**Summary**: Two-dimensional attention map (heatmaps) on slates.</span></span> <span data-ttu-id="965a6-139">Registrando & a reprodução de dados de acompanhamento ocular.</span><span class="sxs-lookup"><span data-stu-id="965a6-139">Recording & replaying eye tracking data.</span></span>

## <a name="setting-up-the-mrtk-eye-tracking-samples"></a><span data-ttu-id="965a6-140">Configurando os exemplos de acompanhamento ocular do MRTK</span><span class="sxs-lookup"><span data-stu-id="965a6-140">Setting up the MRTK eye tracking samples</span></span>

### <a name="prerequisites"></a><span data-ttu-id="965a6-141">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="965a6-141">Prerequisites</span></span>

<span data-ttu-id="965a6-142">Observe que usar os exemplos de acompanhamento de olho no dispositivo requer um HoloLens 2 e um pacote de aplicativo de exemplo criado com o recurso de "entrada olhar" no AppXManifest do pacote.</span><span class="sxs-lookup"><span data-stu-id="965a6-142">Note that using the eye tracking samples on device requires a HoloLens 2 and a sample app package that is built with the "Gaze Input" capability on the package's AppXManifest.</span></span>

<span data-ttu-id="965a6-143">Para usar esses exemplos de acompanhamento de olho no dispositivo, certifique-se de seguir [estas etapas](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) antes de criar o aplicativo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="965a6-143">In order to use these eye tracking samples on device, make sure to follow [these steps](../input/eye-tracking/eye-tracking-basic-setup.md#testing-your-unity-app-on-a-hololens-2) prior to building the app in Visual Studio.</span></span>

### <a name="1-load-eyetrackingdemo-00-rootsceneunity"></a><span data-ttu-id="965a6-144">1. carregar EyeTrackingDemo-00-RootScene. Unity</span><span class="sxs-lookup"><span data-stu-id="965a6-144">1. Load EyeTrackingDemo-00-RootScene.unity</span></span>

<span data-ttu-id="965a6-145">O *EyeTrackingDemo-00-RootScene* é a cena base (_raiz_) que tem todos os componentes principais do MRTK incluídos.</span><span class="sxs-lookup"><span data-stu-id="965a6-145">The *EyeTrackingDemo-00-RootScene* is the base (_root_) scene that has all the core MRTK components included.</span></span>
<span data-ttu-id="965a6-146">Essa é a cena que você precisa carregar primeiro e a partir da qual você executará as demonstrações de controle de olho.</span><span class="sxs-lookup"><span data-stu-id="965a6-146">This is the scene that you need to load first and from which you will run the eye tracking demos.</span></span>
<span data-ttu-id="965a6-147">Ele apresenta um menu de cena gráfica que permite alternar facilmente entre os diferentes exemplos de controle de olho que serão [carregados](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)de forma aditiva.</span><span class="sxs-lookup"><span data-stu-id="965a6-147">It features a graphical scene menu that allows you to easily switch between the different eye tracking samples which will be [loaded additively](https://docs.unity3d.com/ScriptReference/SceneManagement.LoadSceneMode.Additive.html).</span></span>

![Menu cena no exemplo de acompanhamento de olho](../images/eye-tracking/mrtk_et_scenemenu.jpg)

<span data-ttu-id="965a6-149">A cena raiz inclui alguns componentes principais que persistirão em bastidores com carregamento aditivo, como os perfis configurados por MRTK e a câmera de cena.</span><span class="sxs-lookup"><span data-stu-id="965a6-149">The root scene includes a few core components that will persist across the additively loaded scenes, such as the MRTK configured profiles and scene camera.</span></span>
<span data-ttu-id="965a6-150">O _MixedRealityBasicSceneSetup_ (veja a captura de tela abaixo) inclui um script que irá carregar automaticamente a cena referenciada na inicialização.</span><span class="sxs-lookup"><span data-stu-id="965a6-150">The _MixedRealityBasicSceneSetup_ (see screenshot below) includes a script that will automatically load the referenced scene on startup.</span></span>
<span data-ttu-id="965a6-151">Por padrão, isso é _EyeTrackingDemo-02-TargetSelection_.</span><span class="sxs-lookup"><span data-stu-id="965a6-151">By default, this is _EyeTrackingDemo-02-TargetSelection_.</span></span>  

![Exemplo para o script OnLoadStartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

### <a name="2-adding-scenes-to-the-build-menu"></a><span data-ttu-id="965a6-153">2. adicionando cenas ao menu de compilação</span><span class="sxs-lookup"><span data-stu-id="965a6-153">2. Adding scenes to the build menu</span></span>

<span data-ttu-id="965a6-154">Para carregar cenas aditivas durante o tempo de execução, você deve adicionar essas cenas às suas _configurações de Build-> cenas no menu de Build_ primeiro.</span><span class="sxs-lookup"><span data-stu-id="965a6-154">To load additive scenes during runtime, you must add these scenes to your _Build Settings -> Scenes in Build_ menu first.</span></span>
<span data-ttu-id="965a6-155">É importante que a cena raiz seja mostrada como a primeira cena na lista:</span><span class="sxs-lookup"><span data-stu-id="965a6-155">It is important that the root scene is shown as the first scene in the list:</span></span>

![Menu de cena de configurações de compilação para exemplos de acompanhamento de olho](../images/eye-tracking/mrtk_et_build_settings.jpg)

### <a name="3-play-the-eye-tracking-samples-in-the-unity-editor"></a><span data-ttu-id="965a6-157">3. reproduzir os exemplos de acompanhamento de olho no editor do Unity</span><span class="sxs-lookup"><span data-stu-id="965a6-157">3. Play the eye tracking samples in the Unity editor</span></span>

<span data-ttu-id="965a6-158">Depois de adicionar os bastidores de acompanhamento de olho às configurações de compilação e carregar o _EyeTrackingDemo-00-RootScene_, há uma última coisa que você pode querer verificar: é o script _' OnLoadStartScene '_ que está anexado ao _MixedRealityBasicSceneSetup_ gameobject habilitado?</span><span class="sxs-lookup"><span data-stu-id="965a6-158">After adding the eye tracking scenes to the Build Settings and loading the _EyeTrackingDemo-00-RootScene_, there is one last thing you may want to check: Is the _'OnLoadStartScene'_ script that is attached to the _MixedRealityBasicSceneSetup_ GameObject enabled?</span></span> <span data-ttu-id="965a6-159">Isso é para permitir que a cena raiz saiba qual cena de demonstração carregar primeiro.</span><span class="sxs-lookup"><span data-stu-id="965a6-159">This is to let the root scene know which demo scene to load first.</span></span>

![Exemplo para o script de OnLoad_StartScene](../images/eye-tracking/mrtk_et_onloadstartscene.jpg)

<span data-ttu-id="965a6-161">Vamos rolar!</span><span class="sxs-lookup"><span data-stu-id="965a6-161">Let's roll!</span></span> <span data-ttu-id="965a6-162">Toque _em "Reproduzir"_!</span><span class="sxs-lookup"><span data-stu-id="965a6-162">Hit _"Play"_!</span></span>
<span data-ttu-id="965a6-163">Você deverá ver várias gemas aparecerem e o menu de cena na parte superior.</span><span class="sxs-lookup"><span data-stu-id="965a6-163">You should see several gems appear and the scene menu at the top.</span></span>

![Captura de tela de exemplo da cena de seleção de destino ET](../images/eye-tracking/mrtk_et_targetselect.png)

<span data-ttu-id="965a6-165">Você também deve observar um pequeno círculo semitransparente no centro da exibição de jogo.</span><span class="sxs-lookup"><span data-stu-id="965a6-165">You should also notice a small semitransparent circle at the center of your game view.</span></span>
<span data-ttu-id="965a6-166">Isso funciona como um indicador (cursor) do seu olhar _simulado:_ basta pressionar o botão direito do _mouse_ e mover o mouse para alterar sua posição.</span><span class="sxs-lookup"><span data-stu-id="965a6-166">This acts as an indicator (cursor) of your _simulated eye gaze_: Simply press down the _right mouse button_ and move the mouse to change its position.</span></span>
<span data-ttu-id="965a6-167">Quando o cursor estiver sobre as gemas, você observará que ele se ajustará ao centro da gema exibida no momento.</span><span class="sxs-lookup"><span data-stu-id="965a6-167">When the cursor is hovering over the gems, you will notice that it will snap to the center of the currently viewed gem.</span></span>
<span data-ttu-id="965a6-168">Essa é uma ótima maneira de testar se os eventos são disparados conforme o esperado ao _"olhar"_ para um destino.</span><span class="sxs-lookup"><span data-stu-id="965a6-168">This is a great way to test if events are triggered as expected when _"looking"_ at a target.</span></span>
<span data-ttu-id="965a6-169">Esteja ciente de _que_ o olhar simulado por meio do controle do mouse é um suplemento bastante ruim para nossos movimentos de olho rápidos e não intencional.</span><span class="sxs-lookup"><span data-stu-id="965a6-169">Be aware that the _simulated eye gaze_ via mouse control is a rather poor supplement to our rapid and unintentional eye movements.</span></span>
<span data-ttu-id="965a6-170">No entanto, é ótimo testar a funcionalidade básica antes de iterar no design implantando-a no dispositivo HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="965a6-170">However, it is great for testing the basic functionality before iterating on the design by deploying it to the HoloLens 2 device.</span></span>
<span data-ttu-id="965a6-171">Retornando à nossa cena de exemplo de acompanhamento ocular: a gem gira desde que seja analisada e possa ser destruída por "olhar" para ela e ...</span><span class="sxs-lookup"><span data-stu-id="965a6-171">Returning to our eye tracking sample scene: The gem rotates as long as being looked at and can be destroyed by "looking" at it and ...</span></span>

- <span data-ttu-id="965a6-172">Pressionar _Enter_ (que simula dizer "selecionar")</span><span class="sxs-lookup"><span data-stu-id="965a6-172">Pressing _Enter_ (which simulates saying "select")</span></span>
- <span data-ttu-id="965a6-173">Dizendo _"selecionar"_ no microfone</span><span class="sxs-lookup"><span data-stu-id="965a6-173">Saying _"select"_ into your microphone</span></span>
- <span data-ttu-id="965a6-174">Ao pressionar _Espaço para_ mostrar a entrada da mão simulada, clique no botão esquerdo do mouse para executar uma pinçagem simulada</span><span class="sxs-lookup"><span data-stu-id="965a6-174">While pressing _Space_ to show the simulated hand input, click the left mouse button to perform a simulated pinch</span></span>

<span data-ttu-id="965a6-175">Descrevemos mais detalhadamente como você pode obter essas interações em nosso tutorial seleção de destino com [**suporte ocular.**](../input/eye-tracking/eye-tracking-target-selection.md)</span><span class="sxs-lookup"><span data-stu-id="965a6-175">We describe in more detail how you can achieve these interactions in our [**Eye-Supported Target Selection**](../input/eye-tracking/eye-tracking-target-selection.md) tutorial.</span></span>

<span data-ttu-id="965a6-176">Ao mover o cursor para a barra de menus superior na cena, você observará que o item com foco no momento realça subtly.</span><span class="sxs-lookup"><span data-stu-id="965a6-176">When moving the cursor up to the top menu bar in the scene, you will notice that the currently hovered item will highlight subtly.</span></span>
<span data-ttu-id="965a6-177">Você pode selecionar o item realçado no momento usando um dos métodos de confirmação descritos acima (por exemplo, pressionar _Enter_).</span><span class="sxs-lookup"><span data-stu-id="965a6-177">You can select the currently highlighted item by using one of the above described commit methods (e.g., pressing _Enter_).</span></span>
<span data-ttu-id="965a6-178">Dessa forma, você pode alternar entre as diferentes cenas de exemplo de acompanhamento ocular.</span><span class="sxs-lookup"><span data-stu-id="965a6-178">This way you can switch between the different eye tracking sample scenes.</span></span>

### <a name="4-how-to-test-specific-sub-scenes"></a><span data-ttu-id="965a6-179">4. Como testar sub-cenas específicas</span><span class="sxs-lookup"><span data-stu-id="965a6-179">4. How to test specific sub scenes</span></span>

<span data-ttu-id="965a6-180">Ao trabalhar em um cenário específico, talvez você não queira passar pelo menu de cena toda vez.</span><span class="sxs-lookup"><span data-stu-id="965a6-180">When working on a specific scenario, you may not want to go through the scene menu every time.</span></span>
<span data-ttu-id="965a6-181">Em vez disso, talvez você queira começar diretamente da cena em que está trabalhando no momento ao pressionar o _botão_ Reproduzir.</span><span class="sxs-lookup"><span data-stu-id="965a6-181">Instead, you may want to start directly from the scene that you are currently working on when pressing the _Play_ button.</span></span>
<span data-ttu-id="965a6-182">Sem problemas.</span><span class="sxs-lookup"><span data-stu-id="965a6-182">No problem!</span></span> <span data-ttu-id="965a6-183">Veja o que você pode fazer:</span><span class="sxs-lookup"><span data-stu-id="965a6-183">Here is what you can do:</span></span>

1. <span data-ttu-id="965a6-184">Carregar a cena _raiz_</span><span class="sxs-lookup"><span data-stu-id="965a6-184">Load the _root_ scene</span></span>
2. <span data-ttu-id="965a6-185">Na cena _raiz_ , desabilite o script _' OnLoadStartScene '_</span><span class="sxs-lookup"><span data-stu-id="965a6-185">In the _root_ scene, disable the _'OnLoadStartScene'_ script</span></span>
3. <span data-ttu-id="965a6-186">_Arraste e solte_ um dos cenas de teste de controle ocular descritos abaixo (ou qualquer outra cena) em sua exibição de _hierarquia_ , conforme mostrado na captura de tela abaixo.</span><span class="sxs-lookup"><span data-stu-id="965a6-186">_Drag and drop_ one of the eye tracking test scenes that are described below (or any other scene) into your _Hierarchy_ view as shown in the screenshot below.</span></span>

    ![Exemplo de cena aditiva](../images/eye-tracking/mrtk_et_additivescene.jpg)

4. <span data-ttu-id="965a6-188">Pressione _reproduzir_</span><span class="sxs-lookup"><span data-stu-id="965a6-188">Press _Play_</span></span>

<span data-ttu-id="965a6-189">Observe que o carregamento da sub-rotina como esta não é persistente: isso significa que, se você implantar seu aplicativo no dispositivo do HoloLens 2, ele carregará apenas a cena raiz (supondo que ela apareça na parte superior das configurações de Build).</span><span class="sxs-lookup"><span data-stu-id="965a6-189">Please note that loading the sub scene like this is not persistent: This means that if you deploy your app to the HoloLens 2 device, it will only load the root scene (assuming it appears at the top of your Build Settings).</span></span>
<span data-ttu-id="965a6-190">Além disso, quando você compartilha seu projeto com outras pessoas, os sub-cenas não são carregados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="965a6-190">Also, when you share your project with others, the sub scenes are not automatically loaded.</span></span>

---

<span data-ttu-id="965a6-191">Agora que você sabe como fazer as cenas de exemplo de acompanhamento de olho do MRTK para funcionar, vamos continuar com mais detalhes sobre como selecionar hologramas com seus olhos: [seleção de destino com suporte de olho](../input/eye-tracking/eye-tracking-target-selection.md).</span><span class="sxs-lookup"><span data-stu-id="965a6-191">Now that you know how to get the MRTK eye tracking example scenes to work, let's continue with diving deeper into how to select holograms with your eyes: [Eye-supported target selection](../input/eye-tracking/eye-tracking-target-selection.md).</span></span>

---
[<span data-ttu-id="965a6-192">Voltar para "acompanhamento de olho no MixedRealityToolkit"</span><span class="sxs-lookup"><span data-stu-id="965a6-192">Back to "Eye tracking in the MixedRealityToolkit"</span></span>](../input/eye-tracking/eye-tracking-Main.md)
