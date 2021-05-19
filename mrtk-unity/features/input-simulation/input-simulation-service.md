---
title: Serviços de Simulação de Entrada
description: Documentação sobre o serviço de simulação de entrada no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 81e7dcab7e0f349d05521f93d75bba6927761fd1
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145095"
---
# <a name="input-simulation-service"></a><span data-ttu-id="169fe-104">Serviço de simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="169fe-104">Input simulation service</span></span>

<span data-ttu-id="169fe-105">O Serviço de Simulação de Entrada emula o comportamento de dispositivos e plataformas que podem não estar disponíveis no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="169fe-105">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="169fe-106">Os exemplos incluem:</span><span class="sxs-lookup"><span data-stu-id="169fe-106">Examples include:</span></span>

* <span data-ttu-id="169fe-107">Acompanhamento de cabeça do dispositivo HoloLens ou VR</span><span class="sxs-lookup"><span data-stu-id="169fe-107">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="169fe-108">Gestos de mão do HoloLens</span><span class="sxs-lookup"><span data-stu-id="169fe-108">HoloLens hand gestures</span></span>
* <span data-ttu-id="169fe-109">Acompanhamento de mão articulado do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="169fe-109">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="169fe-110">Acompanhamento ocular do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="169fe-110">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="169fe-111">Controladores de dispositivo VR</span><span class="sxs-lookup"><span data-stu-id="169fe-111">VR device controllers</span></span>

<span data-ttu-id="169fe-112">Os usuários podem usar uma combinação convencional de teclado e mouse para controlar dispositivos simulados em runtime.</span><span class="sxs-lookup"><span data-stu-id="169fe-112">Users can use a conventional keyboard and mouse combination to control simulated devices at runtime.</span></span> <span data-ttu-id="169fe-113">Essa abordagem permite o teste de interações no editor do Unity sem primeiro implantar em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="169fe-113">This approach allows testing of interactions in the Unity editor without first deploying to a device.</span></span>

> [!WARNING]
> <span data-ttu-id="169fe-114">Isso não funciona ao usar a Emulação Holográfica XR do Unity > Modo de Emulação = "Simular no Editor".</span><span class="sxs-lookup"><span data-stu-id="169fe-114">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="169fe-115">A simulação no editor do Unity assumirá o controle da simulação de entrada do MRTK.</span><span class="sxs-lookup"><span data-stu-id="169fe-115">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="169fe-116">Para usar o serviço de simulação de entrada do MRTK, você precisará definir a Emulação Holográfica do XR para o Modo de Emulação = *"Nenhum"*</span><span class="sxs-lookup"><span data-stu-id="169fe-116">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="169fe-117">Habilitando o serviço de simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="169fe-117">Enabling the input simulation service</span></span>

<span data-ttu-id="169fe-118">A simulação de entrada é habilitada por padrão nos perfis que são fornecidas com o MRTK.</span><span class="sxs-lookup"><span data-stu-id="169fe-118">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span>

<span data-ttu-id="169fe-119">Na configuração do provedor de dados do sistema de entrada, o serviço de Simulação de Entrada pode ser configurado com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="169fe-119">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="169fe-120">**O** tipo deve ser *Microsoft.MixedReality.Toolkit.Input > InputSimulationService.*</span><span class="sxs-lookup"><span data-stu-id="169fe-120">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="169fe-121">**As plataformas com suporte por** padrão incluem todas as plataformas *do Editor,* pois o serviço usa a entrada do teclado e do mouse.</span><span class="sxs-lookup"><span data-stu-id="169fe-121">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="169fe-122">O serviço de Simulação de Entrada pode ser usado em outros pontos de extremidade de plataforma, como autônomos, alterando a propriedade **Plataformas** com Suporte para incluir os destinos desejados.</span><span class="sxs-lookup"><span data-stu-id="169fe-122">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <span data-ttu-id="169fe-123">![Plataformas com suporte para a simulação de entrada](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span><span class="sxs-lookup"><span data-stu-id="169fe-123">![Input Simulation Supported Platforms](../images/input-simulation/InputSimulationSupportedPlatforms.gif)</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="169fe-124">Janela de ferramentas de simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="169fe-124">Input simulation tools window</span></span>

<span data-ttu-id="169fe-125">Habilite a janela ferramentas de simulação de entrada do menu de simulação de entrada do **Kit de ferramentas da realidade misturada**  >    >   .</span><span class="sxs-lookup"><span data-stu-id="169fe-125">Enable the input simulation tools window from the  **Mixed Reality Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="169fe-126">Esta janela fornece acesso ao estado da simulação de entrada durante o modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="169fe-126">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons"></a><span data-ttu-id="169fe-127">Botões do visor</span><span class="sxs-lookup"><span data-stu-id="169fe-127">Viewport buttons</span></span>

<span data-ttu-id="169fe-128">Um pré-fabricado para botões no editor para controlar o posicionamento básico pode ser especificado no perfil de simulação de entrada em **indicadores pré-fabricado**.</span><span class="sxs-lookup"><span data-stu-id="169fe-128">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="169fe-129">Esse é um utilitário opcional, os mesmos recursos podem ser acessados na [janela ferramentas de simulação de entrada](#input-simulation-tools-window).</span><span class="sxs-lookup"><span data-stu-id="169fe-129">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="169fe-130">Os indicadores do visor são desabilitados por padrão, pois eles podem, às vezes, interferir nas interações da interface do usuário do Unity.</span><span class="sxs-lookup"><span data-stu-id="169fe-130">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="169fe-131">Consulte o problema [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span><span class="sxs-lookup"><span data-stu-id="169fe-131">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="169fe-132">Para habilitar, adicione InputSimulationIndicators pré-fabricado aos **indicadores pré-fabricado**.</span><span class="sxs-lookup"><span data-stu-id="169fe-132">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="169fe-133">Os ícones de mão mostram o estado das mãos simuladas:</span><span class="sxs-lookup"><span data-stu-id="169fe-133">Hand icons show the state of the simulated hands:</span></span>

* ![Ícone de mão não controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="169fe-135&quot;>A mão não está acompanhando.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;169fe-135&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;169fe-136&quot;>Clique para habilitar a mão.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;169fe-136&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;169fe-137&quot;>![Ícone de mão controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;Ícone de mão controlada") A mão é controlada, mas não é controlada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="169fe-137">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="169fe-138">Clique para ocultar a mão.</span><span class="sxs-lookup"><span data-stu-id="169fe-138">Click to hide the hand.</span></span>
* <span data-ttu-id="169fe-139">![Ícone de mão controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Ícone de mão controlada") A mão é controlada e controlada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="169fe-139">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="169fe-140">Clique para ocultar a mão.</span><span class="sxs-lookup"><span data-stu-id="169fe-140">Click to hide the hand.</span></span>
* <span data-ttu-id="169fe-141">![Ícone de redefinir mão](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Ícone de redefinição da mão") Clique para redefinir a mão para a posição padrão.</span><span class="sxs-lookup"><span data-stu-id="169fe-141">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="169fe-142">Na folha de consulta de simulação de entrada do editor</span><span class="sxs-lookup"><span data-stu-id="169fe-142">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="169fe-143">Pressione Ctrl + H na cena HandInteractionExamples para abrir uma folha de consulta com controles de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="169fe-143">Press Left Ctrl + H in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

![Roteiro de simulação de entrada](https://user-images.githubusercontent.com/39840334/86066480-13637f00-ba27-11ea-8814-d222d548f684.gif)

## <a name="camera-control"></a><span data-ttu-id="169fe-145">Controle de câmera</span><span class="sxs-lookup"><span data-stu-id="169fe-145">Camera control</span></span>

<span data-ttu-id="169fe-146">A movimentação de cabeçalho pode ser emulada pelo serviço de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="169fe-146">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="169fe-147">Girando a câmera</span><span class="sxs-lookup"><span data-stu-id="169fe-147">Rotating the camera</span></span>

1. <span data-ttu-id="169fe-148">Passe o mouse sobre a janela do editor do visor.</span><span class="sxs-lookup"><span data-stu-id="169fe-148">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="169fe-149">*Talvez seja necessário clicar na janela para dar um foco de entrada se os pressionamentos de botão não funcionarem.*</span><span class="sxs-lookup"><span data-stu-id="169fe-149">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="169fe-150">Pressione e segure o **botão de aparência do mouse** (padrão: botão direito do mouse).</span><span class="sxs-lookup"><span data-stu-id="169fe-150">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="169fe-151">Mova o mouse na janela do visor para girar a câmera.</span><span class="sxs-lookup"><span data-stu-id="169fe-151">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="169fe-152">Use a roda de rolagem para rolar a câmera pela direção da exibição.</span><span class="sxs-lookup"><span data-stu-id="169fe-152">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="169fe-153">A velocidade de rotação da câmera pode ser configurada alterando a configuração de **velocidade de aparência do mouse** no perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="169fe-153">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="169fe-154">Como alternativa, use a aparência **horizontal** / com eixos **verticais** para girar a câmera (padrão: Game Controller Right Thumbstick).</span><span class="sxs-lookup"><span data-stu-id="169fe-154">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="169fe-155">Movimentação da câmera</span><span class="sxs-lookup"><span data-stu-id="169fe-155">Moving the camera</span></span>

<span data-ttu-id="169fe-156">Use os eixos verticais mover **horizontalmente** /  para mover a câmera (padrão: WASD chaves ou controlador de jogo para a esquerda Thumbstick).</span><span class="sxs-lookup"><span data-stu-id="169fe-156">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="169fe-157">A posição da câmera e os ângulos de rotação também podem ser definidos explicitamente na janela ferramentas.</span><span class="sxs-lookup"><span data-stu-id="169fe-157">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="169fe-158">A câmera pode ser redefinida para o padrão usando o botão **Redefinir** .</span><span class="sxs-lookup"><span data-stu-id="169fe-158">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="169fe-159">Simulação de controlador</span><span class="sxs-lookup"><span data-stu-id="169fe-159">Controller simulation</span></span>

<span data-ttu-id="169fe-160">A simulação de entrada dá suporte a dispositivos de controlador emulados (ou seja, controladores de movimento e mãos).</span><span class="sxs-lookup"><span data-stu-id="169fe-160">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="169fe-161">Esses controladores virtuais podem interagir com qualquer objeto que ofereça suporte a controladores regulares, como botões ou objetos que podem ser capturados.</span><span class="sxs-lookup"><span data-stu-id="169fe-161">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="169fe-162">Modo de simulação do controlador</span><span class="sxs-lookup"><span data-stu-id="169fe-162">Controller simulation mode</span></span>

<span data-ttu-id="169fe-163">Na [janela ferramentas de simulação de entrada](#input-simulation-tools-window) , a configuração do modo de simulação do **controlador padrão** alterna entre três modelos de entrada distintos.</span><span class="sxs-lookup"><span data-stu-id="169fe-163">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="169fe-164">Esse modo padrão também pode ser definido no perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="169fe-164">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="169fe-165">*Mãos articuladas:* simula um dispositivo de mão totalmente articulado com dados de posição conjunta.</span><span class="sxs-lookup"><span data-stu-id="169fe-165">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="169fe-166">Emula o modelo de interação do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="169fe-166">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="169fe-167">As interações baseadas no posicionamento preciso da mão ou no toque de uso podem ser simuladas nesse modo.</span><span class="sxs-lookup"><span data-stu-id="169fe-167">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="169fe-168">*Gestos de mão:* simula um modelo de mão simplificado com toque de ar e gestos básicos.</span><span class="sxs-lookup"><span data-stu-id="169fe-168">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="169fe-169">Emula o [modelo de interação do HoloLens.](/windows/mixed-reality/gestures)</span><span class="sxs-lookup"><span data-stu-id="169fe-169">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="169fe-170">O foco é controlado usando o ponteiro De foco.</span><span class="sxs-lookup"><span data-stu-id="169fe-170">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="169fe-171">O *gesto de toque* de ar é usado para interagir com botões.</span><span class="sxs-lookup"><span data-stu-id="169fe-171">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="169fe-172">*Controlador de Movimento:* simula um controlador de movimento usado com headsets vr que funciona de forma semelhante a interações distantes com mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="169fe-172">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="169fe-173">Emula o headset VR com o modelo de interação de controladores.</span><span class="sxs-lookup"><span data-stu-id="169fe-173">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="169fe-174">As teclas de gatilho, de captura e de menu são simuladas por meio da entrada do teclado e do mouse.</span><span class="sxs-lookup"><span data-stu-id="169fe-174">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="169fe-175">Simulando a movimentação do controlador</span><span class="sxs-lookup"><span data-stu-id="169fe-175">Simulating controller movement</span></span>

<span data-ttu-id="169fe-176">Pressione e mantenha pressionada a Tecla de Manipulação do  Controlador **esquerdo/direito** (padrão:  Deslocamento para a esquerda para o controlador esquerdo e Espaço para o controlador direito) para obter controle de qualquer controlador.</span><span class="sxs-lookup"><span data-stu-id="169fe-176">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="169fe-177">Enquanto a tecla de manipulação é pressionada, o controlador aparecerá no viewport.</span><span class="sxs-lookup"><span data-stu-id="169fe-177">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="169fe-178">Depois que a chave de manipulação for liberada, os controladores desaparecerão depois de um curto Tempo de O tempo **de ocultação do controlador.**</span><span class="sxs-lookup"><span data-stu-id="169fe-178">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="169fe-179">Os controladores podem ser alternados e congelados em relação à câmera na janela de ferramentas de simulação de entrada ou pressionando a tecla Alternar Para a **esquerda/direita** do controlador (padrão: [](#input-simulation-tools-window) *T* para a esquerda e *Y* para a direita).</span><span class="sxs-lookup"><span data-stu-id="169fe-179">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="169fe-180">Pressione a tecla de alternância novamente para ocultar os controladores novamente.</span><span class="sxs-lookup"><span data-stu-id="169fe-180">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="169fe-181">Para manipular os controladores, a chave de manipulação do controlador **esquerdo/direito** precisa ser mantida.</span><span class="sxs-lookup"><span data-stu-id="169fe-181">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="169fe-182">Tocar duas vezes **na Tecla de Manipulação do** Controlador Para a Esquerda/Direita também pode alternar os controladores para cima/para fora.</span><span class="sxs-lookup"><span data-stu-id="169fe-182">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="169fe-183">O movimento do mouse move o controlador no plano de exibição.</span><span class="sxs-lookup"><span data-stu-id="169fe-183">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="169fe-184">Os controladores podem ser movidos mais ou mais perto da câmera usando a **roda do mouse**.</span><span class="sxs-lookup"><span data-stu-id="169fe-184">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="169fe-185">Para girar os controladores usando o mouse, mantenha a **tecla de manipulação do controlador à esquerda/direita** (*deslocamento à esquerda* ou o *espaço*) *e* o **botão de rotação do controlador** (padrão: botão *CTRL esquerda* ) e, em seguida, mova o mouse para girar o controlador.</span><span class="sxs-lookup"><span data-stu-id="169fe-185">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="169fe-186">A velocidade de rotação do controlador pode ser configurada alterando a configuração de **velocidade de rotação do controlador do mouse** no perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="169fe-186">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="169fe-187">Todo o posicionamento manual também pode ser alterado na [janela ferramentas de simulação de entrada](#input-simulation-tools-window), incluindo redefinição de mãos para padrão.</span><span class="sxs-lookup"><span data-stu-id="169fe-187">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="169fe-188">Configurações de perfil adicionais</span><span class="sxs-lookup"><span data-stu-id="169fe-188">Additional profile settings</span></span>

* <span data-ttu-id="169fe-189">O **multiplicador de profundidade do controlador** controla a sensibilidade da movimentação de profundidade da roda de rolagem do mouse.</span><span class="sxs-lookup"><span data-stu-id="169fe-189">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="169fe-190">Um número maior acelerará o zoom do controlador.</span><span class="sxs-lookup"><span data-stu-id="169fe-190">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="169fe-191">A **distância do controlador padrão** é a distância inicial dos controladores da câmera.</span><span class="sxs-lookup"><span data-stu-id="169fe-191">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="169fe-192">Clicar nos controladores de botão **Redefinir** também irá posicionar os controladores nessa distância.</span><span class="sxs-lookup"><span data-stu-id="169fe-192">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="169fe-193">O **valor de Tremulação do controlador** adiciona movimento aleatório aos controladores.</span><span class="sxs-lookup"><span data-stu-id="169fe-193">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="169fe-194">Esse recurso pode ser usado para simular o controle de controlador impreciso no dispositivo e garantir que as interações funcionem bem com entradas ruidosas.</span><span class="sxs-lookup"><span data-stu-id="169fe-194">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="169fe-195">Gestos de mão</span><span class="sxs-lookup"><span data-stu-id="169fe-195">Hand gestures</span></span>

<span data-ttu-id="169fe-196">Gestos de mão como pinçagem, captura, investigar, etc. também podem ser simulados.</span><span class="sxs-lookup"><span data-stu-id="169fe-196">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="169fe-197">Habilitar o controle de mão usando a **tecla de manipulação do controlador à esquerda/direita** (*deslocamento à esquerda* ou *espaço*)</span><span class="sxs-lookup"><span data-stu-id="169fe-197">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="169fe-198">Durante a manipulação, pressione e mantenha pressionado um botão do mouse para executar um gesto de mão.</span><span class="sxs-lookup"><span data-stu-id="169fe-198">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="169fe-199">Cada um dos botões do mouse pode ser mapeado para transformar a forma mão em um gesto diferente usando as configurações de *gesto esquerdo/médio/direito do mouse* .</span><span class="sxs-lookup"><span data-stu-id="169fe-199">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="169fe-200">O *gesto de mão padrão* é a forma da mão quando nenhum botão é pressionado.</span><span class="sxs-lookup"><span data-stu-id="169fe-200">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="169fe-201">O gesto de *pinçar* é o único gesto que executa a ação "selecionar" neste ponto.</span><span class="sxs-lookup"><span data-stu-id="169fe-201">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="169fe-202">Manipulação unidirecional</span><span class="sxs-lookup"><span data-stu-id="169fe-202">One-hand manipulation</span></span>

1. <span data-ttu-id="169fe-203">Pressione e mantenha a **tecla de manipulação da controladora esquerda/direita** (*SHIFT esquerda* ou *espaço*)</span><span class="sxs-lookup"><span data-stu-id="169fe-203">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="169fe-204">Ponto no objeto</span><span class="sxs-lookup"><span data-stu-id="169fe-204">Point at object</span></span>
3. <span data-ttu-id="169fe-205">Mantenha o botão do mouse pressionado para pinçar</span><span class="sxs-lookup"><span data-stu-id="169fe-205">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="169fe-206">Use o mouse para mover o objeto</span><span class="sxs-lookup"><span data-stu-id="169fe-206">Use your mouse to move the object</span></span>
5. <span data-ttu-id="169fe-207">Liberar o botão do mouse para interromper a interação</span><span class="sxs-lookup"><span data-stu-id="169fe-207">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="169fe-208">Manipulação de duas mãos</span><span class="sxs-lookup"><span data-stu-id="169fe-208">Two-hand manipulation</span></span>

<span data-ttu-id="169fe-209">Para manipular objetos com duas mãos ao mesmo tempo, o modo de mão persistente é recomendado.</span><span class="sxs-lookup"><span data-stu-id="169fe-209">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="169fe-210">Alterne em ambas as mãos pressionando as teclas de alternância (*T/Y*).</span><span class="sxs-lookup"><span data-stu-id="169fe-210">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="169fe-211">Manipular uma mão por vez:</span><span class="sxs-lookup"><span data-stu-id="169fe-211">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="169fe-212">Mantenha **o espaço** para controlar o lado direito</span><span class="sxs-lookup"><span data-stu-id="169fe-212">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="169fe-213">Mova a mão para onde você deseja pegar o objeto</span><span class="sxs-lookup"><span data-stu-id="169fe-213">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="169fe-214">Pressione o **botão esquerdo do mouse** para ativar o gesto de *pinçar.*</span><span class="sxs-lookup"><span data-stu-id="169fe-214">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="169fe-215">Liberar **Espaço para** parar de controlar o lado direito.</span><span class="sxs-lookup"><span data-stu-id="169fe-215">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="169fe-216">A mão será congelada no local e será bloqueada no gesto *de pinçar,* pois ela não está mais sendo manipulada.</span><span class="sxs-lookup"><span data-stu-id="169fe-216">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="169fe-217">Repita o processo com a outra mão, segurando o mesmo objeto em um segundo ponto.</span><span class="sxs-lookup"><span data-stu-id="169fe-217">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="169fe-218">Agora que ambas as mãos estão segurando o mesmo objeto, você pode mover qualquer uma delas para executar a manipulação de duas mãos.</span><span class="sxs-lookup"><span data-stu-id="169fe-218">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="169fe-219">Interação de GGV (olhar, gesto e voz)</span><span class="sxs-lookup"><span data-stu-id="169fe-219">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="169fe-220">Por padrão, a interação GGV é habilitada no editor enquanto não há mãos articuladas presentes na cena.</span><span class="sxs-lookup"><span data-stu-id="169fe-220">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="169fe-221">Girar a câmera para apontar o cursor de olhar para o objeto interajante (botão direito do mouse)</span><span class="sxs-lookup"><span data-stu-id="169fe-221">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="169fe-222">Clique e mantenha o **botão esquerdo do mouse pressionado** para interagir</span><span class="sxs-lookup"><span data-stu-id="169fe-222">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="169fe-223">Girar a câmera novamente para manipular o objeto</span><span class="sxs-lookup"><span data-stu-id="169fe-223">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="169fe-224">Você pode desativar isso ativando a opção *Is Hand Free Input Enabled* dentro do Perfil de Simulação de Entrada.</span><span class="sxs-lookup"><span data-stu-id="169fe-224">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="169fe-225">Além disso, você pode usar as mãos simuladas para a interação GGV</span><span class="sxs-lookup"><span data-stu-id="169fe-225">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="169fe-226">Habilitar a simulação de GGV alternando o **modo de simulação** para *gestos* no [perfil de simulação de entrada](#enabling-the-input-simulation-service)</span><span class="sxs-lookup"><span data-stu-id="169fe-226">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="169fe-227">Girar a câmera para apontar o cursor olhar no objeto que interage (botão direito do mouse)</span><span class="sxs-lookup"><span data-stu-id="169fe-227">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="169fe-228">Mantenha **espaço** para controlar a mão direita</span><span class="sxs-lookup"><span data-stu-id="169fe-228">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="169fe-229">Clique e mantenha o **botão esquerdo do mouse** para interagir</span><span class="sxs-lookup"><span data-stu-id="169fe-229">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="169fe-230">Use o mouse para mover o objeto</span><span class="sxs-lookup"><span data-stu-id="169fe-230">Use your mouse to move the object</span></span>
1. <span data-ttu-id="169fe-231">Solte o botão do mouse para parar a interação</span><span class="sxs-lookup"><span data-stu-id="169fe-231">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="169fe-232">Gerando eventos teleport</span><span class="sxs-lookup"><span data-stu-id="169fe-232">Raising Teleport Events</span></span>

<span data-ttu-id="169fe-233">Para gerar o evento teleport na simulação de entrada, defina as configurações de gesto da mão no perfil de simulação de entrada para que um execute o gesto de **início teleport** enquanto o outro executa o gesto de **término teleport** .</span><span class="sxs-lookup"><span data-stu-id="169fe-233">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="169fe-234">O gesto de **início de teleport** abrirá o ponteiro teleport, enquanto o Gesure **teleport end** concluirá a ação teleport e moverá o usuário.</span><span class="sxs-lookup"><span data-stu-id="169fe-234">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="169fe-235">A posição y de seu teleport resultante depende do deslocamento da câmera ao longo do eixo y.</span><span class="sxs-lookup"><span data-stu-id="169fe-235">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="169fe-236">No editor, isso é 0 por padrão. portanto, use as teclas **Q** e **e** para ajustá-la à altura apropriada.</span><span class="sxs-lookup"><span data-stu-id="169fe-236">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![Configurações de teleport de simulação de entrada](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="169fe-238">Interação do controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="169fe-238">Motion controller interaction</span></span>

<span data-ttu-id="169fe-239">Os controladores de movimento simulados podem ser manipulados da mesma forma que as mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="169fe-239">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="169fe-240">O modelo de interação é semelhante à interação extrema da mão articulada enquanto o gatilho, as teclas de captura e de menu são mapeadas para o *botão esquerdo do mouse*, a tecla *G* e *M* , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="169fe-240">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="169fe-241">Acompanhamento ocular</span><span class="sxs-lookup"><span data-stu-id="169fe-241">Eye tracking</span></span>

<span data-ttu-id="169fe-242">A [simulação de acompanhamento de olho](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) pode ser habilitada verificando a opção **simular posição de olho** no perfil de simulação de [entrada](#enabling-the-input-simulation-service).</span><span class="sxs-lookup"><span data-stu-id="169fe-242">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="169fe-243">Isso não deve ser usado com interações de estilo de controlador de movimento ou GGV (portanto, certifique-se de que o **modo de simulação de controlador padrão** esteja definido para a *mão articulada*).</span><span class="sxs-lookup"><span data-stu-id="169fe-243">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="see-also"></a><span data-ttu-id="169fe-244">Confira também</span><span class="sxs-lookup"><span data-stu-id="169fe-244">See also</span></span>

* <span data-ttu-id="169fe-245">[Perfil do sistema de entrada](../input/input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="169fe-245">[Input System profile](../input/input-providers.md).</span></span>