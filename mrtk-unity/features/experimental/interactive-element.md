---
title: Elemento interativo
description: Documentação de MRTK interativaelement
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, elemento interativo, interagir
ms.openlocfilehash: 65f518c53414d68d3a9d2093cb427140cc65560b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144763"
---
# <a name="interactive-element-experimental"></a>Elemento interativo [experimental]

Um ponto de entrada centralizado simplificado para o sistema de entrada MRTK. Contém métodos de gerenciamento de estado, gerenciamento de eventos e a lógica de configuração de estado para os Estados de interação principal.

O elemento interativo é um recurso experimental com suporte no Unity 2019,3 e como ele utiliza uma funcionalidade nova para o Unity 2019,3: [serializar referência](https://docs.unity3d.com/ScriptReference/SerializeReference.html).

### <a name="interactive-element-inspector"></a>Inspetor de elemento interativo

Durante o modo de reprodução, o Inspetor de elemento interativo fornece comentários visuais que indicam se o estado atual está ativo ou não. Se um estado estiver ativo, ele será realçado com uma cor ciano.  Se o estado não estiver ativo, a cor não será alterada. Os números ao lado dos Estados no Inspetor são os valores de estado, se o estado estiver ativo, o valor será 1, se o estado não estiver ativo, o valor será 0.

![Elemento interativo com interação de mão virtual](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>Estados principais

O elemento interativo contém Estados principais e dá suporte à adição de [Estados personalizados](#custom-states).  Um estado de núcleo é aquele que já tem a lógica de configuração de estado definida em `BaseInteractiveElement` . A seguir está uma lista de Estados básicos controlados por entrada atuais: 

### <a name="current-core-states"></a>Estados principais atuais

- [Padrão](#default-state) 

Estados principais de interação próxima e longe:
- [Foco](#focus-state) 

Estados principais de interação próxima:

- [Foco próximo](#focus-near-state)
- [Tocar](#touch-state)

Estados principais de interação distante:
- [Foco Distante](#focus-far-state)
- [Selecione Distante](#select-far-state)

Outros estados principais:
- [Clicado](#clicked-state)
- [Alternar e alternar Para Desligar](#toggle-on-and-toggle-off-state)
- [Palavra-chave speech](#speech-keyword-state)

### <a name="how-to-add-a-core-state-via-inspector"></a>Como adicionar um estado principal por meio do Inspetor

1. Navegue **até Adicionar Estado Principal** no inspetor do Elemento Interativo.

    ![Adicionar um estado principal por meio do Inspetor](../images/interactive-element/InEditor/InteractiveElementAddCoreState.png)


1. Selecione o **botão Selecionar Estado** para escolher o estado principal a ser acrescentado. Os estados no menu são classificar por tipo de interação.

    ![Adicionar um estado principal por meio do Inspetor com o estado selecionado](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectState.png)

1. Abra o dobrado Configuração de Eventos para exibir os eventos e propriedades associados ao estado.

    ![Adicionar um estado principal por meio do Inspetor com a configuração de evento](../images/interactive-element/InEditor/InteractiveElementAddCoreStateSelectStateEventConfig.png)


### <a name="how-to-add-a-core-state-via-script"></a>Como adicionar um estado principal por meio de script

Use o `AddNewState(stateName)` método para adicionar um estado principal. Para uma lista dos nomes de estado principais disponíveis, use `CoreInteractionState` a enum.

```c#
// Add by name or add by CoreInteractionState enum to string

interactiveElement.AddNewState("SelectFar");

interactiveElement.AddNewState(CoreInteractionState.SelectFar.ToString());
```

### <a name="states-internal-structure"></a>Estrutura interna de estados 

Os estados no Elemento Interativo são do tipo `InteractionState` .  Um `InteractionState` contém as seguintes propriedades:

- **Nome**: o nome do estado.
- **Valor**: o valor de estado.  Se o estado for on, o valor do estado será 1. Se o estado for off, o valor de estado será 0.
- **Ativo**: se o estado está ativo no momento. O valor da propriedade ativa é true quando o estado for on, false se o estado for off. 
- **Tipo de interação**: o tipo de interação de um estado é o tipo de interação de que um estado é destinado. 
  - `None`: Não oferece suporte a qualquer forma de interação de entrada.
  - `Near`: Suporte a interação próxima. A entrada é considerada próxima à interação quando uma mão articulada tem contato direto com outro objeto de jogo, ou seja, a posição da mão articulada está perto da posição do objeto de jogo no espaço de mundo.
  - `Far`: Suporte de interação distante. A entrada é considerada longe da interação quando o contato direto com o objeto de jogo não é necessário. Por exemplo, a entrada por meio do controlador Ray ou olhar é considerada uma entrada de interação distante.
  - `NearAndFar`: Abrange o suporte à interação próxima e a extrema. 
  - `Other`: Suporte à interação independente de ponteiro.
- **Configuração de evento**: a configuração de evento para um estado é o ponto de entrada do perfil de eventos serializados. 

Todas essas propriedades são definidas internamente no `State Manager` elemento interativo contido. Para a modificação de Estados, use os seguintes métodos auxiliares:

**Métodos auxiliares de configuração de estado**

```c# 
// Get the InteractionState
interactiveElement.GetState("StateName");

// Set a state value to 1/on
interactiveElement.SetStateOn("StateName");

// Set a state value to 0/off
interactiveElement.SetStateOff("StateName");

// Check if a state is present in the state list
interactiveElement.IsStatePresent("StateName");

// Check whether or not a state is active
interactiveElement.IsStateActive("StateName");

// Add a new state to the state list
interactiveElement.AddNewState("StateName");

// Remove a state from the state list
interactiveElement.RemoveState("StateName");
```

Obter a configuração de evento de um estado é específica para o próprio estado. Cada estado principal tem um tipo de configuração de evento específico que é descrito abaixo nas seções que descrevem cada estado principal.

Aqui está um exemplo generalizado de como obter a configuração de evento de um estado:

```c#
// T varies depending on the core state - the specific T's are specified under each of the core state sections
T stateNameEvents = interactiveElement.GetStateEvents<T>("StateName");
```

### <a name="default-state"></a>Estado padrão

O estado Padrão está sempre presente em um Elemento Interativo.  Esse estado estará ativo somente quando todos os outros estados não estão ativos.  Se qualquer outro estado se tornar ativo, o estado Padrão será definido como off internamente. 

Um Elemento Interativo é inicializado com os estados Padrão e Foco presentes na lista de estados. O estado Padrão sempre precisa estar presente na lista de estados. 

#### <a name="getting-default-state-events"></a>Obter eventos de estado padrão

Tipo de configuração de evento para o Estado Padrão: `StateEvents`

```c#
StateEvents defaultEvents = interactiveElement.GetStateEvents<StateEvents>("Default");

defaultEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State On");
});

defaultEvents.OnStateOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Default State Off");
});
```

### <a name="focus-state"></a>Estado de foco

O estado de Foco é um estado de interação próximo e distante que pode ser pensado como a realidade misturada equivalente a focalizar. O fator de distinção entre a interação próxima e distante para o estado foco é o tipo de ponteiro ativo atual.  Se o tipo de ponteiro para o estado De foco for o Ponteiro de Ponteiro, a interação será considerada quase interação.  Se o ponteiro primário não for o Ponteiro de Ponteiro de Ponteiro, a interação será considerada interação distante. O estado De foco está presente no Elemento Interativo por padrão.

**Comportamento do estado de foco** 
 ![ Estado de foco com interação de mão virtual](../images/interactive-element/InEditor/Gifs/FocusStateEditor.gif) 

**Inspetor de Estado de Foco** 
 ![ Estado de foco no Inpsector](../images/interactive-element/InEditor/FocusStateInspector.png)

#### <a name="getting-focus-state-events&quot;></a>Obter eventos de estado de foco

Tipo de configuração de evento para o Estado de Foco: `FocusEvents`

```c#
FocusEvents focusEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;Focus");

focusEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus On");
});

focusEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Focus Off");
});
```

#### <a name="focus-near-vs-focus-far-behavior"></a>Foco próximo versus comportamento distante do foco 

![Concentre-se perto e longe da interação com a mão virtual](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>Foco próximo ao estado

O foco próximo do estado é definido quando um evento de foco é gerado e o ponteiro principal é o ponteiro de adseção, uma indicação de interação próxima. 

**Focalizar comportamento** 
 ![ de estado próximo Foco próximo ao estado com interação virtual](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**Foco próximo ao inspetor** 
 ![ de estado Foco próximo ao componente no Inspetor](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>Obtendo eventos de estado FocusNear

Tipo de configuração de evento para o estado FocusNear: `FocusEvents`

```c#
FocusEvents focusNearEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusNear");

focusNearEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus On");
});

focusNearEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Near Interaction Focus Off");
});
```

### <a name="focus-far-state"></a>Estado distante do foco

O estado de foco é definido quando o ponteiro principal não é o ponteiro de enfrente.  Por exemplo, o ponteiro de raio do controlador padrão e o ponteiro GGV (olhar, gesto, voz) são considerados ponteiros de interação distantes.

Comportamento do estado **distante do foco** 
 ![ Estado de foco muito com interação virtual](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

Inspetor de estado **distante do foco** 
 ![ Componente de foco no Inspetor](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>Obtendo eventos de estado distante do foco

Tipo de configuração de evento para o estado FocusFar: `FocusEvents`

```c#
FocusEvents focusFarEvents = interactiveElement.GetStateEvents<FocusEvents>(&quot;FocusFar");

focusFarEvents.OnFocusOn.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus On");
});

focusFarEvents.OnFocusOff.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Focus Off");
});
```

### <a name="touch-state"></a>Estado de toque

O estado de toque é um estado de interação próxima que é definido quando uma mão articulada toca o objeto diretamente.  Um toque direto significa que o dedo do índice da mão articulada está muito próximo da posição mundial do objeto. Por padrão, um `NearInteractionTouchableVolume` componente é anexado ao objeto se o estado de toque for adicionado à lista de estado.  A presença de um  `NearInteractionTouchableVolume` `NearInteractionTouchable` componente ou é necessária para detectar eventos de toque.  A diferença entre `NearInteractionTouchableVolume` e `NearInteractionTouchable` é que o `NearInteractionTouchableVolume` detecta um toque com base no colisor do objeto e `NearInteractionTouchable` detecta o toque em uma área definida de um plano.

**Comportamento do estado de toque** 
 ![ Estado de toque com interação de mão virtual](../images/interactive-element/InEditor/Gifs/TouchStateEditor.gif)

**Inspetor de Estado de Toque** 
 ![ Componente de estado de toque no Inspetor](../images/interactive-element/InEditor/TouchStateInspector.png)

#### <a name="getting-touch-state-events&quot;></a>Obter eventos de estado de toque

Tipo de configuração de evento para o Estado de Toque: `TouchEvents`

```c#
TouchEvents touchEvents = interactiveElement.GetStateEvents<TouchEvents>(&quot;Touch");

touchEvents.OnTouchStarted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Started");
});

touchEvents.OnTouchCompleted.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Completed");
});

touchEvents.OnTouchUpdated.AddListener((touchData) =>
{
    Debug.Log($"{gameObject.name} Touch Updated");
});
```

### <a name="select-far-state"></a>Selecionar Estado Distante

O estado Selecionar Longe é `IMixedRealityPointerHandler` a superfície.  Esse estado é um estado de interação distante que detecta um clique de interação distante (toque de ar) e mantém o uso de ponteiros de interação distantes, como o ponteiro de raio do controlador padrão ou o ponteiro GGV.  O estado Selecionar Longe tem uma opção no dobramento de configuração de evento chamado `Global` . Se `Global` for true, o `IMixedRealityPointerHandler` será registrado como um manipulador de entrada global.  O foco em um objeto não é necessário para disparar eventos do sistema de entrada se um manipulador for registrado como global.  Por exemplo, se um usuário quiser saber sempre que o gesto de toque no ar/seleção for executado, independentemente do objeto em foco, de definido `Global` como true. 

**Selecionar Comportamento de Estado Distante** 
 ![ Selecionar distante com interação com a mão virtual](../images/interactive-element/InEditor/Gifs/SelectFarStateEditor.gif)

**Selecione Inspetor de Estado Distante** 
 ![ Selecione o componente distante no Inspetor](../images/interactive-element/InEditor/SelectFarStateInspector.png)

#### <a name="getting-select-far-state-events&quot;></a>Obter eventos de estado selecionados

Tipo de configuração de evento para o estado SelectFar: `SelectFarEvents`

```c#
SelectFarEvents selectFarEvents = interactiveElement.GetStateEvents<SelectFarEvents>(&quot;SelectFar");

selectFarEvents.OnSelectUp.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Up");
});

selectFarEvents.OnSelectDown.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Down");
});

selectFarEvents.OnSelectHold.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Hold");
});

selectFarEvents.OnSelectClicked.AddListener((pointerEventData) =>
{
    Debug.Log($"{gameObject.name} Far Interaction Pointer Clicked");
});
```

### <a name="clicked-state"></a>Estado clicado

O estado Clicado é disparado por um clique de interação distante (Selecione o estado Distante) por padrão.  Esse estado é alternado internamente para , invoca o evento OnClicked e, em seguida, é imediatamente desligado. 

> [!NOTE]
> Os comentários visuais no inspetor com base na atividade de estado não estão presentes para o estado Clicado porque ele é ligado e desligado imediatamente. 

**Comportamento de estado clicado** 
 ![ Estado clicado com interações de mão virtual](../images/interactive-element/InEditor/Gifs/ClickedStateEditor.gif)

Inspetor de estado **clicado** 
 ![ Clique no componente de estado no Inspetor](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Exemplo de estado pressionado próximo e longe**  
O estado clicado pode ser disparado por meio de pontos de entrada adicionais usando o `interactiveElement.TriggerClickedState()` método.  Por exemplo, se um usuário quiser um toque próximo à interação para disparar um clique em um objeto também, ele adicionará o `TriggerClickedState()` método como um ouvinte no estado de toque.   

![Estado próximo e distante com interações virtuais](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>Obtendo eventos de estado clicados

Tipo de configuração de evento para o estado clicado: `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>Ativar/desativar o estado

Os Estados ativar/desativar e desligar são um par e ambos precisam estar presentes para o comportamento de alternância.  Por padrão, os Estados de alternância e desativação são disparados por um clique de interação extrema (selecione estado distante).  Por padrão, o estado de desativação está ativo no início, o que significa que a alternância será inicializada como desativado.  Se um usuário desejar que o estado de alternância esteja ativo no início, em seguida, no estado ativar/desativar definido `IsSelectedOnStart` como true.

**Alternar e desativar o comportamento** 
 ![ do estado Ativar e desativar com interações virtuais](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

**Alternar e desativar o Inspetor** 
 ![ de estado Ativar/desativar componente no Inspetor](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Exemplo de Estados de alternância Near e far**  
Semelhante ao estado clicado, alternar configuração de estado pode ter vários pontos de entrada usando o `interactiveElement.SetToggleStates()` método. Por exemplo, se um usuário quiser tocar como um ponto de entrada adicional para definir os Estados de alternância, ele adicionará o `SetToggleStates()` método a um dos eventos no estado de toque. 

![Alternância próxima e longe com interações virtuais](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>Guia de alternância e desativação de eventos de estado

Tipo de configuração de evento para o estado de alternância: `ToggleOnEvents`  
Tipo de configuração de evento para o estado ToggleOff: `ToggleOffEvents`

```c#
// Toggle On Events
ToggleOnEvents toggleOnEvent = interactiveElement.GetStateEvents<ToggleOnEvents>(&quot;ToggleOn");

toggleOnEvent.OnToggleOn.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled On");
});

// Toggle Off Events
ToggleOffEvents toggleOffEvent = interactiveElement.GetStateEvents<ToggleOffEvents>("ToggleOff");

toggleOffEvent.OnToggleOff.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Toggled Off");
});
```

### <a name="speech-keyword-state"></a>Estado da palavra-chave speech

O estado palavra-chave de fala escuta as palavras-chave definidas no Perfil de Fala de Realidade Misturada. Qualquer nova palavra-chave DEVE ser registrada no perfil de comando de fala antes do runtime (etapas abaixo). 

**Comportamento de estado de palavra-chave de fala** 
 ![ Palavra-chave de fala com interação virtual](../images/interactive-element/InEditor/Gifs/SpeechKeywordStateEditor.gif)

**Inspetor de Estado da Palavra-chave de Fala** 
 ![ Componente de palavra-chave de fala no Inspetor](../images/interactive-element/InEditor/SpeechKeywordStateInspector.png)

> [!NOTE]
> O estado palavra-chave de fala foi disparado no editor pressionando a tecla F5 no gif acima. A configuração no teste do editor para fala é descrita nas etapas abaixo. 

#### <a name="how-to-register-a-speech-commandkeyword"></a>Como registrar um comando/palavra-chave de fala

1. Selecione o **objeto de jogo MixedRealityToolkit**

1. Selecione **Copiar e Personalizar** o perfil atual

1. Navegue até a seção Entrada e selecione **Clonar** para habilitar a modificação do perfil de Entrada

1. Scroll down à seção Fala no perfil de Entrada e clonar o Perfil de Fala

    ![Perfil de palavra-chave de fala no objeto de jogo do MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileClone.png) 

1. Selecione Adicionar um Novo Comando de Fala

    ![Adicionando uma nova palavra-chave de fala no perfil do MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeyword.png) 

1. Insira a nova palavra-chave. Opcional: altere o KeyCode para F5 (ou outro KeyCode) para permitir testes no editor. 

    ![Configurando a palavra-chave de fala no perfil do MRTK](../images/interactive-element/InEditor/SpeechKeywordProfileAddKeywordName.png) 

1. Go back ao inspetor de estado palavra-chave de fala do elemento interativo e selecione **Adicionar Palavra-chave** 

    ![Adicionando palavra-chave ao componente de elemento interativo](../images/interactive-element/InEditor/SpeechKeywordAddKeyword.png) 

    ![Validação e registro de palavra-chave](../images/interactive-element/InEditor/SpeechKeywordAddKeywordBlank.png) 

1. Insira a nova palavra-chave que acabou de ser registrada no perfil de fala

    ![Inserindo nova palavra-chave de fala](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


Para testar o estado da palavra-chave Speech no editor, pressione o código de tecla que foi definido na etapa 6 (F5) para simular o evento reconhecido da palavra-chave de fala.

#### <a name="getting-speech-keyword-state-events&quot;></a>Obtendo eventos de estado de palavra-chave de fala

Tipo de configuração de evento para o estado SpeechKeyword: `SpeechKeywordEvents`

```c#
SpeechKeywordEvents speechKeywordEvents = interactiveElement.GetStateEvents<SpeechKeywordEvents>(&quot;SpeechKeyword");

speechKeywordEvents.OnAnySpeechKeywordRecognized.AddListener((speechEventData) =>
{
    Debug.Log($"{speechEventData.Command.Keyword} recognized");
});

// Get the "Change" Keyword event specifically
KeywordEvent keywordEvent = speechKeywordEvents.Keywords.Find((keyword) => keyword.Keyword == "Change");

keywordEvent.OnKeywordRecognized.AddListener(() =>
{ 
    Debug.Log("Change Keyword Recognized"); 
});
```

## <a name="custom-states"></a>Estados personalizados

### <a name="how-to-create-a-custom-state-via-inspector"></a>Como criar um estado personalizado por meio do Inspetor 

O estado personalizado criado via inspector será inicializado com a configuração de evento de estado padrão. A configuração de evento padrão para um estado personalizado é do tipo `StateEvents` e contém os eventos Onstatee e OnStateOff.

1. Navegue até **criar estado personalizado** no Inspetor para elemento interativo.
    
    ![Criando um estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. Insira o nome do novo estado. Esse nome deve ser exclusivo e não pode ser o mesmo que os Estados principais existentes. 
    
    ![Inserindo o nome de um novo estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. Selecione **definir nome do estado** para adicionar à lista de estado.
    
    ![Adicionar estado personalizado à lista de estado](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   Esse estado personalizado é inicializado com a `StateEvents` configuração de evento padrão que contém os `OnStateOn` `OnStateOff` eventos e. Para criar uma configuração de evento personalizado para um novo estado, consulte: [criando um estado personalizado com uma configuração de evento personalizado](#creating-a-custom-state-with-a-custom-event-configuration).
    
    ![Novo estado mostrado no componente de elemento interativo](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateEventConfig.png)


### <a name="how-to-create-a-custom-state-via-script&quot;></a>Como criar um estado personalizado por meio de script

```c#
interactiveElement.AddNewState(&quot;MyNewState");

// A new state by default is initialized with a the default StateEvents configuration which contains the 
// OnStateOn and OnStateOff events

StateEvents myNewStateEvents = interactiveElement.GetStateEvents<StateEvents>("MyNewState");

myNewStateEvents.OnStateOn.AddListener(() =>
{
    Debug.Log($"MyNewState is On");
});

```

### <a name="creating-a-custom-state-with-a-custom-event-configuration"></a>Criando um estado personalizado com uma configuração de evento personalizado 

Os arquivos de exemplo para um estado personalizado chamado **Keyboard** estão localizados aqui: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

As etapas a seguir percorrem um exemplo existente de criação de uma configuração de evento de estado personalizado e arquivos de receptor.

1. Considere um nome de estado.  Esse nome deve ser exclusivo e não pode ser o mesmo que os Estados principais existentes. Para os fins deste exemplo, o nome do estado será **teclado**.

1. Crie dois arquivos. cs chamados nome do estado + "receptor" e nome do estado + "eventos". A nomenclatura desses arquivos é levada em consideração internamente e deve seguir o nome do estado + Convenção do evento/receptor. 

    ![Scripts de estado do teclado](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. Consulte os arquivos KeyboardEvents. cs e KeyboardReceiver. cs para obter mais detalhes sobre o conteúdo do arquivo. Novas classes de configuração de evento devem herdar de `BaseInteractionEventConfiguration` e novas classes de receptor de eventos devem herdar de `BaseEventReceiver` .  Os exemplos na configuração de estado do estado do teclado estão localizados no `CustomStateSettingExample.cs` arquivo. 

1. Adicione o estado ao elemento interativo usando o nome do estado, o nome do estado será reconhecido se existirem arquivos de configuração de evento e receptor de evento.  As propriedades no arquivo de configuração de evento personalizado devem aparecer no Inspetor.

    ![Adicionando estado personalizado ao elemento interativo ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ estado personalizado reconhecido no elemento interativo](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. Para obter mais exemplos de configuração de evento e de arquivos receptor de eventos, consulte os arquivos nestes caminhos:    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>Cena de exemplo 

A cena de exemplo para elemento interativo + Visualizador de estado está localizada aqui: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![Cena de exemplo com elemento interativo e visualizador de estado](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Botão compactável

A cena de exemplo contém pré-fabricados nomeado `CompressableButton` e `CompressableButtonToggle` , esses pré-fabricados espelham o comportamento dos `PressableButtonHoloLens2` botões, que são construídos usando o elemento interativo e o Visualizador de estado. No `CompressableButton` momento, o componente é uma combinação de `PressableButton`  +  `PressableButtonHoloLens2` com `BaseInteractiveElement` como uma classe base. 

## <a name="state-visualizer-experimental"></a>Visualizador de estado [experimental]

O componente Visualizador de estado adiciona animações a um objeto com base nos Estados definidos em um componente de elemento interativo vinculado. Esse componente cria ativos de animação, coloca-os na pasta MixedRealityToolkit. Generated e habilita a configuração de quadro-chave de animação simplificada por meio da adição de propriedades animáveis a um objeto de jogo de destino. Para habilitar transições de animação entre Estados, um ativo do controlador Animator é criado e uma máquina de estado padrão é gerada com parâmetros associados e quaisquer transições de estado.  A máquina de estado pode ser exibida na janela Animator do Unity.

### <a name="state-visualizer-and-unity-animation-system"></a>Visualizador de estado e sistema de animação Unity

O Visualizador de estado atualmente utiliza o sistema de animação do Unity. 

Quando o botão **gerar novos clipes de animação** no Visualizador de estado é pressionado, novos ativos de clipe de animação são gerados com base nos nomes de estado no elemento interativo e são colocados na pasta MixedRealityToolkit. Generated. A propriedade clipe de animação em cada contêiner de estado é definida como o clipe de animação associado.

![Clipes de animação no componente do Visualizador de estado](../images/interactive-element/StateVisualizer/AnimationClips.png)

Um [computador de estado Animator](https://docs.unity3d.com/Manual/AnimationOverview.html) também é gerado para gerenciar transições suaves entre clipes de animação.  Por padrão, a máquina de estado utiliza o [estado any](https://docs.unity3d.com/Manual/class-State.html) para permitir transições entre qualquer estado no elemento interativo. 

[Os visualizadores de estado](https://docs.unity3d.com/Manual/AnimationParameters.html) disparados no animador também são gerados para cada estado, os parâmetros de gatilho são usados no Visualizador de Estado para disparar uma animação.

![Computador de estado do Unity](../images/interactive-element/StateVisualizer/UnityStateMachine.png)

### <a name="runtime-limitations"></a>Limitações do Runtime 

O Visualizador de Estado deve ser adicionado a um objeto por meio do Inspetor e não pode ser adicionado por meio de script.  As propriedades que modificam o AnimatorStateMachine/AnimationController estão contidas em um namespace do editor ( ) que é removido `UnityEditor.Animations` quando o aplicativo é criado.

## <a name="how-to-use-the-state-visualizer"></a>Como usar o Visualizador de Estado

1. Criar um cubo
1. Anexar elemento interativo
1. Anexar Visualizador de Estado
1. Selecione **Gerar Novos Clipes de Animação**

    ![Gerando novos clipes de animação](../images/interactive-element/StateVisualizer/GenerateAnimationClips.png)

    ![Mostrando clipes de animação gerados em componentes de elemento interativo e visualizador](../images/interactive-element/StateVisualizer/GenerateAnimationClips2.png)

1. No contêiner Estado de foco, selecione **Adicionar Destino**

    ![Adicionando o destino do visualizador de estado](../images/interactive-element/StateVisualizer/AddTarget.png)

1. Arraste o objeto do jogo atual para o campo de destino 

    ![Definindo o destino do visualizador de estado](../images/interactive-element/StateVisualizer/SetTarget.png)

1. Abra o dobrado Propriedades Animatable do Cubo
1. Selecione o menu suspenso propriedade Animatable e selecione **Cor**

    ![Definindo a cor do visualizador de estado](../images/interactive-element/StateVisualizer/SetColor.png)

1. Selecione **Adicionar a propriedade Color Animatable**

    ![Selecionando a propriedade animatable de cor do visualizador](../images/interactive-element/StateVisualizer/SetColorProperty.png)

1. Escolher uma cor 

    ![Escolhendo uma cor do visualisador no disco de cores](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. Pressione reproduzir e observe a alteração de cor de transição

    ![Exemplo de alteração de cor de transição com interação de mão virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Propriedades animáveis

A principal finalidade das propriedades animáveis é simplificar a configuração de quadro-chave do clipe de animação.  Se um usuário estiver familiarizado com o sistema de animação do Unity e preferir definir diretamente os quadros-chave nos clipes de animação gerados, eles poderão simplesmente não adicionar propriedades animáveis a um objeto de destino e abrir o clipe na janela de animação do Unity (animação de > de animação do Windows >). 

Se estiver usando as propriedades animáveis para animação, o tipo de curva será definido como EaseInOut.

**Propriedades animáveis atuais:**
- [Deslocamento de escala](#scale-offset)
- [Deslocamento da posição](#position-offset)
- [Cor](#color)
- [Cor do sombreador](#shader-color)
- [Sombreador float](#shader-float)
- [Vetor de sombreador](#shader-vector)

### <a name="scale-offset"></a>Deslocamento de escala

A propriedade animada de deslocamento de escala usa a escala atual do objeto e adiciona o deslocamento definido.

![Deslocamento de escala com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>Deslocamento da posição

A propriedade de deslocamento animada da posição usa a posição atual do objeto e adiciona o deslocamento definido.

![Deslocamento de posição com interação de mão virtual](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Color

A propriedade de cor animável representa a cor principal de um material se o material tiver uma propriedade de cor principal. Essa propriedade anima a `material._Color` propriedade.

![Alteração de cor do foco com interação de mão virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>Cor do sombreador

A propriedade animada de cor do sombreador refere-se a uma propriedade shader do tipo Color. Um nome de propriedade é necessário para todas as propriedades de sombreador. O GIF abaixo demonstra a animação de uma propriedade de cor do sombreador chamada Fill_Color que não é a cor do material principal.  Observe os valores de alteração no Inspetor de material.

![Cor de sombreamento com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>Sombreador float

A propriedade animada do sombreador float se refere a uma propriedade shader do tipo float. Um nome de propriedade é necessário para todas as propriedades de sombreador. No gif abaixo, observe os valores de alteração no Inspetor de material para a propriedade metálica. 

![Sombreador float com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>Vetor de sombreador

A propriedade animá vector Shader se refere a uma propriedade shader do tipo Vector4. Um nome de propriedade é necessário para todas as propriedades de sombreador. No gif abaixo, observe os valores de alteração no Inspetor de material para a propriedade de colocação em disposição (principal Tex_ST). 

![Vetor de sombreador com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>Como localizar nomes de propriedades de sombreador animáveis

1. Navegue até a > animação > janela
1. Verifique se o objeto com o Visualizador de Estado está selecionado na hierarquia
1. Selecione qualquer clipe de animação na janela Animação
1. Selecione **Adicionar Propriedade**, abra o foldout do Renderador de Malha 

    ![Adicionando a propriedade de animação na janela Animator](../images/interactive-element/StateVisualizer/AnimationWindow.png)

1. Esta lista contém os nomes de todos os nomes de propriedade Animatable 

    ![Propriedades de animação do renderdor de malha na janela Animator](../images/interactive-element/StateVisualizer/MeshRendererProperties.png)

## <a name="see-also"></a>Confira também

- [**Botões**](../ux-building-blocks/button.md)
- [**Controle de limites**](../ux-building-blocks/bounds-control.md)
- [**Coleção de objetos de grade**](../ux-building-blocks/object-collection.md)
- [**Solucionador RadialView**](../ux-building-blocks/solvers/solver.md)
