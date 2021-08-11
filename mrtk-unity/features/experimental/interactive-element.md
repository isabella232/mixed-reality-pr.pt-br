---
title: Elemento interativo
description: Documentação do INTERACTIVEElement MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 02/22/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Elemento Interativo, Interativo
ms.openlocfilehash: 6d8f36c4780844e991eb32943645402503fab8340c6843dbb607f1c11033d912
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115220298"
---
# <a name="interactive-element-experimental"></a>Elemento Interativo [Experimental]

Um ponto de entrada centralizado simplificado para o sistema de entrada do MRTK. Contém métodos de gerenciamento de estado, gerenciamento de eventos e a lógica de configuração de estado para estados de interação principais.

O Elemento Interativo é um recurso experimental com suporte no Unity 2019.3 e para cima, pois utiliza uma funcionalidade nova para o Unity 2019.3: [Serializar](https://docs.unity3d.com/ScriptReference/SerializeReference.html)Referência .

### <a name="interactive-element-inspector"></a>Inspetor de Elemento Interativo

Durante o modo de reprodução, o inspetor do Elemento Interativo fornece comentários visuais que indicam se o estado atual está ativo ou não. Se um estado estiver ativo, ele será realçado com uma cor ciano.  Se o estado não estiver ativo, a cor não será alterada. Os números ao lado dos estados no inspetor são os valores de estado. Se o estado estiver ativo, o valor será 1, se o estado não estiver ativo, o valor será 0.

![Elemento Interativo com interação de mão virtual](../images/interactive-element/InEditor/Gifs/InspectorHighlightEditor.gif)

## <a name="core-states"></a>Estados principais

O Elemento Interativo contém estados principais e dá suporte à adição de [estados personalizados.](#custom-states)  Um estado principal é aquele que já tem a lógica de configuração de estado definida em `BaseInteractiveElement` . Veja a seguir uma lista dos estados principais atuais orientados por entrada: 

### <a name="current-core-states"></a>Estados principais atuais

- [Padrão](#default-state) 

Estados principais de interação próxima e distante:
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

- **Nome:** o nome do estado.
- **Valor**: o valor do estado.  Se o estado estiver, o valor de estado será 1. Se o estado estiver desligado, o valor do estado será 0.
- **Ativo:** se o estado está ativo ou não no momento. O valor da propriedade Active será true quando o estado estiver ativado, false se o estado estiver desligado. 
- **Tipo de** Interação: o Tipo de Interação de um estado é o tipo de interação para o qual um estado se destina. 
  - `None`: não dá suporte a nenhuma forma de interação de entrada.
  - `Near`: suporte à interação próxima. A entrada é considerada quase interação quando uma mão articulada tem contato direto com outro objeto de jogo, ou seja, a posição que a mão articulada está próxima da posição do objeto do jogo no espaço do mundo.
  - `Far`: suporte à interação distante. A entrada é considerada interação distante quando o contato direto com o objeto do jogo não é necessário. Por exemplo, a entrada por meio do raio do controlador ou do olhar é considerada entrada de interação distante.
  - `NearAndFar`: abrange o suporte à interação próxima e distante. 
  - `Other`: suporte à interação independente de ponteiro.
- **Configuração de** Evento: a configuração de evento para um estado é o ponto de entrada do perfil de eventos serializados. 

Todas essas propriedades são definidas internamente no `State Manager` contido no Elemento Interativo. Para modificação de estados, use os seguintes métodos auxiliares:

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

Obter a configuração de evento de um estado é específico para o próprio estado. Cada estado principal tem um tipo de configuração de evento específico que é descrito abaixo nas seções que descrevem cada estado principal.

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

![Foco próximo e distante com interação com a mão virtual](../images/interactive-element/InEditor/Gifs/FocusNearFocusFar.gif)

### <a name="focus-near-state"></a>Foco próximo ao estado

O estado Foco Próximo é definido quando um evento de foco é gerado e o ponteiro primário é o ponteiro Desfoque, uma indicação de interação próxima. 

**Comportamento de foco próximo do estado** 
 ![ Foco próximo ao estado com interação com a mão virtual](../images/interactive-element/InEditor/Gifs/FocusNearStateEditor.gif) 

**Foco próximo ao Inspetor de Estado** 
 ![ Foco próximo do componente no Inspetor](../images/interactive-element/InEditor/FocusNearStateInspector.png)

#### <a name="getting-focusnear-state-events&quot;></a>Obter eventos de estado FocusNear

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

### <a name="focus-far-state"></a>Estado de foco distante

O estado Foco Distante é definido quando o ponteiro primário não é o ponteiro Pointer.  Por exemplo, o ponteiro de raio do controlador padrão e o ponteiro GGV (Gaze, Gesto, Voz) são considerados ponteiros de interação distantes.

**Comportamento do estado de foco distante** 
 ![ Estado de foco distante com interação de mão virtual](../images/interactive-element/InEditor/Gifs/FocusFarStateEditor.gif)

**Inspetor de Estado de Foco Distante** 
 ![ Componente de foco distante no Inspetor](../images/interactive-element/InEditor/FocusFarStateInspector.png)

#### <a name="getting-focus-far-state-events&quot;></a>Obter eventos de estado distante de foco

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

O estado de Toque é um estado de interação próxima que é definido quando uma mão articulada toca o objeto diretamente.  Um toque direto significa que o dedo indicador da mão articulada está muito próximo à posição do mundo do objeto. Por padrão, um `NearInteractionTouchableVolume` componente será anexado ao objeto se o estado Touch for adicionado à lista de estado.  A presença de um  `NearInteractionTouchableVolume` componente ou é necessária para detectar eventos `NearInteractionTouchable` touch.  A diferença entre e é que detecta um toque com base no colisor do objeto e detecta o toque dentro de uma área `NearInteractionTouchableVolume` `NearInteractionTouchable` definida de um `NearInteractionTouchableVolume` `NearInteractionTouchable` plano.

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

**Inspetor de Estado Clicado** 
 ![ Clique no componente de estado no Inspetor](../images/interactive-element/InEditor/ClickedStateInspector.png)

**Exemplo de estado próximo e muito clicado**  
O estado clicado pode ser disparado por meio de pontos de entrada adicionais usando o `interactiveElement.TriggerClickedState()` método .  Por exemplo, se um usuário quiser um toque de interação próxima para disparar um clique em um objeto também, ele adicionará o método como um ouvinte no estado `TriggerClickedState()` de toque.   

![Estado próximo e distante com interações de mão virtual](../images/interactive-element/InEditor/Gifs/NearFarClickedState.gif)

#### <a name="getting-clicked-state-events&quot;></a>Recebendo eventos de estado clicados

Tipo de configuração de evento para o Estado Clicado: `ClickedEvents`

```c#
ClickedEvents clickedEvent = interactiveElement.GetStateEvents<ClickedEvents>(&quot;Clicked");

clickedEvent.OnClicked.AddListener(() =>
{
    Debug.Log($"{gameObject.name} Clicked");
});
```

### <a name="toggle-on-and-toggle-off-state"></a>Alternar o estado De desligar e Desligar

Os estados De alternância e Desligar são um par e ambos precisam estar presentes para o comportamento de alternância.  Por padrão, os estados Ativar/Ativar e Ativar/Desligar são disparados por meio de um clique de interação distante (selecione o estado Distante).  Por padrão, o estado Desativar está ativo na inicialização, o que significa que a alternância será inicializada como off.  Se um usuário quiser que o estado Alternar Ativado seja ativo no início, no estado Alternar Ativado definido `IsSelectedOnStart` como true.

**Comportamento de estado de alternância e de alternância** 
 ![ Alternar e desligar com interações de mão virtual](../images/interactive-element/InEditor/Gifs/ToggleOnToggleOffStateEditor.gif)

Inspetor de Estado de **Alternância e Desligar** 
 ![ Alternar componente no Inspetor](../images/interactive-element/InEditor/ToggleOnToggleOffStateInspector.png)

**Exemplo de estados de alternância próximos e distantes**  
Semelhante ao estado Clicado, a configuração de estado de alternância pode ter vários pontos de entrada usando o `interactiveElement.SetToggleStates()` método . Por exemplo, se um usuário quiser toque como um ponto de entrada adicional para definir os estados de alternância, ele adicionará o método a um dos eventos no `SetToggleStates()` estado Toque. 

![Alternância próxima e distante com interações de mão virtual](../images/interactive-element/InEditor/Gifs/NearFarToggleStates.gif)

#### <a name="getting-toggle-on-and-toggle-off-state-events&quot;></a>Como alternar e alternar eventos de estado

Tipo de configuração de evento para o estado ToggleOn: `ToggleOnEvents`  
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

1. Insira a nova palavra-chave que acabou de ser registrada no Perfil de Fala

    ![Inserindo uma nova palavra-chave de fala](../images/interactive-element/InEditor/SpeechKeywordEnterKeyword.png) 


Para testar o estado palavra-chave de fala no editor, pressione KeyCode definido na etapa 6 (F5) para simular o evento reconhecido da palavra-chave de fala.

#### <a name="getting-speech-keyword-state-events&quot;></a>Obter eventos de estado de palavra-chave de fala

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

O estado personalizado criado por meio do inspetor será inicializado com a configuração de evento de estado padrão. A configuração de evento padrão para um estado personalizado é do tipo `StateEvents` e contém os eventos OnStateOn e OnStateOff.

1. Navegue **até Criar Estado Personalizado** no inspetor do Elemento Interativo.
    
    ![Criando um estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomState.png)

1. Insira o nome do novo estado. Esse nome deve ser exclusivo e não pode ser o mesmo que os estados principais existentes. 
    
    ![Inserindo o nome de um novo estado personalizado](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateName.png)

1. Selecione **Definir Nome do Estado** para adicionar à lista de estados.
    
    ![Adicionar estado personalizado à lista de estados](../images/interactive-element/InEditor/InteractiveElementCreateCustomStateNameSet.png)

   Esse estado personalizado é inicializado com a configuração `StateEvents` de evento padrão que contém os eventos e `OnStateOn` `OnStateOff` . Para criar uma configuração de evento personalizada para um novo estado, consulte: [Criando um estado personalizado com uma configuração de evento personalizado.](#creating-a-custom-state-with-a-custom-event-configuration)
    
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

Arquivos de exemplo para um estado personalizado chamado **Teclado** estão localizados aqui: MRTK\SDK\Experimental\InteractiveElement\Examples\Scripts\CustomStateExample

As etapas a seguir explicam um exemplo existente de criação de uma configuração de evento de estado personalizado e arquivos receptores.

1. Pense em um nome de estado.  Esse nome deve ser exclusivo e não pode ser o mesmo que os estados principais existentes. Para os fins deste exemplo, o nome do estado será **Teclado**.

1. Crie dois arquivos .cs chamados state name + "Receiver" e state name + "Events". A nomeação desses arquivos é levada em consideração internamente e deve seguir o nome do estado + Convenção de Evento/Receptor. 

    ![Scripts de estado do teclado](../images/interactive-element/InEditor/KeyboardStateFiles.png)

1. Consulte os arquivos KeyboardEvents.cs e KeyboardReceiver.cs para obter mais detalhes sobre o conteúdo do arquivo. Novas classes de configuração de evento devem herdar `BaseInteractionEventConfiguration` de e novas classes de receptor de evento devem herdar de `BaseEventReceiver` .  Exemplos de configuração de estado para o estado Teclado estão localizados no `CustomStateSettingExample.cs` arquivo. 

1. Adicione o estado ao Elemento Interativo usando o nome do estado, o nome do estado será reconhecido se existirem arquivos de configuração de evento e receptor de evento.  As propriedades no arquivo de configuração de evento personalizado devem aparecer no inspetor.

    ![Adicionando estado personalizado ao elemento interativo ](../images/interactive-element/InEditor/AddKeyboardState.png) ![ Estado personalizado reconhecido no elemento interativo](../images/interactive-element/InEditor/SetKeyboardStateName.png)


1. Para obter mais exemplos de configuração de evento e arquivos de receptor de eventos, consulte os arquivos nestes caminhos:    
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventConfigurations
- MRTK\SDK\Experimental\InteractiveElement\InteractiveElement\Events\EventReceivers

## <a name="example-scene"></a>Cena de exemplo 

A cena de exemplo do Elemento Interativo + Visualizador de Estado está localizada aqui: MRTK\SDK\Experimental\InteractiveElement\Examples\InteractiveElementExampleScene.unity

![Cena de exemplo com Elemento Interativo e Visualizador de Estado](../images/interactive-element/InEditor/ExampleScene.png)

### <a name="compressable-button"></a>Botão compactado

A cena de exemplo contém pré-fabs chamados e , esses pré-fabs espelham o comportamento dos botões, que são construídos usando o Elemento Interativo e `CompressableButton` `CompressableButtonToggle` o `PressableButtonHoloLens2` Visualizador de Estado. Atualmente, `CompressableButton` o componente é uma combinação de com como uma classe `PressableButton`  +  `PressableButtonHoloLens2` `BaseInteractiveElement` base. 

## <a name="state-visualizer-experimental"></a>Visualizador de Estado [Experimental]

O componente Visualizador de Estado adiciona animações a um objeto com base nos estados definidos em um componente do Elemento Interativo vinculado. Esse componente cria ativos de animação, coloca-os na pasta MixedRealityToolkit.Generated e habilita a configuração de keyframe de animação simplificada por meio da adição de propriedades Animatable a um objeto de jogo de destino. Para habilitar transições de animação entre estados, um ativo do Controlador de Animator é criado e um computador de estado padrão é gerado com parâmetros associados e quaisquer transições de estado.  O computador de estado pode ser exibido na janela Animator do Unity.

### <a name="state-visualizer-and-unity-animation-system"></a>Visualizador de Estado e Sistema de Animação do Unity

Atualmente, o Visualizador de Estado aproveita o Sistema de Animação do Unity. 

Quando  o botão Gerar Novos Clipes de Animação no Visualizador de Estado é pressionado, novos ativos de clipe de animação são gerados com base nos nomes de estado no Elemento Interativo e são colocados na pasta MixedRealityToolkit.Generated. A propriedade Clipe de Animação em cada contêiner de estado é definida como o clipe de animação associado.

![Clipes de animação no componente visualizador de estado](../images/interactive-element/StateVisualizer/AnimationClips.png)

Um [Computador de Estado animador também](https://docs.unity3d.com/Manual/AnimationOverview.html) é gerado para gerenciar transições suaves entre clipes de animação.  Por padrão, o computador de estado utiliza Qualquer [Estado](https://docs.unity3d.com/Manual/class-State.html) para permitir transições entre qualquer estado no Elemento Interativo. 

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

    ![Escolhendo uma cor do visualizador na roda de cores](../images/interactive-element/StateVisualizer/SetBlueColor.png)

1. Pressione Reproduzir e observe a alteração de cor de transição

    ![Exemplo de alteração de cor de transição com interação com a mão virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

## <a name="animatable-properties"></a>Propriedades animaíveis

A principal finalidade das Propriedades Animatable é simplificar a configuração de keyframe do clipe de animação.  Se um usuário estiver familiarizado com o Sistema de Animação do Unity e preferir definir diretamente os keyframes nos clipes de animação gerados, ele simplesmente não poderá adicionar propriedades Animatable a um objeto de destino e abrir o clipe na janela Animação do Unity (animação Windows > animação >). 

Se estiver usando as propriedades Animatable para animação, o tipo de curva será definido como EaseInOut.

**Propriedades animaíveis atuais:**
- [Deslocamento de escala](#scale-offset)
- [Deslocamento de posição](#position-offset)
- [Cor](#color)
- [Cor do sombreador](#shader-color)
- [Float do sombreador](#shader-float)
- [Vetor de sombreador](#shader-vector)

### <a name="scale-offset"></a>Deslocamento de escala

A propriedade Animatable de Deslocamento de Escala pega a escala atual do objeto e adiciona o deslocamento definido.

![Deslocamento de escala com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ScaleOffset.gif)

### <a name="position-offset"></a>Deslocamento de posição

A propriedade Animatable deslocamento de posição assume a posição atual do objeto e adiciona o deslocamento definido.

![Deslocamento de posição com interação de mão virtual](../images/interactive-element/InEditor/Gifs/PositionOffset.gif)

### <a name="color"></a>Color

A propriedade Color Animatable representará a cor principal de um material se o material tiver uma propriedade de cor principal. Essa propriedade anima a `material._Color` propriedade .

![Alteração de cor de foco com interação com a mão virtual](../images/interactive-element/InEditor/Gifs/FocusColorChange.gif)

### <a name="shader-color"></a>Cor do sombreador

A propriedade Animatable de Cor do Sombreador refere-se a uma propriedade de sombreador da cor do tipo. Um nome de propriedade é necessário para todas as propriedades do sombreador. O gif abaixo demonstra a animação de uma propriedade de cor do sombreador chamada Fill_Color que não é a cor principal do material.  Observe os valores de alteração no inspetor de material.

![Sombrear cor com interação com a mão virtual](../images/interactive-element/InEditor/Gifs/ShaderColor.gif)

### <a name="shader-float"></a>Float do sombreador

A propriedade Animatable Float do Sombreador refere-se a uma propriedade de sombreador do tipo float. Um nome de propriedade é necessário para todas as propriedades do sombreador. No gif abaixo, observe os valores de alteração no inspetor de material para a propriedade Demão. 

![Flutuação do sombreador com interação com a mão virtual](../images/interactive-element/InEditor/Gifs/ShaderFloat.gif)

### <a name="shader-vector"></a>Vetor de sombreador

A propriedade Animatable vector do sombreador refere-se a uma propriedade de sombreador do tipo Vector4. Um nome de propriedade é necessário para todas as propriedades do sombreador. No gif abaixo, observe os valores de alteração no inspetor de material para a propriedade Til (Tex_ST) . 

![Vetor de sombreador com interação de mão virtual](../images/interactive-element/InEditor/Gifs/ShaderVector.gif)


### <a name="how-to-find-animatable-shader-property-names"></a>Como encontrar nomes de propriedade do sombreador animatable

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
