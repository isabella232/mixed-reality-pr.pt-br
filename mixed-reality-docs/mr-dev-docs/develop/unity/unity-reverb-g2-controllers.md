---
title: Controladores de reverbo do HP G2 no Unity
description: Saiba como configurar e usar os novos controladores HP reverbs G2 nos aplicativos SteamVR e Windows Mixed Reality Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 10/14/2020
ms.topic: article
keywords: Unity, reverberação, reverbo G2, HP reverbs G2, realidade mista, desenvolvimento, controladores de movimento, entrada do usuário, recursos, novo projeto, emulador, documentação, guias, recursos, hologramas, desenvolvimento de jogos
ms.openlocfilehash: 1c9d8f1279f81ea1d8020e2a3c689dae86496221
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009826"
---
# <a name="hp-reverb-g2-controllers-in-unity"></a>Controladores de reverbo do HP G2 no Unity

Os controladores HP Motion são um tipo totalmente novo de controladores de realidade misturada do Windows: toda a mesma tecnologia de controle com um conjunto ligeiramente diferente de entradas disponíveis: 

* O touchpad foi substituído por dois botões: A e B para o controlador correto e X e Y para o controlador esquerdo. 
* Segure agora é um gatilho que publica um fluxo de valores entre 0,0 e 1,0 em vez de um botão com Estados pressionados e não pressionados. 

Como as novas entradas não estão acessíveis por meio de APIs existentes do Windows e do Unity, você precisa do pacote **Microsoft. MixedReality. Input** UPM dedicado. 

> [!IMPORTANT]
> **As classes neste pacote não substituem as APIs existentes do Windows e do Unity, mas as complementam.** Recursos normalmente disponíveis para controladores de realidade mista do Windows misto e controladores HP Motion podem ser acessados por meio do mesmo caminho de código usando APIs existentes. Somente as novas entradas exigem o uso do pacote adicional Microsoft. MixedReality. Input. 

## <a name="hp-motion-controller-overview"></a>Visão geral do controlador HP Motion

*Microsoft. MixedReality. Input. MotionController* representa um controlador de movimento. Cada instância de *MotionController* tem um *XR. WSA. Input. codeaction* -peer, que pode ser correlacionado usando destroly, ID do fornecedor, product ID e Version. 

Você pode obter instâncias de MotionController criando um *MotionControllerWatcher* e assinando seus eventos, semelhante ao uso de eventos *interactionmanager* para descobrir novas instâncias de *interação* . Os métodos e as propriedades de MotionController descrevem as entradas com suporte pelo controlador, incluindo seus botões, gatilhos, eixo 2D e Thumbstick. A classe MotionController também expõe métodos para acessar os Estados de entrada por meio da classe *MotionControllerReading* . A classe MotionControllerReading representa um instantâneo do estado do controlador em um determinado momento. 

## <a name="installing-microsoftmixedrealityinput-using-the-unity-package-manager"></a>Instalando Microsoft. MixedReality. Input usando o Gerenciador de pacotes do Unity 

O Gerenciador de pacotes do Unity usa um [arquivo de manifesto](https://docs.unity3d.com/Manual/upm-manifestPkg.html) (manifest.jsem) para determinar quais pacotes instalar e os registros (servidores) dos quais eles podem ser instalados. Antes de poder usar o pacote Microsoft. MixedReality. Input, você precisará registrar o servidor de componentes da realidade misturada.

### <a name="registering-the-mixed-reality-component-server"></a>Registrando o servidor de componentes da realidade misturada 

Para cada projeto que usará o pacote de entrada de realidade misturada, o manifest.jsno arquivo (na pasta pacotes) precisa do registro com escopo de realidade misturada adicionado. Para modificar corretamente o manifest.jsno para dar suporte à realidade misturada: 
    1. Abra <projectRoot> /Packages/manifest.jsem um editor de texto, como Visual Studio Code. 
    2. Na parte superior do arquivo de manifesto, adicione o servidor de realidade misturada à seção do registro com escopo e salve o arquivo. 
    
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

### <a name="adding-the-microsoftmixedrealityinput-package"></a>Adicionando o pacote Microsoft. MixedReality. Input 

Modifique a seção de dependências do <projectRoot> /Packages/manifest.jsno arquivo no editor de texto para adicionar com. Microsoft. mixedreality. Input Package e salve o arquivo. 

<pre>
  "dependencies": { 
    "com.microsoft.mixedreality.input": "0.9.2006", 
  }
</pre>

## <a name="using-microsoftmixedrealityinput"></a>Usando Microsoft. MixedReality. Input 

### <a name="input-values"></a>Valores de entrada

Um MotionController pode expor dois tipos de entradas: 

* Os botões e os Estados de gatilho são expressos por um valor float exclusivo entre 0,0 e 1,0 que indica quanto eles são pressionados.
    * Um botão só pode retornar 0,0 (quando não pressionado) ou 1,0 (quando pressionado) enquanto um gatilho pode retornar valores contínuos entre 0,0 (totalmente lançado) para 1,0 (totalmente pressionado). 
* O estado Thumbstick é expresso por um vector2 cujos componentes X e Y estão entre-1,0 e 1,0. 

Você pode usar *MotionController. GetPressableInputs ()* para retornar uma lista de entradas que retornam um valor pressionado (botões e gatilhos) ou o método *MotionController. GetXYInputs ()* para retornar uma lista de entradas que retornam um valor de eixo 2. 

Uma instância de MotionControllerReading representa o estado do controlador em um determinado momento: 

* *Getpressionvalue ()* recupera o estado de um botão ou um gatilho. 
* *GetXYValue ()* recupera o estado de um Thumbstick. 

### <a name="creating-a-cache-to-maintain-a-collection-of-motioncontroller-instances-and-their-states"></a>Criando um cache para manter uma coleção de instâncias MotionController e seus Estados 

Comece instanciando um MotionControllerWatcher e Registrando manipuladores para seus eventos *MotionControllerAdded* e *MotionControllerRemoved* para manter um cache de instâncias de MotionController disponíveis. Esse cache deve ser um monobehavior anexado a um gameobject, conforme demonstrado no código a seguir:

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

### <a name="reading-new-inputs-by-polling"></a>Lendo novas entradas por sondagem 

Você pode ler o estado atual de cada controlador conhecido por meio de *MotionController. TryGetReadingAtTime* durante o método *Update* da classe monobehavior. Você deseja passar *DateTime. Now* como o parâmetro timestamp para garantir que o estado mais recente do controlador seja lido. 

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

Você pode obter o valor de entrada atual dos controladores usando a destro/canhoto do controlador: 

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

Por exemplo, para ler o valor de Segure analógico de uma interação: 

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

### <a name="generating-events-from-the-new-inputs"></a>Gerando eventos a partir das novas entradas 

Em vez de sondar o estado de um controlador uma vez por quadro, você tem a opção de lidar com todas as alterações de estado como eventos, o que permite que você manipule até as ações mais rápidas que têm menos de um quadro. Para que essa abordagem funcione, o cache de controladores de movimento precisa processar todos os Estados publicados por um controlador desde o último quadro, o que pode ser feito armazenando o carimbo de data/hora do último MotionControllerReading recuperado de um MotionController e chamando *MotionController. TryGetReadingAfterTime ()*: 

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

Agora que você atualizou as classes internas do cache, a classe monobehavior pode expor dois eventos – pressionado e liberado – e os elevamos a partir do seu método Update (): 

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

A estrutura nos exemplos de código acima torna o registro de eventos muito mais legível: 

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

## <a name="see-also"></a>Confira também

<!-- ## Getting started

There's no additional setup required to use the HP Reverb G2 controller if you're developing for SteamVR or using the Windows Mixed Reality Input API (XR.WSA.Input). However, the A, B, X, Y buttons and the squeeze trigger are not currently accessible through the Input Manager unless you're using SteamVR. Support for the extra Reverb G2 inputs will be available in the near future, so be sure to check back!

## Porting existing applications

If you already have an existing app that you're developing for Windows Mixed Reality immersive headsets, check out our [porting guide](../porting-apps/porting-guides.md) and [project settings](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=project#unity-porting-guidance) sections for general suggestions.

## Mapping input

When you're ready to get your input mapping up and running for your new controllers, start at the [input mapping](https://docs.microsoft.com/windows/mixed-reality/develop/porting-apps/porting-guides?tabs=input#unity-porting-guidance) section of the immersive porting guide. Instructions on how to configure inputs in Unity is detailed in [Gestures and motion controllers](gestures-and-motion-controllers-in-unity.md), along with a full [button and axis mapping table](gestures-and-motion-controllers-in-unity.md#using-hp-reverb-g2-controllers) for reference.

## See also
* [Updating for SteamVR](../porting-apps/updating-your-steamvr-application-for-windows-mixed-reality.md) -->