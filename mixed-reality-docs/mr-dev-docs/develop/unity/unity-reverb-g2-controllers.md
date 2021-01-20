---
title: Controladores de reverbo do HP G2 no Unity
description: Saiba como configurar e usar os novos controladores HP reverbs G2 nos aplicativos SteamVR e Windows Mixed Reality Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, reverberação, reverbo G2, HP reverbs G2, realidade mista, desenvolvimento, controladores de movimento, entrada do usuário, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos
ms.openlocfilehash: fa9b80076d65978ae1602fc4f9519d7e11c651b5
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98583573"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a><span data-ttu-id="e3311-104">Controladores de reverbo do HP G2 no Unity</span><span class="sxs-lookup"><span data-stu-id="e3311-104">HP Reverb G2 Controllers in Unity</span></span>

<span data-ttu-id="e3311-105">Os controladores HP Motion são um tipo totalmente novo de controladores de realidade misturada do Windows: toda a mesma tecnologia de controle com um conjunto ligeiramente diferente de entradas disponíveis:</span><span class="sxs-lookup"><span data-stu-id="e3311-105">HP Motion controllers are a brand new type of Windows Mixed Reality controllers: all the same tracking technology with a slightly different set of available inputs:</span></span> 

* <span data-ttu-id="e3311-106">O touchpad foi substituído por dois botões: A e B para o controlador correto e X e Y para o controlador esquerdo.</span><span class="sxs-lookup"><span data-stu-id="e3311-106">Touchpad has been replaced by two buttons: A and B for the right controller, and X and Y for the left controller.</span></span> 
* <span data-ttu-id="e3311-107">Segure agora é um gatilho que publica um fluxo de valores entre 0,0 e 1,0 em vez de um botão com Estados pressionados e não pressionados.</span><span class="sxs-lookup"><span data-stu-id="e3311-107">Grasp is now a trigger that publishes a stream of values between 0.0 and 1.0 instead of a button with Pressed and Not Pressed states.</span></span> 

<span data-ttu-id="e3311-108">Como as novas entradas não estão acessíveis por meio de APIs existentes do Windows e do Unity, você precisa do pacote **Microsoft. MixedReality. Input** UPM dedicado.</span><span class="sxs-lookup"><span data-stu-id="e3311-108">Since the new inputs aren't accessible through existing Windows and Unity APIs, you need the dedicated **Microsoft.MixedReality.Input** UPM Package.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="e3311-109">**As classes neste pacote não substituem as APIs existentes do Windows e do Unity, mas as complementam.**</span><span class="sxs-lookup"><span data-stu-id="e3311-109">**Classes in this package do not replace existing Windows and Unity APIs but complement them.**</span></span> <span data-ttu-id="e3311-110">Recursos normalmente disponíveis para controladores de realidade mista do Windows misto e controladores HP Motion podem ser acessados por meio do mesmo caminho de código usando APIs existentes.</span><span class="sxs-lookup"><span data-stu-id="e3311-110">Features commonly available to both classic Windows Mixed Reality controllers and HP Motion Controllers are accessible through the same code path using existing APIs.</span></span> <span data-ttu-id="e3311-111">Somente as novas entradas exigem o uso do pacote adicional Microsoft. MixedReality. Input.</span><span class="sxs-lookup"><span data-stu-id="e3311-111">Only the new inputs require the use of the additional Microsoft.MixedReality.Input package.</span></span> 

## <a name="hp-motion-controller-overview"></a><span data-ttu-id="e3311-112">Visão geral do controlador HP Motion</span><span class="sxs-lookup"><span data-stu-id="e3311-112">HP Motion Controller overview</span></span>

<span data-ttu-id="e3311-113">*Microsoft. MixedReality. Input. MotionController* representa um controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="e3311-113">*Microsoft.MixedReality.Input.MotionController* represents a motion controller.</span></span> <span data-ttu-id="e3311-114">Cada instância de *MotionController* tem um *XR. WSA. Input. codeaction* -peer, que pode ser correlacionado usando destroly, ID do fornecedor, product ID e Version.</span><span class="sxs-lookup"><span data-stu-id="e3311-114">Each *MotionController* instance has an *XR.WSA.Input.InteractionSource* peer, which can be correlated using handedness, vendor ID, product ID, and version.</span></span> 

<span data-ttu-id="e3311-115">Você pode obter instâncias de MotionController criando um *MotionControllerWatcher* e assinando seus eventos, semelhante ao uso de eventos *interactionmanager* para descobrir novas instâncias de *interação* .</span><span class="sxs-lookup"><span data-stu-id="e3311-115">You can grab MotionController instances by creating a *MotionControllerWatcher* and subscribing to its events, similar to using *InteractionManager* events to discover new *InteractionSource* instances.</span></span> <span data-ttu-id="e3311-116">Os métodos e as propriedades de MotionController descrevem as entradas com suporte pelo controlador, incluindo seus botões, gatilhos, eixo 2D e Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="e3311-116">The MotionController’s methods and properties describe the inputs supported by the controller, including its buttons, triggers, 2D axis, and thumbstick.</span></span> <span data-ttu-id="e3311-117">A classe MotionController também expõe métodos para acessar os Estados de entrada por meio da classe *MotionControllerReading* .</span><span class="sxs-lookup"><span data-stu-id="e3311-117">The MotionController class also exposes methods for accessing input states through the *MotionControllerReading* class.</span></span> <span data-ttu-id="e3311-118">A classe MotionControllerReading representa um instantâneo do estado do controlador em um determinado momento.</span><span class="sxs-lookup"><span data-stu-id="e3311-118">The MotionControllerReading class represents a snapshot of the controller’s state at a given time.</span></span> 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a><span data-ttu-id="e3311-119">Instalando Microsoft. MixedReality. Input usando o Gerenciador de pacotes do Unity</span><span class="sxs-lookup"><span data-stu-id="e3311-119">Installing Microsoft.MixedReality.Input using the Unity Package Manager</span></span> 

<span data-ttu-id="e3311-120">O Gerenciador de pacotes do Unity usa um [arquivo de manifesto](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.jsem) para determinar quais pacotes instalar e os registros (servidores) dos quais eles podem ser instalados.</span><span class="sxs-lookup"><span data-stu-id="e3311-120">The Unity Package Manager uses a [manifest file](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.json) to determine which packages to install and the registries (servers) they can be installed from.</span></span> <span data-ttu-id="e3311-121">Antes de poder usar o pacote Microsoft. MixedReality. Input, você precisará registrar o servidor de componentes da realidade misturada.</span><span class="sxs-lookup"><span data-stu-id="e3311-121">Before you can use the Microsoft.MixedReality.Input package, you'll need to register the Mixed Reality component server.</span></span>

### <a name="registering-the-mixed-reality-component-server"></a><span data-ttu-id="e3311-122">Registrando o servidor de componentes da realidade misturada</span><span class="sxs-lookup"><span data-stu-id="e3311-122">Registering the Mixed Reality component server</span></span> 

<span data-ttu-id="e3311-123">Para cada projeto que usará o pacote de entrada de realidade misturada, o manifest.jsno arquivo (na pasta pacotes) precisa do registro com escopo de realidade misturada adicionado.</span><span class="sxs-lookup"><span data-stu-id="e3311-123">For each project that will be using the Mixed Reality Input package, the manifest.json file (in the Packages folder) needs the Mixed Reality scoped registry added.</span></span> <span data-ttu-id="e3311-124">Para modificar corretamente o manifest.jsno para dar suporte à realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="e3311-124">To properly modify manifest.json to support Mixed Reality:</span></span> 
    1. <span data-ttu-id="e3311-125">Abra <projectRoot> /Packages/manifest.jsem um editor de texto, como Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e3311-125">Open <projectRoot>/Packages/manifest.json in a text editor, such as Visual Studio Code.</span></span> 
    2. <span data-ttu-id="e3311-126">Na parte superior do arquivo de manifesto, adicione o servidor de realidade misturada à seção do registro com escopo e salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3311-126">At the top of the manifest file, add the Mixed Reality server to the scoped registry section and save the file.</span></span> 
    
<pre>
{ 
  "scopedRegistries": [ 
    { 
      "name": "Microsoft Mixed Reality", 
      "url": "https://pkgs.dev.azure.com/aipmr/MixedReality-Unity-Packages/_packaging/Unity-packages/npm/registry/", 
      "scopes": [ 
        "com.microsoft.mixedreality" 
      ] 
    } 
  ], 
</pre>

### <a name="adding-the-microsoftmixedrealityinput-package"></a><span data-ttu-id="e3311-127">Adicionando o pacote Microsoft. MixedReality. Input</span><span class="sxs-lookup"><span data-stu-id="e3311-127">Adding the Microsoft.MixedReality.Input package</span></span> 

<span data-ttu-id="e3311-128">Modifique a seção de dependências do <projectRoot> /Packages/manifest.jsno arquivo no editor de texto para adicionar com. Microsoft. mixedreality. Input Package e salve o arquivo.</span><span class="sxs-lookup"><span data-stu-id="e3311-128">Modify the dependencies section of the <projectRoot>/Packages/manifest.json file in the text editor to add com.microsoft.mixedreality.input package and save the file.</span></span> 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a><span data-ttu-id="e3311-129">Usando Microsoft. MixedReality. Input</span><span class="sxs-lookup"><span data-stu-id="e3311-129">Using Microsoft.MixedReality.Input</span></span> 

### <a name="input-values"></a><span data-ttu-id="e3311-130">Valores de entrada</span><span class="sxs-lookup"><span data-stu-id="e3311-130">Input values</span></span>

<span data-ttu-id="e3311-131">Um MotionController pode expor dois tipos de entradas:</span><span class="sxs-lookup"><span data-stu-id="e3311-131">A MotionController can expose two kinds of inputs:</span></span> 

* <span data-ttu-id="e3311-132">Os botões e os Estados de gatilho são expressos por um valor float exclusivo entre 0,0 e 1,0 que indica quanto eles são pressionados.</span><span class="sxs-lookup"><span data-stu-id="e3311-132">Buttons and trigger states are expressed by a unique float value between 0.0 and 1.0 that indicates how much they're pressed.</span></span>
    * <span data-ttu-id="e3311-133">Um botão só pode retornar 0,0 (quando não pressionado) ou 1,0 (quando pressionado) enquanto um gatilho pode retornar valores contínuos entre 0,0 (totalmente lançado) para 1,0 (totalmente pressionado).</span><span class="sxs-lookup"><span data-stu-id="e3311-133">A button can only return 0.0 (when not pressed) or 1.0 (when pressed) while a trigger can return continuous values between 0.0 (fully released) to 1.0 (fully pressed).</span></span> 
* <span data-ttu-id="e3311-134">O estado Thumbstick é expresso por um vector2 cujos componentes X e Y estão entre-1,0 e 1,0.</span><span class="sxs-lookup"><span data-stu-id="e3311-134">Thumbstick state is expressed by a Vector2 whose X and Y components are between -1.0 and 1.0.</span></span> 

<span data-ttu-id="e3311-135">Você pode usar *MotionController. GetPressableInputs ()* para retornar uma lista de entradas que retornam um valor pressionado (botões e gatilhos) ou o método *MotionController. GetXYInputs ()* para retornar uma lista de entradas que retornam um valor de eixo 2.</span><span class="sxs-lookup"><span data-stu-id="e3311-135">You can use *MotionController.GetPressableInputs()* to return a list of inputs returning a pressed value (buttons and triggers) or the *MotionController.GetXYInputs()* method to return a list of inputs returning a 2-axis value.</span></span> 

<span data-ttu-id="e3311-136">Uma instância de MotionControllerReading representa o estado do controlador em um determinado momento:</span><span class="sxs-lookup"><span data-stu-id="e3311-136">A MotionControllerReading instance represents the state of the controller at a given time:</span></span> 

* <span data-ttu-id="e3311-137">*Getpressionvalue ()* recupera o estado de um botão ou um gatilho.</span><span class="sxs-lookup"><span data-stu-id="e3311-137">*GetPressedValue()* retrieves the state of a button or a trigger.</span></span> 
* <span data-ttu-id="e3311-138">*GetXYValue ()* recupera o estado de um Thumbstick.</span><span class="sxs-lookup"><span data-stu-id="e3311-138">*GetXYValue()* retrieves the state of a thumbstick.</span></span> 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a><span data-ttu-id="e3311-139">Criando um cache para manter uma coleção de instâncias MotionController e seus Estados</span><span class="sxs-lookup"><span data-stu-id="e3311-139">Creating a cache to maintain a collection of MotionController instances and their states</span></span> 

<span data-ttu-id="e3311-140">Comece instanciando um MotionControllerWatcher e Registrando manipuladores para seus eventos *MotionControllerAdded* e *MotionControllerRemoved* para manter um cache de instâncias de MotionController disponíveis.</span><span class="sxs-lookup"><span data-stu-id="e3311-140">Start by instantiating a MotionControllerWatcher and registering handlers for its *MotionControllerAdded* and *MotionControllerRemoved* events to keep a cache of available MotionController instances.</span></span> <span data-ttu-id="e3311-141">Esse cache deve ser um monobehavior anexado a um gameobject, conforme demonstrado no código a seguir:</span><span class="sxs-lookup"><span data-stu-id="e3311-141">This cache should be a MonoBehavior attached to a GameObject as demonstrated in the following code:</span></span>

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    /// <summary> 
    /// Internal helper class which associates a Motion Controller 
    /// and its known state 
    /// </summary> 
    private class MotionControllerState 
    { 
        /// <summary> 
        /// Construction 
        /// </summary> 
        /// <param name="mc">motion controller</param>` 
        public MotionControllerState(MotionController mc) 
        { 
            this.MotionController = mc; 
        } 

        /// <summary> 
        /// Motion Controller that the state represents 
        /// </summary> 
        public MotionController MotionController { get; private set; } 
        … 
    } 

    private MotionControllerWatcher _watcher; 
    private Dictionary<Handedness, MotionControllerState> 
        _controllers = new Dictionary<Handedness, MotionControllerState>(); 

    /// <summary> 
    /// Starts monitoring controller's connections and disconnections 
    /// </summary> 
    public void Start() 
    { 
        _watcher = new MotionControllerWatcher(); 
        _watcher.MotionControllerAdded += _watcher_MotionControllerAdded; 
        _watcher.MotionControllerRemoved += _watcher_MotionControllerRemoved; 
        var nowait = _watcher.StartAsync(); 
    } 

    /// <summary> 
    /// Stops monitoring controller's connections and disconnections 
    /// </summary> 
    public void Stop() 
    { 
        if (_watcher != null) 
        { 
            _watcher.MotionControllerAdded -= _watcher_MotionControllerAdded; 
            _watcher.MotionControllerRemoved -= _watcher_MotionControllerRemoved; 
            _watcher.Stop(); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been removed from the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerRemoved(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers.Remove(e.Handedness); 
        } 
    }

    /// <summary> 
    /// called when a motion controller has been added to the system: 
    /// Remove a motion controller from the cache 
    /// </summary> 
    /// <param name="sender">motion controller watcher</param> 
    /// <param name="e">motion controller </param> 
    private void _watcher_MotionControllerAdded(object sender, MotionController e) 
    { 
        lock (_controllers) 
        { 
            _controllers[e.Handedness] = new MotionControllerState(e); 
        } 
    } 
} 
```

### <a name="reading-new-inputs-by-polling"></a><span data-ttu-id="e3311-142">Lendo novas entradas por sondagem</span><span class="sxs-lookup"><span data-stu-id="e3311-142">Reading new inputs by polling</span></span> 

<span data-ttu-id="e3311-143">Você pode ler o estado atual de cada controlador conhecido por meio de *MotionController. TryGetReadingAtTime* durante o método *Update* da classe monobehavior.</span><span class="sxs-lookup"><span data-stu-id="e3311-143">You can read the current state of each known controller through *MotionController.TryGetReadingAtTime* during the *Update* method of the MonoBehavior class.</span></span> <span data-ttu-id="e3311-144">Você deseja passar *DateTime. Now* como o parâmetro timestamp para garantir que o estado mais recente do controlador seja lido.</span><span class="sxs-lookup"><span data-stu-id="e3311-144">You want to pass *DateTime.Now* as the timestamp parameter to ensure that the latest state of the controller is read.</span></span> 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 

    private class MotionControllerState 
    {
        … 

        /// <summary> 
        /// Update the current state of the motion controller 
        /// </summary> 
        /// <param name="when">time of the reading</param> 
        public void Update(DateTime when) 
        { 
            this.CurrentReading = this.MotionController.TryGetReadingAtTime(when); 
        } 

        /// <summary> 
        /// Last reading from the controller 
        /// </summary> 
        public MotionControllerReading CurrentReading { get; private set; } 
    } 

    /// <summary> 
    /// Updates the input states of the known motion controllers 
    /// </summary> 
    public void Update() 
    { 
        var now = DateTime.Now; 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

<span data-ttu-id="e3311-145">Você pode obter o valor de entrada atual dos controladores usando a destro/canhoto do controlador:</span><span class="sxs-lookup"><span data-stu-id="e3311-145">You can grab the controllers current input value using the Handedness of the controller:</span></span> 

```csharp
public class MotionControllerStateCache : MonoBehaviour 
{ 
    … 
    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(Handedness handedness, ControllerInput input) 
    { 
        MotionControllerReading currentReading = null; 

        lock (_controllers) 
        { 
            if (_controllers.TryGetValue(handedness, out MotionControllerState mc)) 
            { 
                currentReading = mc.CurrentReading; 
            } 
        } 

        return (currentReading == null) ? 0.0f : currentReading.GetPressedValue(input); 
    } 

    /// <summary> 
    /// Returns the current value of a controller input such as button or trigger 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>float value between 0.0 (not pressed) and 1.0 
    /// (fully pressed)</returns> 
    public float GetValue(UnityEngine.XR.WSA.Input.InteractionSourceHandedness handedness, ControllerInput input) 
    { 
        return GetValue(Convert(handedness), input); 
    } 

    /// <summary> 
    /// Returns a boolean indicating whether a controller input such as button or trigger is pressed 
    /// </summary> 
    /// <param name="handedness">Handedness of the controller</param> 
    /// <param name="input">Button or Trigger to query</param> 
    /// <returns>true if pressed, false if not pressed</returns> 
    public bool IsPressed(Handedness handedness, ControllerInput input) 
    { 
        return GetValue(handedness, input) >= PressedThreshold; 
    } 
} 
```

<span data-ttu-id="e3311-146">Por exemplo, para ler o valor de Segure analógico de uma interação:</span><span class="sxs-lookup"><span data-stu-id="e3311-146">For example, to read the analog grasp value of an InteractionSource:</span></span> 

```csharp
/// Read the analog grasp value of all connected interaction sources 
void Update() 
{ 
    … 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    foreach (var sourceState in InteractionManager.GetCurrentReading()) 
    { 
        float graspValue = stateCache.GetValue(sourceState.source.handedness, 
            Microsoft.MixedReality.Input.ControllerInput.Grasp);
        … 
    }
} 
```

### <a name="generating-events-from-the-new-inputs"></a><span data-ttu-id="e3311-147">Gerando eventos a partir das novas entradas</span><span class="sxs-lookup"><span data-stu-id="e3311-147">Generating events from the new inputs</span></span> 

<span data-ttu-id="e3311-148">Em vez de sondar o estado de um controlador uma vez por quadro, você tem a opção de lidar com todas as alterações de estado como eventos, o que permite que você manipule até as ações mais rápidas que têm menos de um quadro.</span><span class="sxs-lookup"><span data-stu-id="e3311-148">Instead of polling for a controller's state once per frame, you have the option of handling all state changes as events, which lets you handle even the quickest actions lasting less than a frame.</span></span> <span data-ttu-id="e3311-149">Para que essa abordagem funcione, o cache de controladores de movimento precisa processar todos os Estados publicados por um controlador desde o último quadro, o que pode ser feito armazenando o carimbo de data/hora do último MotionControllerReading recuperado de um MotionController e chamando *MotionController. TryGetReadingAfterTime ()*:</span><span class="sxs-lookup"><span data-stu-id="e3311-149">In order for this approach to work, the cache of motion controllers needs to process all states published by a controller since the last frame, which you can do by storing the timestamp of the last MotionControllerReading retrieved from a MotionController and calling *MotionController.TryGetReadingAfterTime()*:</span></span> 

```csharp
private class MotionControllerState 
{ 
    … 
    /// <summary> 
    /// Returns an array representng buttons which are pressed 
    /// </summary> 
    /// <param name="reading">motion controller reading</param> 
    /// <returns>array of booleans</returns> 
    private bool[] GetPressed(MotionControllerReading reading) 
    { 
        if (reading == null) 
        { 
            return null; 
        } 
        else 
        { 
            bool[] ret = new bool[this.pressableInputs.Length]; 
            for (int i = 0; i < pressableInputs.Length; ++i) 
            { 
                ret[i] = reading.GetPressedValue(pressableInputs[i]) >= PressedThreshold; 
            } 

            return ret; 
        } 
    } 

    /// <summary> 
    /// Get the next available state of the motion controller 
    /// </summary> 
    /// <param name="lastReading">previous reading</param> 
    /// <param name="newReading">new reading</param> 
    /// <returns>true is a new reading was available</returns> 
    private bool GetNextReading(MotionControllerReading lastReading, out MotionControllerReading newReading) 
    { 
        if (lastReading == null) 
        { 
            // Get the first state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterSystemRelativeTime(TimeSpan.FromSeconds(0.0)); 
        } 
        else 
        { 
            // Get the next state published by the controller 
            newReading = this.MotionController.TryGetReadingAfterTime(lastReading.InputTime); 
        } 

        return newReading != null; 
    } 

    /// <summary> 
    /// Processes all the new states published by the controller since the last call 
    /// </summary> 
    public IEnumerable<MotionControllerEventArgs> GetNextEvents() 
    {
        MotionControllerReading lastReading = this.CurrentReading; 
        bool[] lastPressed = GetPressed(lastReading); 
        MotionControllerReading newReading; 
        bool[] newPressed; 

        while (GetNextReading(lastReading, out newReading)) 
        { 
            newPressed = GetPressed(newReading); 

            // If we have two readings, compare and generate events 
            if (lastPressed != null) 
            { 
                for (int i = 0; i < pressableInputs.Length; ++i) 
                { 
                    if (newPressed[i] != lastPressed[i]) 
                    { 
                        yield return new MotionControllerEventArgs(this.MotionController.Handedness, newPressed[i], this.pressableInputs[i], newReading.InputTime); 
                    } 
                } 
            } 

            lastPressed = newPressed; 
            lastReading = newReading; 
        } 

        // No more reading 
        this.CurrentReading = lastReading; 
    } 
} 
```

<span data-ttu-id="e3311-150">Agora que você atualizou as classes internas do cache, a classe monobehavior pode expor dois eventos – pressionado e liberado – e os elevamos a partir do seu método Update ():</span><span class="sxs-lookup"><span data-stu-id="e3311-150">Now that you've updated the cache internal classes, the MonoBehavior class can expose two events – Pressed and Released – and raise them from its Update() method:</span></span> 

```csharp
/// <summary> 
/// Event argument class for InputPressed and InputReleased events 
/// </summary> 
public class MotionControllerEventArgs : EventArgs 
{ 
    public MotionControllerEventArgs(Handedness handedness, bool isPressed, rollerInput input, DateTime inputTime) 
    { 
        this.Handedness = handedness; 
        this.Input = input; 
        this.InputTime = inputTime; 
        this.IsPressed = isPressed; 
    } 

    /// <summary> 
    /// Handedness of the controller raising the event 
    /// </summary> 
    public Handedness Handedness { get; private set; } 

    /// <summary> 
    /// Button pressed or released 
    /// </summary> 
    public ControllerInput Input { get; private set; } 

    /// <summary> 
    /// Time of the event 
    /// </summary> 
    public DateTime InputTime { get; private set; } 

    /// <summary> 
    /// true if button is pressed, false otherwise 
    /// </summary> 
    public bool IsPressed { get; private set; } 
} 

/// <summary> 
/// Event raised when a button is pressed 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputPressed; 

/// <summary> 
/// Event raised when a button is released 
/// </summary> 
public event EventHandler<MotionControllerEventArgs> InputReleased; 

/// <summary> 
/// Updates the input states of the known motion controllers 
/// </summary> 
public void Update() 
{ 
    // If some event handler has been registered, we need to process all states  
    // since the last update, to avoid missing a quick press / release 
    if ((InputPressed != null) || (InputReleased != null)) 
    { 
        List<MotionControllerEventArgs> events = new <MotionControllerEventArgs>(); 

        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                events.AddRange(controller.Value.GetNextEvents()); 
            } 
        } 
 
        // Sort the events by time 
        events.Sort((e1, e2) => DateTime.Compare(e1.InputTime, e2.InputTime)); 

        foreach (MotionControllerEventArgs evt in events) 
        { 
            if (evt.IsPressed && (InputPressed != null)) 
            { 
                InputPressed(this, evt); 
            } 
            else if (!evt.IsPressed && (InputReleased != null)) 
            { 
                InputReleased(this, evt); 
            } 
        } 
    } 
    else 
    { 
        // As we do not predict button presses and the timestamp of the next e is in the future 
        // DateTime.Now is correct in this context as it will return the latest e of controllers 
        // which is the best we have at the moment for the frame. 
        var now = DateTime.Now; 
        lock (_controllers) 
        { 
            foreach (var controller in _controllers) 
            { 
                controller.Value.Update(now); 
            } 
        } 
    } 
} 
```

<span data-ttu-id="e3311-151">A estrutura nos exemplos de código acima torna o registro de eventos muito mais legível:</span><span class="sxs-lookup"><span data-stu-id="e3311-151">The structure in the above code examples makes registering events much more readable:</span></span> 

```csharp
public InteractionSourceHandedness handedness; 
public Microsoft.MixedReality.Input.ControllerInput redButton;

// Start of the Mono Behavior: register handlers for events from cache 
void Start() 
{ 
    var stateCache = gameObject.GetComponent<MotionControllerStateCache>(); 
    stateCache.InputPressed += stateCache_InputPressed; 
    stateCache.InputReleased += stateCache_InputReleased; 
    … 
} 

// Called when a button is released 
private void stateCache_InputReleased(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 

// Called when a button is pressed 
private void stateCache_InputPressed(object sender, MotionControllerStateCache.MotionControllerEventArgs e) 
{ 
    if ((e.SourceHandedness == handedness) && (e.Input == redButton)) 
    { 
        … 
    } 
} 
```

## <a name="see-also"></a><span data-ttu-id="e3311-152">Confira também</span><span class="sxs-lookup"><span data-stu-id="e3311-152">See also</span></span>

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](../porting-apps/porting-guides.md?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](../porting-apps/porting-guides.md?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->