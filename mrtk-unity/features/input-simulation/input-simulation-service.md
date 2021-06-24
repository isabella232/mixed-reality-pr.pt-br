---
title: Serviços de simulação de entrada
description: Documentação sobre o serviço de simulação de entrada no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 5420f3f2d20d07585007a58f5cf70d8e2027efc6
ms.sourcegitcommit: c08997a75acfe4ac1d044c0fb9112e6817eb3d45
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2021
ms.locfileid: "112588840"
---
# <a name="input-simulation-service"></a><span data-ttu-id="8615e-104">Serviço de simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="8615e-104">Input simulation service</span></span>

![Simulação de entrada MRTK](../images/input-simulation/MRTK_InputSimulation_Hero.jpg)

<span data-ttu-id="8615e-106">Com a simulação de entrada do MRTK, você pode testar vários tipos de interações no editor do Unity sem compilar e implantar em um dispositivo.</span><span class="sxs-lookup"><span data-stu-id="8615e-106">With MRTK's input simulation, you can test various types of interactions in the Unity editor without building and deploying to a device.</span></span> <span data-ttu-id="8615e-107">Isso permite que você itere rapidamente suas ideias no processo de design e desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8615e-107">This allows you quickly iterate your ideas in the design and development process.</span></span> <span data-ttu-id="8615e-108">Use combinações de teclado e mouse para controlar as entradas simuladas.</span><span class="sxs-lookup"><span data-stu-id="8615e-108">Use keyboard and mouse combinations to control simulated inputs.</span></span>

<span data-ttu-id="8615e-109">O serviço de simulação de entrada emula o comportamento de dispositivos e plataformas que podem não estar disponíveis no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="8615e-109">The Input Simulation Service emulates the behavior of devices and platforms that may not be available in the Unity editor.</span></span> <span data-ttu-id="8615e-110">Os exemplos incluem:</span><span class="sxs-lookup"><span data-stu-id="8615e-110">Examples include:</span></span>

* <span data-ttu-id="8615e-111">Rastreamento de cabeça do dispositivo HoloLens ou VR</span><span class="sxs-lookup"><span data-stu-id="8615e-111">HoloLens or VR device head tracking</span></span>
* <span data-ttu-id="8615e-112">Gestos do HoloLens Hand</span><span class="sxs-lookup"><span data-stu-id="8615e-112">HoloLens hand gestures</span></span>
* <span data-ttu-id="8615e-113">Acompanhamento de mão articulada 2 do HoloLens</span><span class="sxs-lookup"><span data-stu-id="8615e-113">HoloLens 2 articulated hand tracking</span></span>
* <span data-ttu-id="8615e-114">Acompanhamento de olho do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="8615e-114">HoloLens 2 eye tracking</span></span>
* <span data-ttu-id="8615e-115">Controladores de dispositivo VR</span><span class="sxs-lookup"><span data-stu-id="8615e-115">VR device controllers</span></span>

> [!WARNING]
> <span data-ttu-id="8615e-116">Isso não funciona ao usar o modo de emulação de > de emulação de Holographic do Unity = "simular no editor".</span><span class="sxs-lookup"><span data-stu-id="8615e-116">This does not work when using Unity's XR Holographic Emulation > Emulation Mode = "Simulate in Editor".</span></span> <span data-ttu-id="8615e-117">A simulação no editor do Unity assumirá o controle da simulação de entrada do MRTK.</span><span class="sxs-lookup"><span data-stu-id="8615e-117">Unity's in-editor simulation will take control away from MRTK's input simulation.</span></span> <span data-ttu-id="8615e-118">Para usar o serviço de simulação de entrada do MRTK, você precisará definir a emulação de Holographic de XR para o modo de emulação = *"nenhum"*</span><span class="sxs-lookup"><span data-stu-id="8615e-118">In order to use the MRTK input simulation service, you will need to set XR Holographic Emulation to Emulation Mode = *"None"*</span></span>

## <a name="how-to-use-mrtk-input-simulation"></a><span data-ttu-id="8615e-119">Como usar a simulação de entrada do MRTK</span><span class="sxs-lookup"><span data-stu-id="8615e-119">How to use MRTK Input simulation</span></span> 

<span data-ttu-id="8615e-120">A simulação de entrada é habilitada por padrão nos perfis fornecidos com MRTK.</span><span class="sxs-lookup"><span data-stu-id="8615e-120">Input simulation is enabled by default in the profiles that ship with MRTK.</span></span> <span data-ttu-id="8615e-121">Você pode simplesmente clicar no botão **executar** para executar a cena com suporte à simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="8615e-121">You can simply click **Play** button to run the scene with input simulation support.</span></span>

* <span data-ttu-id="8615e-122">Pressione **W, A, S, D, Q e** as teclas e para mover a câmera.</span><span class="sxs-lookup"><span data-stu-id="8615e-122">Press **W, A, S, D, Q, E** keys to move the camera.</span></span>
* <span data-ttu-id="8615e-123">Mantenha o **botão direito do mouse** e mova o mouse para examinar.</span><span class="sxs-lookup"><span data-stu-id="8615e-123">Hold the **Right mouse button** and move the mouse to look around.</span></span>
* <span data-ttu-id="8615e-124">Para exibir as mãos simuladas, pressione a **barra de espaço (à direita)** ou a **tecla SHIFT esquerda (à esquerda)**</span><span class="sxs-lookup"><span data-stu-id="8615e-124">To bring up the simulated hands, press **Space bar(Right hand)** or **Left Shift key(Left hand)**</span></span>
* <span data-ttu-id="8615e-125">Para manter as mãos simuladas na exibição, pressione **T** ou a tecla **Y**</span><span class="sxs-lookup"><span data-stu-id="8615e-125">To keep simulated hands in the view, press **T** or **Y** key</span></span>
* <span data-ttu-id="8615e-126">Para girar as mãos simuladas, pressione e segure a **tecla CTRL** e mova o mouse</span><span class="sxs-lookup"><span data-stu-id="8615e-126">To rotate simulated hands, press and hold **Ctrl key** and move mouse</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4OYrm]

## <a name="in-editor-input-simulation-cheat-sheet"></a><span data-ttu-id="8615e-127">Na folha de consulta de simulação de entrada do editor</span><span class="sxs-lookup"><span data-stu-id="8615e-127">In editor input simulation cheat sheet</span></span>

<span data-ttu-id="8615e-128">Pressione **Ctrl + H** na cena HandInteractionExamples para abrir uma folha de consulta com controles de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="8615e-128">Press **Left Ctrl + H** in the HandInteractionExamples scene to bring up a cheat sheet with Input simulation controls.</span></span>

> ![Roteiro de MRTK de simulação de entrada](../images/input-simulation/MRTK_InputSimulation_CheatSheet.png)


## <a name="enabling-the-input-simulation-service"></a><span data-ttu-id="8615e-130">Habilitando o serviço de simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="8615e-130">Enabling the input simulation service</span></span>

<span data-ttu-id="8615e-131">Na configuração do provedor de dados do sistema de entrada, o serviço de simulação de entrada pode ser configurado com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="8615e-131">Under the Input System Data provider configuration, the Input Simulation service can be configured with the following.</span></span>

* <span data-ttu-id="8615e-132">O **tipo** deve ser *Microsoft. MixedReality. Toolkit. Input > InputSimulationService*.</span><span class="sxs-lookup"><span data-stu-id="8615e-132">**Type** must be *Microsoft.MixedReality.Toolkit.Input > InputSimulationService*.</span></span>
* <span data-ttu-id="8615e-133">As **plataformas com suporte** por padrão incluem todas as plataformas do *Editor* , já que o serviço usa teclado e entrada do mouse.</span><span class="sxs-lookup"><span data-stu-id="8615e-133">**Supported Platform(s)** by default includes all *Editor* platforms, since the service uses keyboard and mouse input.</span></span>

> [!NOTE]
> <span data-ttu-id="8615e-134">O serviço de simulação de entrada pode ser usado em outros pontos de extremidade de plataforma, como autônomo, alterando a propriedade de **plataforma (s) com suporte** para incluir os destinos desejados.</span><span class="sxs-lookup"><span data-stu-id="8615e-134">The Input Simulation service can be used on other platform endpoints such as standalone by changing the **Supported Platform(s)** property to include the desired targets.</span></span>
> <br/><img src="../images/input-simulation/InputSimulationSupportedPlatforms.gif" alt="Input Simulation Supported Platforms" width="550px">

## <a name="camera-control"></a><span data-ttu-id="8615e-135">Controle de câmera</span><span class="sxs-lookup"><span data-stu-id="8615e-135">Camera control</span></span>

<span data-ttu-id="8615e-136">A movimentação de cabeçalho pode ser emulada pelo serviço de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="8615e-136">Head movement can be emulated by the Input Simulation Service.</span></span>

### <a name="rotating-the-camera"></a><span data-ttu-id="8615e-137">Girando a câmera</span><span class="sxs-lookup"><span data-stu-id="8615e-137">Rotating the camera</span></span>

1. <span data-ttu-id="8615e-138">Passe o mouse sobre a janela do editor do visor.</span><span class="sxs-lookup"><span data-stu-id="8615e-138">Hover over the viewport editor window.</span></span>
    <span data-ttu-id="8615e-139">*Talvez seja necessário clicar na janela para dar um foco de entrada se os pressionamentos de botão não funcionarem.*</span><span class="sxs-lookup"><span data-stu-id="8615e-139">*You may need to click the window to give it input focus if button presses don't work.*</span></span>
1. <span data-ttu-id="8615e-140">Pressione e segure o **botão de aparência do mouse** (padrão: botão direito do mouse).</span><span class="sxs-lookup"><span data-stu-id="8615e-140">Press and hold the **Mouse Look Button** (default: Right mouse button).</span></span>
1. <span data-ttu-id="8615e-141">Mova o mouse na janela do visor para girar a câmera.</span><span class="sxs-lookup"><span data-stu-id="8615e-141">Move the mouse in the viewport window to rotate the camera.</span></span>
1. <span data-ttu-id="8615e-142">Use a roda de rolagem para rolar a câmera pela direção da exibição.</span><span class="sxs-lookup"><span data-stu-id="8615e-142">Use the scroll wheel to roll the camera around the view direction.</span></span>

<span data-ttu-id="8615e-143">A velocidade de rotação da câmera pode ser configurada alterando a configuração de **velocidade de aparência do mouse** no perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="8615e-143">Camera rotation speed can be configured by changing the **Mouse Look Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="8615e-144">Como alternativa, use a aparência **horizontal** / com eixos **verticais** para girar a câmera (padrão: Game Controller Right Thumbstick).</span><span class="sxs-lookup"><span data-stu-id="8615e-144">Alternatively, use the **Look Horizontal**/**Look Vertical** axes to rotate the camera (default: game controller right thumbstick).</span></span>

### <a name="moving-the-camera"></a><span data-ttu-id="8615e-145">Movimentação da câmera</span><span class="sxs-lookup"><span data-stu-id="8615e-145">Moving the camera</span></span>

<span data-ttu-id="8615e-146">Use os eixos verticais mover **horizontalmente** /  para mover a câmera (padrão: WASD chaves ou controlador de jogo para a esquerda Thumbstick).</span><span class="sxs-lookup"><span data-stu-id="8615e-146">Use the **Move Horizontal**/**Move Vertical** axes to move the camera (default: WASD keys or game controller left thumbstick).</span></span>

<span data-ttu-id="8615e-147">A posição da câmera e os ângulos de rotação também podem ser definidos explicitamente na janela ferramentas.</span><span class="sxs-lookup"><span data-stu-id="8615e-147">Camera position and rotation angles can be set explicitly in the tools window, as well.</span></span> <span data-ttu-id="8615e-148">A câmera pode ser redefinida para o padrão usando o botão **Redefinir** .</span><span class="sxs-lookup"><span data-stu-id="8615e-148">The camera can be reset to its default using the **Reset** button.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Z7L4I1ET7GU" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

## <a name="controller-simulation"></a><span data-ttu-id="8615e-149">Simulação de controlador</span><span class="sxs-lookup"><span data-stu-id="8615e-149">Controller simulation</span></span>

<span data-ttu-id="8615e-150">A simulação de entrada dá suporte a dispositivos de controlador emulados (ou seja, controladores de movimento e mãos).</span><span class="sxs-lookup"><span data-stu-id="8615e-150">The input simulation supports emulated controller devices (i.e. motion controllers and hands).</span></span> <span data-ttu-id="8615e-151">Esses controladores virtuais podem interagir com qualquer objeto que ofereça suporte a controladores regulares, como botões ou objetos que podem ser capturados.</span><span class="sxs-lookup"><span data-stu-id="8615e-151">These virtual controllers can interact with any object that supports regular controllers, such as buttons or grabbable objects.</span></span>

### <a name="controller-simulation-mode"></a><span data-ttu-id="8615e-152">Modo de simulação do controlador</span><span class="sxs-lookup"><span data-stu-id="8615e-152">Controller simulation mode</span></span>

<span data-ttu-id="8615e-153">Na [janela ferramentas de simulação de entrada](#input-simulation-tools-window) , a configuração do modo de simulação do **controlador padrão** alterna entre três modelos de entrada distintos.</span><span class="sxs-lookup"><span data-stu-id="8615e-153">In the [input simulation tools window](#input-simulation-tools-window) the **Default Controller Simulation Mode** setting switches between three distinct input models.</span></span> <span data-ttu-id="8615e-154">Esse modo padrão também pode ser definido no perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="8615e-154">This default mode can also be set in the input simulation profile.</span></span>

* <span data-ttu-id="8615e-155">*Mãos articuladas*: simula um dispositivo de mão totalmente articulado com dados de posição conjunta.</span><span class="sxs-lookup"><span data-stu-id="8615e-155">*Articulated Hands*: Simulates a fully articulated hand device with joint position data.</span></span>

   <span data-ttu-id="8615e-156">Emula o modelo de interação do HoloLens 2.</span><span class="sxs-lookup"><span data-stu-id="8615e-156">Emulates HoloLens 2 interaction model.</span></span>

   <span data-ttu-id="8615e-157">As interações que se baseiam no posicionamento preciso da mão ou usam o toque podem ser simuladas nesse modo.</span><span class="sxs-lookup"><span data-stu-id="8615e-157">Interactions that are based on the precise positioning of the hand or use touching can be simulated in this mode.</span></span>

* <span data-ttu-id="8615e-158">*Gestos de mão*: simula um modelo de mão simplificado com toque de ar e gestos básicos.</span><span class="sxs-lookup"><span data-stu-id="8615e-158">*Hand Gestures*: Simulates a simplified hand model with air tap and basic gestures.</span></span>

   <span data-ttu-id="8615e-159">Emula o [modelo de interação do HoloLens](/windows/mixed-reality/gestures).</span><span class="sxs-lookup"><span data-stu-id="8615e-159">Emulates [HoloLens interaction model](/windows/mixed-reality/gestures).</span></span>

   <span data-ttu-id="8615e-160">O foco é controlado usando o ponteiro olhar.</span><span class="sxs-lookup"><span data-stu-id="8615e-160">Focus is controlled using the Gaze pointer.</span></span> <span data-ttu-id="8615e-161">O gesto de *toque do ar* é usado para interagir com botões.</span><span class="sxs-lookup"><span data-stu-id="8615e-161">The *Air Tap* gesture is used to interact with buttons.</span></span>

* <span data-ttu-id="8615e-162">*Controlador de movimento*: simula um controlador de movimento usado com headsets VR que funciona de forma semelhante a interações com mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="8615e-162">*Motion Controller*: Simulates a motion controller used with VR headsets that works similarly to far interactions with Articulated Hands.</span></span>

   <span data-ttu-id="8615e-163">Emula o headset de VR com o modelo de interação de controladores.</span><span class="sxs-lookup"><span data-stu-id="8615e-163">Emulates VR headset with controllers interaction model.</span></span>

   <span data-ttu-id="8615e-164">O gatilho, as teclas de captura e de menu são simuladas por meio de entrada de teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="8615e-164">The trigger, grab and menu keys are simulated via keyboard and mouse input.</span></span>

### <a name="simulating-controller-movement"></a><span data-ttu-id="8615e-165">Simulando a movimentação do controlador</span><span class="sxs-lookup"><span data-stu-id="8615e-165">Simulating controller movement</span></span>

<span data-ttu-id="8615e-166">Pressione e segure a **tecla de manipulação do controlador à esquerda/direita** (padrão: *deslocamento à* esquerda para o controlador esquerdo e o *espaço* para o controlador direito) para obter o controle de qualquer controlador.</span><span class="sxs-lookup"><span data-stu-id="8615e-166">Press and hold the **Left/Right Controller Manipulation Key** (default: *Left Shift* for left controller and *Space* for right controller) to gain control of either controller.</span></span> <span data-ttu-id="8615e-167">Enquanto a tecla de manipulação for pressionada, o controlador aparecerá no visor.</span><span class="sxs-lookup"><span data-stu-id="8615e-167">While the manipulation key is pressed, the controller will appear in the viewport.</span></span> <span data-ttu-id="8615e-168">Depois que a chave de manipulação for liberada, os controladores desaparecerão após um curto **tempo limite de ocultar controlador**.</span><span class="sxs-lookup"><span data-stu-id="8615e-168">Once the manipulation key is released, the controllers will disappear after a short **Controller Hide Timeout**.</span></span>

<span data-ttu-id="8615e-169">Os controladores podem ser ativados e congelados em relação à câmera na [janela ferramentas de simulação de entrada](#input-simulation-tools-window) ou pressionando a **tecla ativar/desativar chave do controlador** (padrão: *T* para esquerda e *Y* para direita).</span><span class="sxs-lookup"><span data-stu-id="8615e-169">Controllers can be toggled on and frozen relative to the camera in the [input simulation tools window](#input-simulation-tools-window) or by pressing the **Toggle Left/Right Controller Key** (default: *T* for left and *Y* for right).</span></span> <span data-ttu-id="8615e-170">Pressione a tecla de alternância novamente para ocultar os controladores novamente.</span><span class="sxs-lookup"><span data-stu-id="8615e-170">Press the toggle key again to hide the controllers again.</span></span> <span data-ttu-id="8615e-171">Para manipular os controladores, a **chave de manipulação do controlador à esquerda/direita** precisa ser mantida.</span><span class="sxs-lookup"><span data-stu-id="8615e-171">To manipulate the controllers, the **Left/Right Controller Manipulation Key** needs to be held.</span></span> <span data-ttu-id="8615e-172">Tocar duas vezes na **tecla de manipulação do controlador à esquerda/direita** também pode ativar/desativar os controladores.</span><span class="sxs-lookup"><span data-stu-id="8615e-172">Double tapping the **Left/Right Controller Manipulation Key** can also toggle the controllers on/off.</span></span>

<span data-ttu-id="8615e-173">O movimento do mouse moverá o controlador no plano de exibição.</span><span class="sxs-lookup"><span data-stu-id="8615e-173">Mouse movement will move the controller in the view plane.</span></span> <span data-ttu-id="8615e-174">Os controladores podem ser movidos mais ou mais perto da câmera usando a **roda do mouse**.</span><span class="sxs-lookup"><span data-stu-id="8615e-174">Controllers can be moved further or closer to the camera using the **mouse wheel**.</span></span>

<span data-ttu-id="8615e-175">Para girar os controladores usando o mouse, mantenha a **tecla de manipulação do controlador à esquerda/direita** (*deslocamento à esquerda* ou o *espaço*) *e* o **botão de rotação do controlador** (padrão: botão *CTRL esquerda* ) e, em seguida, mova o mouse para girar o controlador.</span><span class="sxs-lookup"><span data-stu-id="8615e-175">To rotate controllers using the mouse, hold both the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*) *and* the **Controller Rotate Button** (default: *Left Ctrl* button) and then move the mouse to rotate the controller.</span></span> <span data-ttu-id="8615e-176">A velocidade de rotação do controlador pode ser configurada alterando a configuração de **velocidade de rotação do controlador do mouse** no perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="8615e-176">Controller rotation speed can be configured by changing the **Mouse Controller Rotation Speed** setting in the input simulation profile.</span></span>

<span data-ttu-id="8615e-177">Todo o posicionamento manual também pode ser alterado na [janela ferramentas de simulação de entrada](#input-simulation-tools-window), incluindo redefinição de mãos para padrão.</span><span class="sxs-lookup"><span data-stu-id="8615e-177">All hand placement can also changed in the [input simulation tools window](#input-simulation-tools-window), including resetting hands to default.</span></span>

### <a name="additional-profile-settings"></a><span data-ttu-id="8615e-178">Configurações de perfil adicionais</span><span class="sxs-lookup"><span data-stu-id="8615e-178">Additional profile settings</span></span>

* <span data-ttu-id="8615e-179">O **multiplicador de profundidade do controlador** controla a sensibilidade da movimentação de profundidade da roda de rolagem do mouse.</span><span class="sxs-lookup"><span data-stu-id="8615e-179">**Controller Depth Multiplier** controls the sensitivity of the mouse scroll wheel depth movement.</span></span> <span data-ttu-id="8615e-180">Um número maior acelerará o zoom do controlador.</span><span class="sxs-lookup"><span data-stu-id="8615e-180">A larger number will speed up controller zoom.</span></span>
* <span data-ttu-id="8615e-181">A **distância do controlador padrão** é a distância inicial dos controladores da câmera.</span><span class="sxs-lookup"><span data-stu-id="8615e-181">**Default Controller Distance** is the initial distance of controllers from the camera.</span></span> <span data-ttu-id="8615e-182">Clicar nos controladores de botão **Redefinir** também irá posicionar os controladores nessa distância.</span><span class="sxs-lookup"><span data-stu-id="8615e-182">Clicking the **Reset** button controllers will also place controllers at this distance.</span></span>
* <span data-ttu-id="8615e-183">O **valor de Tremulação do controlador** adiciona movimento aleatório aos controladores.</span><span class="sxs-lookup"><span data-stu-id="8615e-183">**Controller Jitter Amount** adds random motion to controllers.</span></span> <span data-ttu-id="8615e-184">Esse recurso pode ser usado para simular o controle de controlador impreciso no dispositivo e garantir que as interações funcionem bem com entradas ruidosas.</span><span class="sxs-lookup"><span data-stu-id="8615e-184">This feature can be used to simulate inaccurate controller tracking on the device, and ensure that interactions work well with noisy input.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/uRYfwuqsjBQ" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="hand-gestures"></a><span data-ttu-id="8615e-185">Gestos de mão</span><span class="sxs-lookup"><span data-stu-id="8615e-185">Hand gestures</span></span>

<span data-ttu-id="8615e-186">Gestos de mão como pinçagem, captura, investigar, etc. também podem ser simulados.</span><span class="sxs-lookup"><span data-stu-id="8615e-186">Hand gestures such as pinching, grabbing, poking, etc. can also be simulated.</span></span>

1. <span data-ttu-id="8615e-187">Habilitar o controle de mão usando a **tecla de manipulação do controlador à esquerda/direita** (*deslocamento à esquerda* ou *espaço*)</span><span class="sxs-lookup"><span data-stu-id="8615e-187">Enable hand control using the **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>

2. <span data-ttu-id="8615e-188">Durante a manipulação, pressione e mantenha pressionado um botão do mouse para executar um gesto de mão.</span><span class="sxs-lookup"><span data-stu-id="8615e-188">While manipulating, press and hold a mouse button to perform a hand gesture.</span></span>

<span data-ttu-id="8615e-189">Cada um dos botões do mouse pode ser mapeado para transformar a forma mão em um gesto diferente usando as configurações de *gesto esquerdo/médio/direito do mouse* .</span><span class="sxs-lookup"><span data-stu-id="8615e-189">Each of the mouse buttons can be mapped to transform the hand shape into a different gesture using the *Left/Middle/Right Mouse Hand Gesture* settings.</span></span> <span data-ttu-id="8615e-190">O *gesto de mão padrão* é a forma da mão quando nenhum botão é pressionado.</span><span class="sxs-lookup"><span data-stu-id="8615e-190">The *Default Hand Gesture* is the shape of the hand when no button is pressed.</span></span>

> [!NOTE]
> <span data-ttu-id="8615e-191">O gesto de *pinçar* é o único gesto que executa a ação "selecionar" neste ponto.</span><span class="sxs-lookup"><span data-stu-id="8615e-191">The *Pinch* gesture is the only gesture that performs the "Select" action at this point.</span></span>

### <a name="one-hand-manipulation"></a><span data-ttu-id="8615e-192">Manipulação unidirecional</span><span class="sxs-lookup"><span data-stu-id="8615e-192">One-hand manipulation</span></span>

1. <span data-ttu-id="8615e-193">Pressione e mantenha a **tecla de manipulação da controladora esquerda/direita** (*SHIFT esquerda* ou *espaço*)</span><span class="sxs-lookup"><span data-stu-id="8615e-193">Press and hold **Left/Right Controller Manipulation Key** (*Left Shift* or *Space*)</span></span>
2. <span data-ttu-id="8615e-194">Ponto no objeto</span><span class="sxs-lookup"><span data-stu-id="8615e-194">Point at object</span></span>
3. <span data-ttu-id="8615e-195">Mantenha o botão do mouse para pinçar</span><span class="sxs-lookup"><span data-stu-id="8615e-195">Hold mouse button to pinch</span></span>
4. <span data-ttu-id="8615e-196">Use o mouse para mover o objeto</span><span class="sxs-lookup"><span data-stu-id="8615e-196">Use your mouse to move the object</span></span>
5. <span data-ttu-id="8615e-197">Solte o botão do mouse para parar a interação</span><span class="sxs-lookup"><span data-stu-id="8615e-197">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/rM0xaHam6wM" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="two-hand-manipulation"></a><span data-ttu-id="8615e-198">Manipulação de duas mãos</span><span class="sxs-lookup"><span data-stu-id="8615e-198">Two-hand manipulation</span></span>

<span data-ttu-id="8615e-199">Para manipular objetos com duas mãos ao mesmo tempo, o modo de mão persistente é recomendado.</span><span class="sxs-lookup"><span data-stu-id="8615e-199">For manipulating objects with two hands at the same time, the persistent hand mode is recommended.</span></span>

1. <span data-ttu-id="8615e-200">Ative as duas mãos pressionando as teclas de alternância (*T/Y*).</span><span class="sxs-lookup"><span data-stu-id="8615e-200">Toggle on both hands by pressing the toggle keys (*T/Y*).</span></span>
1. <span data-ttu-id="8615e-201">Manipule uma mão por vez:</span><span class="sxs-lookup"><span data-stu-id="8615e-201">Manipulate one hand at a time:</span></span>
    1. <span data-ttu-id="8615e-202">Mantenha **espaço** para controlar a mão direita</span><span class="sxs-lookup"><span data-stu-id="8615e-202">Hold **Space** to control the right hand</span></span>
    1. <span data-ttu-id="8615e-203">Mover a mão para onde você deseja obter o objeto</span><span class="sxs-lookup"><span data-stu-id="8615e-203">Move the hand to where you want to grab the object</span></span>
    1. <span data-ttu-id="8615e-204">Pressione o **botão esquerdo do mouse** para ativar o gesto de *pinçar* .</span><span class="sxs-lookup"><span data-stu-id="8615e-204">Press the **left mouse button** to activate the *Pinch* gesture.</span></span>
    1. <span data-ttu-id="8615e-205">Liberar **espaço** para parar de controlar a mão direita.</span><span class="sxs-lookup"><span data-stu-id="8615e-205">Release **Space** to stop controlling the right hand.</span></span> <span data-ttu-id="8615e-206">A mão será congelada no local e ficará bloqueada no gesto de *pinçar* , já que ele não está mais sendo manipulado.</span><span class="sxs-lookup"><span data-stu-id="8615e-206">The hand will be frozen in place and be locked into the *Pinch* gesture since it is no longer being manipulated.</span></span>
1. <span data-ttu-id="8615e-207">Repita o processo com a outra mão, capturando o mesmo objeto em um segundo ponto.</span><span class="sxs-lookup"><span data-stu-id="8615e-207">Repeat the process with the other hand, grabbing the same object in a second spot.</span></span>
1. <span data-ttu-id="8615e-208">Agora que ambas as mãos estão captando o mesmo objeto, você pode mover qualquer um deles para executar a manipulação de duas mãos.</span><span class="sxs-lookup"><span data-stu-id="8615e-208">Now that both hands are grabbing the same object, you can move either of them to perform two-handed manipulation.</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qol5OFNfN14" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="ggv-gaze-gesture-and-voice-interaction"></a><span data-ttu-id="8615e-209">Interação de GGV (olhar, gesto e voz)</span><span class="sxs-lookup"><span data-stu-id="8615e-209">GGV (Gaze, Gesture, and Voice) interaction</span></span>

<span data-ttu-id="8615e-210">Por padrão, a interação GGV é habilitada no editor enquanto não há nenhuma mão articulada presente na cena.</span><span class="sxs-lookup"><span data-stu-id="8615e-210">By default, GGV interaction is enabled in-editor while there are no articulated hands present in the scene.</span></span>

1. <span data-ttu-id="8615e-211">Girar a câmera para apontar o cursor olhar no objeto que interage (botão direito do mouse)</span><span class="sxs-lookup"><span data-stu-id="8615e-211">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="8615e-212">Clique e mantenha o **botão esquerdo do mouse** para interagir</span><span class="sxs-lookup"><span data-stu-id="8615e-212">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="8615e-213">Gire a câmera novamente para manipular o objeto</span><span class="sxs-lookup"><span data-stu-id="8615e-213">Rotate the camera again to manipulate the object</span></span>

<span data-ttu-id="8615e-214">Você pode desativar isso alternando a opção *é mão habilitada para entrada livre* dentro do perfil de simulação de entrada.</span><span class="sxs-lookup"><span data-stu-id="8615e-214">You can turn this off by toggling the *Is Hand Free Input Enabled* option inside the Input Simulation Profile.</span></span>

<span data-ttu-id="8615e-215">Além disso, você pode usar as mãos simuladas para a interação GGV</span><span class="sxs-lookup"><span data-stu-id="8615e-215">In addition, you can use simulated hands for GGV interaction</span></span>

1. <span data-ttu-id="8615e-216">Habilitar a simulação de GGV alternando o **modo de simulação** para *gestos* no [perfil de simulação de entrada](#enabling-the-input-simulation-service)</span><span class="sxs-lookup"><span data-stu-id="8615e-216">Enable GGV simulation by switching **Hand Simulation Mode** to *Gestures* in the [Input Simulation Profile](#enabling-the-input-simulation-service)</span></span>
1. <span data-ttu-id="8615e-217">Girar a câmera para apontar o cursor olhar no objeto que interage (botão direito do mouse)</span><span class="sxs-lookup"><span data-stu-id="8615e-217">Rotate the camera to point the gaze cursor at the interactable object (right mouse button)</span></span>
1. <span data-ttu-id="8615e-218">Mantenha **espaço** para controlar a mão direita</span><span class="sxs-lookup"><span data-stu-id="8615e-218">Hold **Space** to control the right hand</span></span>
1. <span data-ttu-id="8615e-219">Clique e mantenha o **botão esquerdo do mouse** para interagir</span><span class="sxs-lookup"><span data-stu-id="8615e-219">Click and hold **left mouse button** to interact</span></span>
1. <span data-ttu-id="8615e-220">Use o mouse para mover o objeto</span><span class="sxs-lookup"><span data-stu-id="8615e-220">Use your mouse to move the object</span></span>
1. <span data-ttu-id="8615e-221">Solte o botão do mouse para parar a interação</span><span class="sxs-lookup"><span data-stu-id="8615e-221">Release the mouse button to stop interaction</span></span>

<iframe width="560" height="315" src="https://www.youtube.com/embed/6841rRMdqWw" class="center" frameborder="0" allow="accelerometer; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### <a name="raising-teleport-events"></a><span data-ttu-id="8615e-222">Gerando eventos teleport</span><span class="sxs-lookup"><span data-stu-id="8615e-222">Raising Teleport Events</span></span>

<span data-ttu-id="8615e-223">Para gerar o evento teleport na simulação de entrada, defina as configurações de gesto da mão no perfil de simulação de entrada para que um execute o gesto de **início teleport** enquanto o outro executa o gesto de **término teleport** .</span><span class="sxs-lookup"><span data-stu-id="8615e-223">To raise the teleport event in input simulation, configure the Hand Gesture Settings in the Input Simulation Profile so that one performs the **Teleport Start** Gesture while the other performs the **Teleport End** Gesture.</span></span> <span data-ttu-id="8615e-224">O gesto de **início de teleport** abrirá o ponteiro teleport, enquanto o Gesure **teleport end** concluirá a ação teleport e moverá o usuário.</span><span class="sxs-lookup"><span data-stu-id="8615e-224">The **Teleport Start** gesture will bring up the Teleport Pointer, while the **Teleport End** gesure will complete the teleport action and move the user.</span></span>

<span data-ttu-id="8615e-225">A posição y de seu teleport resultante depende do deslocamento da câmera ao longo do eixo y.</span><span class="sxs-lookup"><span data-stu-id="8615e-225">The y-position of your resulting teleport is dependent on the camera's displacement along the y-axis.</span></span> <span data-ttu-id="8615e-226">No editor, isso é 0 por padrão. portanto, use as teclas **Q** e **e** para ajustá-la à altura apropriada.</span><span class="sxs-lookup"><span data-stu-id="8615e-226">In editor, this is 0 by default, so use the **Q** and **E** keys to adjust it to the appropriate height.</span></span>

![Configurações de teleport de simulação de entrada](../images/input-simulation/InputSimulationTeleport.gif)

### <a name="motion-controller-interaction"></a><span data-ttu-id="8615e-228">Interação do controlador de movimento</span><span class="sxs-lookup"><span data-stu-id="8615e-228">Motion controller interaction</span></span>

<span data-ttu-id="8615e-229">Os controladores de movimento simulados podem ser manipulados da mesma forma que as mãos articuladas.</span><span class="sxs-lookup"><span data-stu-id="8615e-229">The simulated motion controllers can be manipulated the same way articulated hands are.</span></span> <span data-ttu-id="8615e-230">O modelo de interação é semelhante à interação extrema da mão articulada enquanto o gatilho, as teclas de captura e de menu são mapeadas para o *botão esquerdo do mouse*, a tecla *G* e *M* , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8615e-230">The interaction model is similar to far interaction of articulated hand while the trigger, grab and menu keys are mapped to *left mouse button*, *G* and *M* key respectively.</span></span>

### <a name="eye-tracking"></a><span data-ttu-id="8615e-231">Acompanhamento ocular</span><span class="sxs-lookup"><span data-stu-id="8615e-231">Eye tracking</span></span>

<span data-ttu-id="8615e-232">A [simulação de acompanhamento de olho](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) pode ser habilitada verificando a opção **simular posição de olho** no perfil de simulação de [entrada](#enabling-the-input-simulation-service).</span><span class="sxs-lookup"><span data-stu-id="8615e-232">[Eye tracking simulation](../input/eye-tracking/eye-tracking-basic-setup.md#simulating-eye-tracking-in-the-unity-editor) can be enabled by checking the **Simulate Eye Position** option in the [Input Simulation Profile](#enabling-the-input-simulation-service).</span></span> <span data-ttu-id="8615e-233">Isso não deve ser usado com interações de estilo de controlador de movimento ou GGV (portanto, certifique-se de que o **modo de simulação de controlador padrão** esteja definido para a *mão articulada*).</span><span class="sxs-lookup"><span data-stu-id="8615e-233">This should not be used with GGV or motion controller style interactions (so ensure that **Default Controller Simulation Mode** is set to *Articulated Hand*).</span></span>

## <a name="input-simulation-tools-window"></a><span data-ttu-id="8615e-234">Janela de ferramentas de simulação de entrada</span><span class="sxs-lookup"><span data-stu-id="8615e-234">Input simulation tools window</span></span>

<span data-ttu-id="8615e-235">Habilite a janela ferramentas de simulação de entrada do menu de simulação de entrada do kit de ferramentas da **realidade misturada**  >    >    >   .</span><span class="sxs-lookup"><span data-stu-id="8615e-235">Enable the input simulation tools window from the  **Mixed Reality** > **Toolkit** > **Utilities** > **Input Simulation** menu.</span></span> <span data-ttu-id="8615e-236">Esta janela fornece acesso ao estado da simulação de entrada durante o modo de reprodução.</span><span class="sxs-lookup"><span data-stu-id="8615e-236">This window provides access to the state of input simulation during play mode.</span></span>

## <a name="viewport-buttons-optional"></a><span data-ttu-id="8615e-237">Botões do visor (opcional)</span><span class="sxs-lookup"><span data-stu-id="8615e-237">Viewport buttons (optional)</span></span>

<span data-ttu-id="8615e-238">Um pré-fabricado para botões no editor para controlar o posicionamento básico pode ser especificado no perfil de simulação de entrada em **indicadores pré-fabricado**.</span><span class="sxs-lookup"><span data-stu-id="8615e-238">A prefab for in-editor buttons to control basic hand placement can be specified in the input simulation profile under **Indicators Prefab**.</span></span> <span data-ttu-id="8615e-239">Esse é um utilitário opcional, os mesmos recursos podem ser acessados na [janela ferramentas de simulação de entrada](#input-simulation-tools-window).</span><span class="sxs-lookup"><span data-stu-id="8615e-239">This is an optional utility, the same features can be accessed in the [input simulation tools window](#input-simulation-tools-window).</span></span>

> [!NOTE]
> <span data-ttu-id="8615e-240">Os indicadores do visor são desabilitados por padrão, pois eles podem, às vezes, interferir nas interações da interface do usuário do Unity.</span><span class="sxs-lookup"><span data-stu-id="8615e-240">The viewport indicators are disabled by default, as they currently can sometimes interfere with Unity UI interactions.</span></span> <span data-ttu-id="8615e-241">Consulte o problema [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span><span class="sxs-lookup"><span data-stu-id="8615e-241">See issue [#6106](https://github.com/microsoft/MixedRealityToolkit-Unity/issues/6106).</span></span> <span data-ttu-id="8615e-242">Para habilitar, adicione InputSimulationIndicators pré-fabricado aos **indicadores pré-fabricado**.</span><span class="sxs-lookup"><span data-stu-id="8615e-242">To enable, add the InputSimulationIndicators prefab to **Indicators Prefab**.</span></span>

<span data-ttu-id="8615e-243">Os ícones de mão mostram o estado das mãos simuladas:</span><span class="sxs-lookup"><span data-stu-id="8615e-243">Hand icons show the state of the simulated hands:</span></span>

* ![Ícone de mão não controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Untracked.png) <span data-ttu-id="8615e-245&quot;>A mão não está acompanhando.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8615e-245&quot;>The hand is not tracking.</span></span> <span data-ttu-id=&quot;8615e-246&quot;>Clique para habilitar a mão.</span><span class=&quot;sxs-lookup&quot;><span data-stu-id=&quot;8615e-246&quot;>Click to enable the hand.</span></span>
* <span data-ttu-id=&quot;8615e-247&quot;>![Ícone de mão controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png &quot;Ícone de mão controlada") A mão é controlada, mas não é controlada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="8615e-247">![Tracked hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Tracked.png "Tracked hand icon") The hand is tracked, but not controlled by the user.</span></span> <span data-ttu-id="8615e-248">Clique para ocultar a mão.</span><span class="sxs-lookup"><span data-stu-id="8615e-248">Click to hide the hand.</span></span>
* <span data-ttu-id="8615e-249">![Ícone de mão controlada](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Ícone de mão controlada") A mão é controlada e controlada pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="8615e-249">![Controlled hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Controlled.png "Controlled hand icon") The hand is tracked and controlled by the user.</span></span> <span data-ttu-id="8615e-250">Clique para ocultar a mão.</span><span class="sxs-lookup"><span data-stu-id="8615e-250">Click to hide the hand.</span></span>
* <span data-ttu-id="8615e-251">![Ícone de redefinir mão](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Ícone de redefinir mão") Clique para redefinir a mão para a posição padrão.</span><span class="sxs-lookup"><span data-stu-id="8615e-251">![Reset hand icon](../images/input-simulation/MRTK_InputSimulation_HandIndicator_Reset.png "Reset hand icon") Click to reset the hand to default position.</span></span>


## <a name="see-also"></a><span data-ttu-id="8615e-252">Confira também</span><span class="sxs-lookup"><span data-stu-id="8615e-252">See also</span></span>

* <span data-ttu-id="8615e-253">[Perfil do sistema de entrada](../input/input-providers.md).</span><span class="sxs-lookup"><span data-stu-id="8615e-253">[Input System profile](../input/input-providers.md).</span></span>