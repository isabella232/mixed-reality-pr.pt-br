---
title: Interativo
description: Visão geral sobre o componente de script interagir no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, interagir, eventos,
ms.openlocfilehash: f141a394ec9395e0a27cc964caeb66654fb6fe08
ms.sourcegitcommit: 47c402dc8e588817ce60229bf019170fa36f3045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2021
ms.locfileid: "107581558"
---
# <a name="interactable"></a>Interativo

![Interativo](../images/interactable/InteractableExamples.png)

O [`Interactable`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) componente é um contêiner All-in-One para tornar qualquer objeto fácil de *interagir* e de responder à entrada. A interação interage com todos os tipos de entrada, incluindo toque, raios para a mão, fala, etc. e funil dessas interações em [eventos](#events) e respostas de [tema Visual](visual-themes.md) . Esse componente fornece uma maneira fácil de criar botões, alterar a cor em objetos com foco e muito mais.

## <a name="how-to-configure-interactable"></a>Como configurar o interagir

O componente permite três seções principais de configuração:

1) [Configuração de entrada geral](#general-input-settings)
1) [Temas visuais](visual-themes.md) direcionados a vários Gameobjects
1) [Manipuladores de eventos](#events)

### <a name="general-input-settings"></a>Configurações de entrada gerais

![Configurações gerais de interação](../images/interactable/InputFeatures_short.png)

**Estados**

*Estados* é um parâmetro [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) que define as fases de interações, como Press ou Observad, para perfis de [elementos e temas](visual-themes.md)de [interação](#interactable-profiles) .

O **DefaultInteractableStates** (assets/MRTK/SDK/Features/UX/interagible/States/DefaultInteractableStates. Asset) é fornecido com o MRTK pronto para uso e é o parâmetro padrão para componentes que *interagem* .

![Exemplo de Estados ScriptableObject no Inspetor](../images/interactable/DefaultInteractableStates.png)

O ativo *DefaultInteractableStates* contém quatro Estados e utiliza a [`InteractableStates`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableStates) implementação do modelo de estado.

* **Padrão**: nada está acontecendo, esse é o estado base mais isolado.

* **Foco**: o objeto está sendo apontado para. Este é um estado único, não há outros Estados atualmente definidos, mas ele deixará o padrão de classificação.

* **Pressione**: o objeto está sendo apontado para e um botão ou mão está pressionando. As classificações de estado de saída de pressionamento padrão e foco. Esse estado também será definido como um fallback para a prensa física.

* **Desabilitado**: o botão não deve ser interativo e os comentários visuais permitirão que o usuário saiba se, por algum motivo, esse botão não pode ser usado no momento. Teoricamente, o estado desabilitado pode conter todos os outros Estados, mas quando habilitado está desativado, o estado desabilitado supera todos os outros Estados.

Um valor de bit (#) é atribuído ao estado, dependendo da ordem na lista.

> [!NOTE]
> Geralmente, é recomendável utilizar o **DefaultInteractableStates** (assets/MRTK/SDK/Features/UX/interajable/DefaultInteractableStates. Asset) ao criar componentes de *interação* .
>
> No entanto, há 17 Estados interagindo disponíveis que podem ser usados para impulsionar temas, embora algumas sejam direcionadas a outros componentes. Aqui está uma lista delas com funcionalidade interna.
>
> * Visitado: o interagir foi clicado.
> * Alternado: o botão está em um estado de alternância ou o índice de dimensão é um número ímpar.
> * Gesto: a mão ou o controlador foi pressionado e movido da posição original.
> * VoiceCommand: um comando de fala foi usado para disparar o interagir.
> * PhysicalTouch: uma entrada de toque está detectada no momento; use [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) para habilitar.
> * Captura: uma mão está atualmente captando os limites do objeto, use [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) para habilitar

**Enabled**

Alterna se um interagindo será iniciado ou não. Isso corresponde ao [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) no código.

Uma propriedade habilitada *de interação* é diferente da Propriedade habilitada configurada por meio de gameobject/componente (ou seja, SetActive etc.). A desabilitação do Jogoobject ou do monocomportamento *interagir* desabilitará a execução de tudo na classe, incluindo entrada, temas visuais, eventos, etc. A desabilitação via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) desabilitará a maioria dos tratamentos de entrada, redefinindo os Estados de entrada relacionados. No entanto, a classe ainda executará todos os quadros e receberá eventos de entrada que serão ignorados. Isso é útil para exibir o interagir em um estado desabilitado que pode ser feito por meio de temas visuais. Um exemplo típico disso seria um botão enviar aguardando a conclusão de todos os campos de entrada necessários.

**Ações de entrada**

Selecione a [ação de entrada](../input/input-actions.md) do perfil de configuração de entrada ou de mapeamento do controlador ao qual o componente *interagindo* deve reagir.

Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .

**Caso IsGlobal**

Se for true, o componente será marcado como um ouvinte de entrada global para a [ação de entrada](../input/input-actions.md)selecionada. O comportamento padrão é false, que restringirá a entrada somente a esse colisor ou gameobject de *interação* .

Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.IsGlobal`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsGlobal) .

**Comando de fala**

[Comando de fala](../input/speech.md), do perfil de comandos de fala do MRTK, para disparar um evento OnClick para interação de voz.

Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.VoiceCommand`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceCommand) .

**Requer foco**

Se for true, o comando de voz só ativará o *interage* se e somente se ele já tiver o foco de um ponteiro. Se for false, o que poderá ser *interagido* atuará como um ouvinte global para o comando de voz selecionado. O comportamento padrão é true, pois vários ouvintes de fala global podem ser difíceis de organizar em uma cena.

Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.VoiceRequiresFocus`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.VoiceRequiresFocus) .

**Modo de seleção**

Essa propriedade define a lógica de seleção. Quando um usuário *interage* é clicado, ele faz a iteração em um nível de *dimensão* seguinte. As *dimensões* são semelhantes à classificação e define um estado fora das entradas (ou seja, foco, pressione etc.). Eles são úteis para definir Estados de alternância ou outros Estados de várias classificações associados a um botão. O nível de dimensão atual é acompanhado pelo `Interactable.DimensionIndex` .

Os modos de seleção disponíveis são:

* **Botão**  -  *Dimensões* = 1, fácil de clicar  simples
* **Alternar**  -  *Dimensões* = *2, alternativas*  / *interligadas* entre o estado desativado
* **Várias dimensões**  -  *Dimensions* >= 3, cada clique aumenta o nível de dimensão atual + 1. Útil para definir um estado de botão para uma lista, etc.

*Interagir* também permite que vários temas sejam definidos por *dimensão*. Por exemplo, quando *SelectionMode = Toggle*, um tema pode ser aplicado quando o *interagir* é *desmarcado* e outro tema aplicado quando o componente é *selecionado*.

O modo de seleção atual pode ser consultado em tempo de execução via [`Interactable.ButtonMode`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.ButtonMode) . A atualização do modo em tempo de execução pode ser obtida definindo a  [`Interactable.Dimensions`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.Dimensions) propriedade para corresponder à funcionalidade desejada. Além disso, a dimensão atual, útil para *alternar* e modos de *várias dimensões* , pode ser acessada via [`Interactable.CurrentDimension`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.CurrentDimension) .

### <a name="interactable-profiles"></a>Perfis de interação

*Perfis* são itens que criam uma relação entre um gameobject e um [tema Visual](visual-themes.md). O perfil define qual conteúdo será manipulado por um tema quando ocorrer uma [alteração de estado](#general-input-settings).

Os temas funcionam muito parecidos com materiais. Eles são objetos programáveis que contêm uma lista de propriedades que serão atribuídas a um objeto com base no estado atual. Os temas também são reutilizáveis e podem ser atribuídos em vários objetos UX *interagindo* .

**Redefinir em destruir**

Os temas visuais modificam várias propriedades em um gameobject direcionado, dependendo da classe e do tipo de mecanismo de tema selecionado. Se *Redefinir em Destroy* for verdadeiro quando o componente interagindo for destruído, o componente redefinirá todas as propriedades modificadas de temas ativos para seus valores originais. Caso contrário, quando destruído, o componente que poderá interagir deixará todas as propriedades modificadas como estão. Nesse último caso, o último estado dos valores persistirá, a menos que seja alterado por outro componente externo. O padrão é falso.

<img src="../images/interactable/Profiles_Themes.png" width="450" alt="Profile theams">

## <a name="events"></a>Eventos

Cada componente que *interage* tem um evento *onclick* que é acionado quando o componente é simplesmente selecionado. No entanto, *interagir* pode ser usado para detectar eventos de entrada que não sejam apenas *onclick*.

Clique no botão *Adicionar evento* para adicionar um novo tipo de definição de receptor de evento. Depois de adicionado, selecione o tipo de evento desejado.

![Exemplo de eventos](../images/interactable/Events.png))

Há diferentes tipos de receptores de eventos para responder a diferentes tipos de entrada. O MRTK é fornecido com o seguinte conjunto de receptores prontos para uso.

* [`InteractableAudioReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableAudioReceiver)
* [`InteractableOnClickReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnClickReceiver)
* [`InteractableOnFocusReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver)
* [`InteractableOnGrabReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnGrabReceiver)
* [`InteractableOnHoldReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnHoldReceiver)
* [`InteractableOnPressReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnPressReceiver)
* [`InteractableOnToggleReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnToggleReceiver)
* [`InteractableOnTouchReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnTouchReceiver)

Um receptor personalizado pode ser criado criando-se uma nova classe que se estende [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) .

![Exemplo de receptor de alternância de eventos](../images/interactable/Event_toggle.png)

*Exemplo de um receptor de evento de alternância*

### <a name="interactable-receivers"></a>Receptores interagir

 O [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente permite que os eventos sejam definidos fora do componente de origem *interagir* . O *InteractableReceiver* escutará um tipo de evento filtrado disparado por outro *interagir*. Se a propriedade *interagir* não for atribuída diretamente, a propriedade *escopo da pesquisa* definirá a direção que o *InteractableReceiver* escutará por eventos que estejam em si, em um pai ou em um gameobject filho.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) age de maneira semelhante, mas para obter uma lista de eventos correspondentes.

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>Criar eventos personalizados

Como os [temas visuais](visual-themes.md#custom-theme-engines), os eventos podem ser estendidos para detectar qualquer padrão de estado ou para expor a funcionalidade.

Os eventos personalizados podem ser criados de duas maneiras principais:

1) Estenda a [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) classe para criar um evento personalizado que aparecerá na lista suspensa de tipos de eventos. Um evento do Unity é fornecido por padrão, mas outros eventos do Unity podem ser adicionados ou o evento pode ser definido para ocultar eventos do Unity. Essa funcionalidade permite que um designer trabalhe com um engenheiro em um projeto para criar um evento personalizado que o designer pode configurar no editor.

1) Estenda a [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) classe para criar um componente de evento completamente personalizado que pode residir em um ou outro objeto que possa ser *interagindo* . O [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) fará referência às alterações de estado que são *interagirs* para detectar.

#### <a name="example-of-extending-receiverbase"></a>Exemplo de extensão `ReceiverBase`

A [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) classe exibe informações de status sobre um *interagindo* e é um exemplo de como criar um receptor de evento personalizado.

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

Os métodos a seguir são úteis para substituir/implementar ao criar um receptor de evento personalizado. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) é um método abstrato que pode ser usado para detectar padrões/transições de estado. Além disso, [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) os [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) métodos e são úteis para a criação de lógica de evento Personalizada quando a *interação* é selecionada.

```c#
public override void OnUpdate(InteractableStates state, Interactable source)
{
    if (state.CurrentState() != lastState)
    {
        // the state has changed, do something new
        lastState = state.CurrentState();
        ...
    }
}

public virtual void OnVoiceCommand(InteractableStates state, Interactable source,
                                    string command, int index = 0, int length = 1)
{
    base.OnVoiceCommand(state, source, command, index, length);
    // voice command called, perform some action
}  

public virtual void OnClick(InteractableStates state,
                            Interactable source,
                            IMixedRealityPointer pointer = null)
{
    base.OnClick(state, source);
    // click called, perform some action
}
```

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>Exibindo campos de receptor de eventos personalizados no Inspetor

Os scripts *ReceiverBase* usam [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) atributos para expor propriedades personalizadas no Inspetor. Aqui está um exemplo de Vector3, uma propriedade personalizada com dica de ferramenta e informações de rótulo. Essa propriedade será exibida como configurável no Inspetor quando um gameobject *interagindo* for selecionado e tiver o tipo de *receptor de evento* associado adicionado.

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Como usar o interagir

### <a name="building-a-simple-button"></a>Criando um botão simples

É possível criar um botão simples adicionando o componente *interagindo* a um gameobject configurado para receber eventos de entrada. Ele pode ter um colisor ou um filho para receber a entrada. Se você estiver usando *interagir* com uma interface do usuário baseada em Gameobjects, ela deverá estar sob o gameobject do Canvas.

Dê o botão um passo além, criando um novo perfil, atribuindo o próprio gameobject e criando um novo tema. Além disso, use o evento *onclick* para fazer algo acontecer.

> [!NOTE]
> Tornar um [botão pressionável](button.md) requer o [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) componente. Além disso, o [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) componente é necessário para encaminhada eventos de impressão para o componente *interagindo* .

### <a name="creating-toggle-and-multi-dimension-buttons"></a>Criando botões de alternância e de várias dimensões

#### <a name="toggle-button"></a>Botão de alternância

Para tornar um botão alternado, altere o [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo para tipo `Toggle` . Na seção de *perfis* , um novo tema alternado é adicionado para cada perfil que é usado quando o *interagir* é alternado.

Enquanto o [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) é definido como Toggle, a caixa de seleção *isalternated* pode ser usada para definir o valor padrão do controle na inicialização do tempo de execução.

*CanSelect* significa que o *interagindo* pode ir de *desativado* para *ativado* enquanto o *CanDeselect* significa o inverso.

![Exemplo de temas visuais de alternância de perfil](../images/interactable/Profile_toggle.png)

Os desenvolvedores podem utilizar [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) as [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) interfaces e para obter/definir o estado de alternância de um *interagindo* por meio de código.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>Alternar coleção de botões

É comum ter uma lista de botões de alternância em que apenas um pode estar ativo em um determinado momento, também conhecido como um conjunto radial ou botões de opção, etc.

Use o [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente para habilitar essa funcionalidade. Esse controle garante que apenas um *interagir* seja alternado em um determinado momento. O *radialset* (assets/MRTK/SDK/Features/UX/interajable/pré-fabricados/radialset. pré-fabricado) também é um ótimo ponto de partida pronto para uso.

Para criar um grupo de botões radiais personalizado:

1) Criar vários botões/Gameobjects *interagir*
1) Defina cada *interação* com *SelectionMode* = Toggle, *CanSelect* = true e *CanDeselect* = false
1) Criar um gameobject pai vazio em todos os *Interactables* e adicionar o componente *InteractableToggleCollection*
1) Adicionar todos os *Interactables* à barra de *alternância* no *InteractableToggleCollection*
1) Defina a propriedade *InteractableToggleCollection. CurrentIndex* para determinar qual botão está selecionado por padrão no início

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>Botão multidimensional

O modo de seleção de várias dimensões é usado para criar botões sequenciais ou um botão que tem mais de duas etapas, como controlar a velocidade com três valores, rápido (1x), mais rápido (2x) ou mais rápido (3x).

Com as dimensões sendo um valor numérico, podem ser adicionadas até 9 temas para controlar o rótulo de texto ou a textura do botão para cada configuração de velocidade, usando um tema diferente para cada etapa.

Cada evento de clique avançará em `DimensionIndex` 1 em tempo de execução até que o `Dimensions` valor seja atingido. Em seguida, o ciclo será redefinido como 0.

![Exemplo de perfil multidimensional](../images/interactable/Profile_multiDimensions.png)

Os desenvolvedores podem avaliar o [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) para determinar qual dimensão está ativa no momento.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>Criar interagindo em tempo de execução

O *interagir* pode ser facilmente adicionado a qualquer gameobject no tempo de execução. O exemplo a seguir demonstra como atribuir um perfil com um [tema Visual](visual-themes.md).

```c#
var interactableObject = GameObject.CreatePrimitive(PrimitiveType.Cylinder);
var interactable = interactableObject.AddComponent<Interactable>();

// Get the default configuration for the Theme engine InteractableColorTheme
var newThemeType = ThemeDefinition.GetDefaultThemeDefinition<InteractableColorTheme>().Value;

// Define a color for every state in our Default Interactable States
newThemeType.StateProperties[0].Values = new List<ThemePropertyValue>()
{
    new ThemePropertyValue() { Color = Color.black},  // Default
    new ThemePropertyValue() { Color = Color.black}, // Focus
    new ThemePropertyValue() { Color = Random.ColorHSV()},   // Pressed
    new ThemePropertyValue() { Color = Color.black},   // Disabled
};

interactable.Profiles = new List<InteractableProfileItem>()
{
    new InteractableProfileItem()
    {
        Themes = new List<Theme>()
        {
            Interactable.GetDefaultThemeAsset(new List<ThemeDefinition>() { newThemeType })
        },
        Target = interactableObject,
    },
};

// Force the Interactable to be clicked
interactable.TriggerOnClick()
```

### <a name="interactable-events-via-code"></a>Eventos de interação via código

É possível adicionar uma ação ao evento base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) por meio de código com o exemplo a seguir.

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

Use a [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) função para adicionar receptores de eventos dinamicamente no tempo de execução.

O código de exemplo abaixo demonstra como adicionar um [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escuta o foco entrar/sair e, além disso, define o código de ação a ser executado quando as instâncias de evento são acionadas.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

O código de exemplo abaixo demonstra como adicionar um [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escuta as transições de estado selecionadas/desmarcadas em *Interactables* de alternância habilitada e, além disso, define o código de ação a ser executado quando as instâncias de evento são acionadas.

```c#
public static void AddToggleEvents(Interactable interactable)
{
    var toggleReceiver = interactable.AddReceiver<InteractableOnToggleReceiver>();

    // Make the interactable have toggle capability, from code.
    // In the gui editor it's much easier
    interactable.Dimensions = 2;
    interactable.CanSelect = true;
    interactable.CanDeselect  = true;

    toggleReceiver.OnSelect.AddListener(() => Debug.Log("Toggle selected"));
    toggleReceiver.OnDeselect.AddListener(() => Debug.Log("Toggle un-selected"));
}
```

## <a name="see-also"></a>Confira também

* [Temas visuais](visual-themes.md)
* [Ações de entrada](../input/input-actions.md)
* [Comandos de fala](../input/speech.md)
* [Botões](button.md)
* [Sombreador padrão MRTK](../rendering/MRTK-standard-shader.md)
