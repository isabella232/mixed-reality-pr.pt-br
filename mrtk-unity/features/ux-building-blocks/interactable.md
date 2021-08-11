---
title: Interativo
description: Visão geral sobre o componente de script interagir no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, interagir, eventos,
ms.openlocfilehash: a0aee99d01ae59a8ebedc4d62a4b0aaf844a7afaa6961bbfd05238dd9d5b673d
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115206752"
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

![Configurações de interação geral](../images/interactable/InputFeatures_short.png)

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

**Habilitada**

Alterna se um interagindo será iniciado ou não. Isso corresponde ao [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) no código.

Uma propriedade habilitada *de interação* é diferente da Propriedade habilitada configurada por meio de gameobject/componente (ou seja, SetActive etc.). A desabilitação do Jogoobject ou do monocomportamento *interagir* desabilitará a execução de tudo na classe, incluindo entrada, temas visuais, eventos, etc. A desabilitação via [`Interactable.IsEnabled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.IsEnabled) desabilitará a maioria dos tratamentos de entrada, redefinindo os Estados de entrada relacionados. No entanto, a classe ainda executará todos os quadros e receberá eventos de entrada que serão ignorados. Isso é útil para exibir o interagir em um estado desabilitado que pode ser feito por meio de temas visuais. Um exemplo típico disso seria um botão enviar aguardando a conclusão de todos os campos de entrada necessários.

**Ações de entrada**

Selecione a [ação de entrada](../input/input-actions.md) do perfil de configuração de entrada ou de mapeamento do controlador ao qual o componente *interagindo* deve reagir.

Essa propriedade pode ser configurada em tempo de execução no código via [`Interactable.InputAction`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.InputAction) .

**IsGlobal**

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

![Exemplo de receptor de alternância de evento](../images/interactable/Event_toggle.png)

*Exemplo de um receptor de evento de alternância*

### <a name="interactable-receivers"></a>Receptores interagidos

 O [`InteractableReceiver`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiver) componente permite que os eventos sejam definidos fora do componente *Interactable de origem.* O *InteractableReceiver* escutará um tipo de evento filtrado disparado por outro *Interacionável.* Se a propriedade *Interactable* não for  atribuída diretamente, a propriedade Escopo da Pesquisa definirá a direção em que *InteractableReceiver* escuta eventos que estão em si, em um pai ou em um GameObject filho.

[`InteractableReceiverList`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableReceiverList) atua de maneira semelhante, mas para uma lista de eventos correspondentes.

<img src="../images/interactable/InteractableReceiver.png" width="450" alt="Interactable reciver">

### <a name="create-custom-events"></a>Criar eventos personalizados

Assim [como os Temas Visuais,](visual-themes.md#custom-theme-engines)os eventos podem ser estendidos para detectar qualquer padrão de estado ou para expor a funcionalidade.

Eventos personalizados podem ser criados de duas maneiras principais:

1) Estenda [`ReceiverBase`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) a classe para criar um evento personalizado que será aparecer na lista suspenso de tipos de evento. Um evento do Unity é fornecido por padrão, mas eventos adicionais do Unity podem ser adicionados ou o evento pode ser definido para ocultar eventos do Unity. Essa funcionalidade permite que um designer trabalhe com um engenheiro em um projeto para criar um evento personalizado que o designer pode configurar no editor.

1) Estenda [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) a classe para criar um componente de evento completamente personalizado que pode residir no *Interactable* ou em outro objeto. O [`ReceiverBaseMonoBehavior`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBaseMonoBehavior) fará referência ao *Interactable para* detectar alterações de estado.

#### <a name="example-of-extending-receiverbase"></a>Exemplo de extensão `ReceiverBase`

A [`CustomInteractablesReceiver`](xref:Microsoft.MixedReality.Toolkit.UI) classe exibe informações de status sobre um *Interactable* e é um exemplo de como criar um Receptor de Eventos personalizado.

```c#
public CustomInteractablesReceiver(UnityEvent ev) : base(ev, "CustomEvent")
{
    HideUnityEvents = true; // hides Unity events in the receiver - meant to be code only
}
```

Os métodos a seguir são úteis para substituir/implementar ao criar um Receptor de Eventos personalizado. [`ReceiverBase.OnUpdate()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) é um método abstrato que pode ser usado para detectar padrões de estado/transições. Além disso, os [`ReceiverBase.OnVoiceCommand()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) métodos e são úteis para criar uma lógica de evento personalizada quando o [`ReceiverBase.OnClick()`](xref:Microsoft.MixedReality.Toolkit.UI.ReceiverBase) *Interactable* é selecionado.

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

##### <a name="displaying-custom-event-receiver-fields-in-the-inspector"></a>Exibindo campos de receptor de eventos personalizados no inspetor

Os scripts *ReceiverBase* usam [`InspectorField`](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.InspectorField) atributos para expor propriedades personalizadas no inspetor. Aqui está um exemplo de Vector3, uma propriedade personalizada com informações de dica de ferramenta e rótulo. Essa propriedade será acionada como configurável no inspetor quando um  GameObject Interacionável for selecionado e tiver o tipo de Receptor *de* Eventos associado adicionado.

```c#
[InspectorField(Label = "<Property label>",Tooltip = "<Insert tooltip info>",Type = InspectorField.FieldTypes.Vector3)]
public Vector3 EffectOffset = Vector3.zero;
```

## <a name="how-to-use-interactable"></a>Como usar o Interactable

### <a name="building-a-simple-button"></a>Criando um botão simples

É possível criar um botão simples adicionando *o componente Interacionável* a um GameObject configurado para receber eventos de entrada. Ele pode ter um colisor nele ou em um filho para receber entrada. Se estiver *usando o Interactable* com um GameObjects baseado na interface do usuário do Unity, ele deverá estar no GameObject da Tela.

Dê um passo a mais no botão, criando um novo perfil, atribuindo o gameObject em si e criando um novo tema. Além disso, use o *evento OnClick* para fazer algo acontecer.

> [!NOTE]
> Tornar um [botão pressionável](button.md) requer o [`PressableButton`](xref:Microsoft.MixedReality.Toolkit.UI.PressableButton) componente . Além disso, o componente [`PhysicalPressEventRouter`](xref:Microsoft.MixedReality.Toolkit.PhysicalPressEventRouter) é necessário para funilar eventos de pressiona para *o componente Interactable.*

### <a name="creating-toggle-and-multi-dimension-buttons"></a>Criando botões de alternância e várias dimensões

#### <a name="toggle-button"></a>Botão de alternância

Para fazer com que um botão Seja capaz de alternar, altere o [`Selection Mode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) campo para o tipo `Toggle` . Na seção *Perfis,* um novo tema alternado é adicionado para cada perfil que é usado quando *o Interactable* é alternado.

Embora o seja definido como Alternância, a caixa de seleção IsToggled pode ser usada para definir o valor padrão do controle na [`SelectionMode`](xref:Microsoft.MixedReality.Toolkit.UI.SelectionModes) inicialização do  runtime.

*CanSelect* significa que *o Interactable* pode ir de *off* para *on* enquanto *CanDeselect* significa o inverso.

![Exemplo de temas visuais de alternância de perfil](../images/interactable/Profile_toggle.png)

Os desenvolvedores podem utilizar [`SetToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) [`IsToggled`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) as interfaces e para obter/definir o estado de alternância de *um Interactable* por meio de código.

```c#
// If using SelectionMode = Toggle (i.e Dimensions == 2)

// Make the Interactable selected and toggled on
myInteractable.IsToggled = true;

// Get whether the Interactable is selected or not
bool isSelected = myInteractable.IsToggled;
```

##### <a name="toggle-button-collection"></a>Coleção de botões de alternância

É comum ter uma lista de botões de alternância em que apenas um pode estar ativo a qualquer momento, também conhecido como um conjunto radial ou botões de rádio etc.

Use o [`InteractableToggleCollection`](xref:Microsoft.MixedReality.Toolkit.UI.InteractableToggleCollection) componente para habilitar essa funcionalidade. Esse controle garante que apenas um *Interactable* seja alternado em um determinado momento. O *RadialSet* (Assets/MRTK/SDK/Features/UX/Interactable/Prefabs/RadialSet.prefab) também é um ótimo ponto de partida.

Para criar um grupo de botões radial personalizado:

1) Criar  vários GameObjects/botões interacionáveis
1) Definir cada *Interactable with* *SelectionMode* = Toggle, *CanSelect* = true e *CanDeselect* = false
1) Crie um GameObject pai vazio em todos os *Interactables* e adicione o *componente InteractableToggleCollection*
1) Adicionar todos *os Interactables* ao *ToggleList* na *InteractableToggleCollection*
1) Definir a *propriedade InteractableToggleCollection.CurrentIndex* para determinar qual botão é selecionado por padrão no início

<img src="../images/interactable/InteractableToggleCollection.png" width="450" alt="Toggle collection">

#### <a name="multi-dimensional-button"></a>Botão multidimensional

O modo de seleção de várias dimensões é usado para criar botões sequenciais ou um botão que tem mais de duas etapas, como controlar a velocidade com três valores, Rápido (1x), Mais Rápido (2x) ou Mais Rápido (3x).

Com as dimensões sendo um valor numérico, até 9 temas podem ser adicionados para controlar o rótulo de texto ou a textura do botão para cada configuração de velocidade, usando um tema diferente para cada etapa.

Cada evento de clique avançará `DimensionIndex` o em 1 no runtime até que `Dimensions` o valor seja atingido. Em seguida, o ciclo será redefinido para 0.

![Exemplo de perfil multidimensional](../images/interactable/Profile_multiDimensions.png)

Os desenvolvedores podem avaliar [`DimensionIndex`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) o para determinar qual dimensão está ativa no momento.

```c#
// If using SelectionMode = Multi-dimension (i.e Dimensions >= 3)

//Access the current DimensionIndex
int currentDimension = myInteractable.CurrentDimension;

//Set the current DimensionIndex to 2
myInteractable.CurrentDimension = 2;

// Promote Dimension to next level
myInteractable.IncreaseDimension();
```

### <a name="create-interactable-at-runtime"></a>Criar interação em runtime

*Interagir pode* ser facilmente adicionado a qualquer GameObject em runtime. O exemplo a seguir demonstra como atribuir um perfil com um [tema visual](visual-themes.md).

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

### <a name="interactable-events-via-code"></a>Eventos interagidos por meio de código

É possível adicionar uma ação ao evento base [`Interactable.OnClick`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable.OnClick) por meio de código com o exemplo a seguir.

```c#
public static void AddOnClick(Interactable interactable)
{
    interactable.OnClick.AddListener(() => Debug.Log("Interactable clicked"));
}
```

Use a [`Interactable.AddReceiver<T>()`](xref:Microsoft.MixedReality.Toolkit.UI.Interactable) função para adicionar receptores de eventos dinamicamente em runtime.

O código de exemplo a seguir demonstra como adicionar um [InteractableOnFocusReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escuta o foco enter/exit e, além disso, define o código de ação a ser realizado quando as instâncias de evento são acionada.

```c#
public static void AddFocusEvents(Interactable interactable)
{
    var onFocusReceiver = interactable.AddReceiver<InteractableOnFocusReceiver>();

    onFocusReceiver.OnFocusOn.AddListener(() => Debug.Log("Focus on"));
    onFocusReceiver.OnFocusOff.AddListener(() => Debug.Log("Focus off"));
}
```

O código de exemplo a seguir demonstra como adicionar um [InteractableOnToggleReceiver](xref:Microsoft.MixedReality.Toolkit.UI.InteractableOnFocusReceiver), que escuta transições de estado selecionadas/deselecionadas em *Interactables* com alternância e, além disso, define o código de ação a ser realizado quando as instâncias de evento são acionadas.

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
* [Comandos de Fala](../input/speech.md)
* [Botões](button.md)
* [Sombreador Padrão do MRTK](../rendering/MRTK-standard-shader.md)
