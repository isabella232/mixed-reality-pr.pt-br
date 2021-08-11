---
title: Ponteiros
description: Documentação sobre ponteiros no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, Ponteiros,
ms.openlocfilehash: 9fec02e7866aaf867c7145491bfd84f727e039cdd7a4323ace9c65f74e49480a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190956"
---
# <a name="pointers"></a>Ponteiros

![Ponteiro](../images/pointers/MRTK_Pointer_Main.png)

Este artigo explica como configurar e responder à entrada de ponteiro na prática, em comparação com a [arquitetura de ponteiro](../../architecture/controllers-pointers-and-focus.md)

Os ponteiros são instâncias automaticamente em runtime quando um novo controlador é detectado. Mais de um ponteiro pode ser anexado a um controlador. Por exemplo, com o perfil de ponteiro padrão, os controladores Windows Mixed Reality obter uma linha e um ponteiro parabólico para seleção normal e seleção normal, respectivamente.

## <a name="pointer-configuration"></a>Configuração do ponteiro

Os ponteiros são configurados como parte do sistema de entrada no MRTK por meio de um [`MixedRealityPointerProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityPointerProfile) . Esse tipo de perfil é atribuído a um no inspetor de Configuração [`MixedRealityInputSystemProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityInputSystemProfile) do MRTK. O perfil Ponteiro determina o cursor, os tipos de Ponteiros disponíveis em runtime e como esses ponteiros se comunicam entre si para decidir qual deles está ativo.

- *Apontando extensão* – define a distância máxima para a qual um Ponteiro pode interagir com um GameObject.

- *Apontando máscaras* de camada raycast – essa é uma matriz priorizada de LayerMasks para determinar com quais possíveis GameObjects qualquer ponteiro determinado pode interagir e a ordem de interação a ser tentada. Isso pode ser útil para garantir que os ponteiros interajam com os elementos da interface do usuário primeiro antes de outros objetos de cena.
![Exemplo de perfil de ponteiro](../images/input/pointers/PointerProfile.PNG)

### <a name="pointer-options-configuration"></a>Configuração de opções de ponteiro

A configuração padrão do Perfil de Ponteiro do MRTK inclui as seguintes classes de ponteiro e pré-requisitos associados. A lista de ponteiros disponíveis para o sistema em runtime é definida em *Opções de Ponteiro* no perfil Ponteiro. Os desenvolvedores podem utilizar essa lista para reconfigurar ponteiros existentes, adicionar ponteiros novos ou excluir um.

![Exemplo de perfil de opções de ponteiro](../images/input/pointers/PointerOptionsProfile.PNG)

Cada entrada De ponteiro é definida pelo seguinte conjunto de dados:

- *Tipo de* Controlador – o conjunto de controladores para os qual um ponteiro é válido.
  - Por exemplo, *oPointer é* responsável por "cutucar" objetos com um dedo e é, por padrão, marcado como apenas para dar suporte ao tipo de controlador de mão articulado. Os ponteiros são instautados apenas quando um controlador fica disponível e, em particular, o Tipo de Controlador *define* com quais controladores esse pré-fab de ponteiro pode ser criado.

- *Mãos –* permite que um ponteiro seja instauenciado apenas para uma mão específica (esquerda/direita)

> [!NOTE]
> Definir a *propriedade Handedness* de uma entrada Ponteiro como *Nenhum* a desabilitará efetivamente do sistema como uma alternativa para remover esse Ponteiro da lista.

- *Pré-fab de* ponteiro – esse ativo de pré-fab será instauido quando um controlador que corresponde ao tipo de controlador e à entrega especificados começar a ser rastreado.

É possível ter vários ponteiros associados a um controlador. Por exemplo, em `DefaultHoloLens2InputSystemProfile` (Ativos/MRTK/SDK/Perfis/HoloLens2/) o controlador de mão articulado está associado com *oPointer,* *o GrabPointer* e o *DefaultControllerPointer* (ou seja, raios de mão).

> [!NOTE]
> O MRTK fornece um conjunto de pré-requisitos de ponteiro em *Ativos/MRTK/SDK/Recursos/UX/Prefabs/Ponteiros*. Um novo pré-fab personalizado pode ser criado desde que ele contenha um dos scripts de ponteiro em *Ativos/MRTK/SDK/Recursos/UX/Scripts/Ponteiros* ou qualquer outro script que implemente [`IMixedRealityPointer`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer) .

### <a name="default-pointer-classes"></a>Classes de ponteiro padrão

As classes a seguir são os ponteiros do MRTK in-box disponíveis e definidos no Perfil de Ponteiro *do MRTK* padrão descrito acima. Cada pré-fab de ponteiro fornecido em *Ativos/MRTK/SDK/Recursos/UX/Prefabs/Pointers* contém um dos componentes de ponteiro anexados.

![Ponteiros padrão do MRTK](../images/input/pointers/MRTK_Pointers.png)

#### <a name="far-pointers"></a>Ponteiros distantes

##### [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.LinePointer)

 *LinePointer*, uma classe de ponteiro base, desenha uma linha da origem da entrada (ou seja, o controlador) na direção do ponteiro e dá suporte a uma única redução de raio nessa direção. Em geral, as classes filho, como os ponteiros do e do teletransporte, são instauidas e utilizadas (que também desenham linhas para indicar em que ponto a teletransporte terminará) em vez dessa classe, que fornece principalmente funcionalidades [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) comuns.

Para controladores de movimento como em Oculus, Vive e Windows Mixed Reality, a rotação corresponderá à rotação do controlador. Para outros controladores, como HoloLens 2 mãos articuladas, a rotação corresponde à pose que aponta para o sistema da mão.

<img src="../images/pointers/MRTK_Pointers_Line.png" width="400" alt="MRTK Pointer Line">

##### [`CurvePointer`](xref:Microsoft.MixedReality.Toolkit.Input.CurvePointer)

*CurvePointer* estende a *classe LinePointer* permitindo que o raio de várias etapas seja lançado ao longo de uma curva. Essa classe de ponteiro base é útil para instâncias curvadas, como ponteiros de teletransporte, em que a linha se inclina consistentemente em um parano.

##### [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer)

A implementação de *ShellHandRayPointer,* que se estende de , é usada como o padrão para o Perfil de [`LinePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer) Ponteiro do *MRTK.* O *pré-fab DefaultControllerPointer* implementa a [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) classe .

##### [`GGVPointer`](xref:Microsoft.MixedReality.Toolkit.Input.GGVPointer)

Também conhecido como ponteiro de *foco/gesto/voz (GGV),* o GGVPoint HoloLens er aciona as interações de toque e aparência de estilo 1, principalmente por meio de foco e toque de ar ou foco e voz. A posição e a direção do ponteiro GGV são orientadas pela posição e rotação da cabeça.

##### [`TouchPointer`](xref:Microsoft.MixedReality.Toolkit.Input.TouchPointer)

O *TouchPointer* é responsável por trabalhar com a entrada do Unity Touch (ou seja, tela sensível ao toque). Essas são 'interações distantes' porque o ato de tocar na tela lançará um raio da câmera para um local potencialmente distante na cena.

##### [`MousePointer`](xref:Microsoft.MixedReality.Toolkit.Input.MousePointer)

O *MousePointer alimenta* uma tela para o raycast mundial para interações distantes, mas para o mouse em vez de toque.

![Ponteiro do mouse](../images/pointers/MRTK_MousePointer.png)

> [!NOTE]
> O suporte *ao* mouse não está disponível por padrão no MRTK, mas pode ser habilitado adicionando um novo Provedor de Dados entrada do tipo ao perfil de entrada do MRTK e atribuindo o ao provedor de [`MouseDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) [`MixedRealityMouseInputProfile`](xref:Microsoft.MixedReality.Toolkit.Input.MixedRealityMouseInputProfile) dados.

#### <a name="near-pointers"></a>Ponteiros próximos

##### [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)

*[OPointer doPointer](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer)* é usado para interagir com objetos de jogo que suportam "interação próxima que pode ser tocada". que são GameObjects que têm um [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) script anexado. No caso do UnityUI, esse ponteiro procura NearInteractionTouchableUnityUIs.  OPointer Dopointer usa um SphereCast para determinar o elemento que pode ser tocável mais próximo e é usado para ligar coisas como os botões pressionáveis.

 Ao configurar o GameObject com o componente, configure o parâmetro localForward para apontar para fora da frente do botão ou outro objeto que deve se tornar sensível [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) ao toque.  Além disso, certifique-se de que os limites do *touchable* corresponde aos limites do objeto sensível ao toque.

Propriedades úteis de Ponteiro de Ponteiro de Ponteiro:

- *TouchableDistance:* distância máxima com a qual uma superfície sensível ao toque pode ser interage
- *Visuais:* objeto de jogo usado para renderizar o visual de dica de dedo (o anel no dedo, por padrão).
- *Linha*: linha opcional para desenhar do dedo para a superfície de entrada ativa.
- *Máscaras de Camada de* Camada de Camada – uma matriz priorizada de LayerMasks para determinar com quais gameObjects o ponteiro pode interagir e a ordem de interação a ser tentada. Observe que um GameObject também deve ter um `NearInteractionTouchable` componente para interagir com um ponteiro de ponteiro.

<img src="../images/pointers/MRTK_PokePointer.png" width="400" alt="Poke Pointer">

##### [`SpherePointer`](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)

O *[SpherePointer](xref:Microsoft.MixedReality.Toolkit.Input.SpherePointer)* usa [UnityEngine.Physics.OverlapSphere](https://docs.unity3d.com/ScriptReference/Physics.OverlapSphere.html) para identificar o objeto mais próximo para interação, o que é útil para [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) entrada "acessível", como `ManipulationHandler` o . Semelhante ao par funcional, para interagir com o Ponteiro sphere, o objeto do jogo deve conter um componente [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) / [`NearInteractionTouchable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionTouchable) que seja o [`NearInteractionGrabbable`](xref:Microsoft.MixedReality.Toolkit.Input.NearInteractionGrabbable) script.

<img src="../images/pointers/MRTK_GrabPointer.jpg" width="400" alt="Grab Pointer">

Propriedades de ponteiro de esfera útil:

- *Raio de Cast sphere:* o raio para a esfera usada para consultar objetos que podem ser buscados.
- *Margem de objeto* próximo: a distância na parte superior do Raio de Cast da Esfera a ser consultada para detectar se um objeto está próximo do ponteiro. O raio total de detecção de Objeto Próximo é Raio de Cast de Esfera + Margem de Objeto Próximo
- *Ângulo do setor de objeto* próximo: o ângulo em torno do eixo de avanço do ponteiro para consultar objetos próximos. Torna a `IsNearObject` função de consulta como um cone. Isso é definido como 66 graus por padrão para corresponder ao comportamento do Hololens 2

![Ponteiro de esfera modificado para consultar apenas objetos na direção da frente](https://user-images.githubusercontent.com/39840334/82500569-72d58300-9aa8-11ea-8102-ec9a62832d4e.png)

- *Fator de suavização de objeto próximo:* fator de suavização para detecção de objeto próximo. Se um objeto for detectado no Raio de Objeto Próximo, o raio consultado se tornará Raio de Objeto Próximo * (1 + Fator de Suavização de Objeto Próximo) para reduzir a sensibilidade e dificultar a saída do intervalo de detecção por um objeto.
- *Pegar máscaras de camada* – uma matriz priorizada de LayerMasks para determinar com quais gameObjects o ponteiro pode interagir e a ordem de interação para tentar. Observe que um GameObject também deve ter um `NearInteractionGrabbable` para interagir com um SpherePointer.
    > [!NOTE]
    > A camada de Reconhecimento Espacial está desabilitada no pré-fab grabPointer padrão fornecido pelo MRTK. Isso é feito para reduzir o impacto no desempenho de fazer uma consulta de sobreposição de esfera com a malha espacial. Você pode habilitar isso modificando o pré-fab GrabPointer.
- *Ignorar colisores não em FOV* – se deve ignorar colisores que podem estar próximos ao ponteiro, mas não realmente no FOV visual.
Isso pode impedir capturas acidentais e permitirá que raios de mão sejam ativas quando você pode estar perto de um grabbable, mas não pode vê-lo. O *Visual FOV é* definido por meio de um cone em vez do típico por motivos de desempenho. Esse cone é centralizado e orientado da mesma forma que o frustum da câmera com um raio igual a meia altura de exibição (ou FOV vertical).

<img src="../images/input/pointers/SpherePointer_VisualFOV.png" width="200" alt="Sphere Pointer">

#### <a name="teleport-pointers"></a>Ponteiros de teletransporte

- [`TeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.TeleportPointer) vai auportar uma solicitação de teletransporte quando a ação for tomada (ou seja, o botão de teletransporte é pressionado) para mover o usuário.
- [`ParabolicTeleportPointer`](xref:Microsoft.MixedReality.Toolkit.Teleport.ParabolicTeleportPointer) vai auportar uma solicitação de teletransporte quando a ação for tomada (ou seja, o botão de teletransporte é pressionado) com um raycast de linha parabólica para mover o usuário.

<img src="../images/pointers/MRTK_Pointers_Parabolic.png" width="400" alt="Pointer Parabolic">

## <a name="pointer-support-for-mixed-reality-platforms"></a>Suporte de ponteiro para plataformas de realidade misturada

A tabela a seguir detalha os tipos de ponteiro que normalmente são usados para as plataformas comuns no MRTK. OBSERVAÇÃO: é possível adicionar diferentes tipos de ponteiro a essas plataformas. Por exemplo, você pode adicionar um ponteiro Decodar ou um ponteiro Sphere à VR. Além disso, dispositivos VR com um gamepad podem usar o ponteiro GGV.

|       Ponteiro              | OpenVR  | Windows Mixed Reality | HoloLens 1 | HoloLens 2 |
|---------------------|---------|-----------------------|------------|------------|
| ShellHandRayPointer | Válido   | Válido                 |            | Válido      |
| Transpointer     | Válido   | Válido                 |            |            |
| GGVPointer          |         |                       | Válido      |            |
| SpherePointer       |         |                       |            | Válido      |
| Pointer         |         |                       |            | Válido      |

## <a name="pointer-interactions-via-code"></a>Interações de ponteiro por meio de código

### <a name="pointer-event-interfaces"></a>Interfaces de evento de ponteiro

MonoBehaviours que implementam uma ou mais das interfaces a seguir e são atribuídos a um GameObject com um receberão eventos de interações de ponteiro conforme definido pela `Collider` interface associada.

| Evento | Descrição | Manipulador |
| --- | --- | --- |
| Antes de o foco ser alterado/foco alterado | Gerado no objeto de jogo que perde o foco e aquele que o ganha sempre que um ponteiro altera o foco. | [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) |
Focus Enter/Exit | Gerado no objeto de jogo que está se concentrando quando o primeiro ponteiro entra nele e no que perde o foco quando o último ponteiro o deixa. | [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler)
Ponteiro para baixo/arrastado/para cima/clicado | Gerado para pressionar, arrastar e soltar do ponteiro de relatório. | [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler)
Toque iniciado/atualizado/concluído | Gerados por ponteiros sensíveis ao toque, como [`PokePointer`](xref:Microsoft.MixedReality.Toolkit.Input.PokePointer) relatar atividade de toque. | [`IMixedRealityTouchHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityTouchHandler)

> [!NOTE]
> [`IMixedRealityFocusChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusChangedHandler) e [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityFocusHandler) devem ser tratados nos objetos em que são gerados. É possível receber eventos de foco globalmente, mas, ao contrário de outros eventos de entrada, o manipulador de eventos global não bloqueará o recebimento de eventos com base no foco (o evento será recebido pelo manipulador global e um objeto correspondente em foco).

#### <a name="pointer-input-events-in-action"></a>Eventos de entrada de ponteiro em ação

Eventos de entrada de ponteiro são reconhecidos e manipulados pelo sistema de entrada do MRTK de maneira semelhante aos [eventos de entrada regulares](input-events.md#input-events-in-action). A diferença é que os eventos de entrada de ponteiro são manipulados apenas pelo GameObject em foco pelo ponteiro que disparou o evento de entrada, bem como quaisquer manipuladores de entrada globais. Eventos de entrada regulares são tratados por GameObjects em foco para todos os ponteiros ativos.

1. O sistema de entrada do MRTK reconhece que ocorreu um evento de entrada
1. O sistema de entrada do MRTK dispara a função de interface relevante para o evento de entrada para todos os manipuladores de entrada globais registrados
1. O sistema de entrada determina qual GameObject está em foco para o ponteiro que disparou o evento
    1. O sistema de entrada utiliza o Sistema de Eventos do [Unity](https://docs.unity3d.com/Manual/EventSystem.html) para disparar a função de interface relevante para todos os componentes correspondentes no GameObject focado
    1. Se a qualquer momento um evento de entrada tiver sido marcado como [usado,](input-events.md#how-to-stop-input-events)o processo será final e nenhum GameObjects mais receberá retornos de chamada.
        - Exemplo: os componentes que implementam a interface serão pesquisados em busca [`IMixedRealityFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealitySpeechHandler) de ganhos gameObject ou perderão o foco
        - Observação: o Sistema de Eventos do Unity será bolha para pesquisar o GameObject pai se nenhum componente que corresponde à interface desejada for encontrado no GameObject atual.
1. Se nenhum manipulador de entrada global for registrado e nenhum GameObject for encontrado com um componente/interface correspondente, o sistema de entrada chamará cada manipulador de entrada registrado de fallback

#### <a name="example"></a>Exemplo

Abaixo está um script de exemplo que altera a cor do renderador anexado quando um ponteiro recebe ou sai do foco ou quando um ponteiro seleciona o objeto.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    private Color color_IdleState = Color.cyan;
    private Color color_OnHover = Color.white;
    private Color color_OnSelect = Color.blue;
    private Material material;

    private void Awake()
    {
        material = GetComponent<Renderer>().material;
    }

    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }

    void IMixedRealityPointerHandler.OnPointerDown(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerDragged(
         MixedRealityPointerEventData eventData) { }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
    {
        material.color = color_OnSelect;
    }
}
```

### <a name="query-pointers"></a>Ponteiros de consulta

É possível reunir todos os ponteiros atualmente ativos por meio de loop por meio das fontes de entrada disponíveis (ou seja, controladores e entradas disponíveis) para descobrir quais ponteiros estão anexados a eles.

```c#
var pointers = new HashSet<IMixedRealityPointer>();

// Find all valid pointers
foreach (var inputSource in CoreServices.InputSystem.DetectedInputSources)
{
    foreach (var pointer in inputSource.Pointers)
    {
        if (pointer.IsInteractionEnabled && !pointers.Contains(pointer))
        {
            pointers.Add(pointer);
        }
    }
}
```

#### <a name="primary-pointer"></a>Ponteiro principal

Os desenvolvedores podem assinar o evento PrimaryPointerChanged do FocusProviders para serem notificados quando o ponteiro primário em foco for alterado. Isso pode ser extremamente útil para identificar se o usuário está interagindo com uma cena por meio de um olhar, um raio de mão ou outra fonte de entrada.

```c#
private void OnEnable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.SubscribeToPrimaryPointerChanged(OnPrimaryPointerChanged, true);
}

private void OnPrimaryPointerChanged(IMixedRealityPointer oldPointer, IMixedRealityPointer newPointer)
{
    ...
}

private void OnDisable()
{
    var focusProvider = CoreServices.InputSystem?.FocusProvider;
    focusProvider?.UnsubscribeFromPrimaryPointerChanged(OnPrimaryPointerChanged);

    // This flushes out the current primary pointer
    OnPrimaryPointerChanged(null, null);
}
```

A `PrimaryPointerExample` cena (Assets/MRTK/Examples/Demos/Input/Scenes/PrimaryPointer) mostra como usar o para eventos [`PrimaryPointerChangedHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PrimaryPointerChangedHandler) responderem a um novo ponteiro primário.

<img src="../images/pointers/PrimaryPointerExample.png" style="max-width:100%;" alt="Primary Pointer Example">

### <a name="pointer-result"></a>Resultado do ponteiro

A propriedade [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) de ponteiro contém o resultado atual da consulta de cena usada para determinar o objeto com foco. Para um ponteiro raycast, como aqueles criados por padrão para controladores de movimento, entrada de olhar e raios de mão, ele conterá o local e o normal do ataque de raycast.

```c#
private void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData)
{
    var result = eventData.Pointer.Result;
    var spawnPosition = result.Details.Point;
    var spawnRotation = Quaternion.LookRotation(result.Details.Normal);
    Instantiate(MyPrefab, spawnPosition, spawnRotation);
}
```

A cena `PointerResultExample` (Assets/MRTK/Examples/Demos/Input/Scenes/PointerResult/PointerResultExample.unity) mostra como usar o ponteiro para gerar um objeto no local de [`Result`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointer.Result) ocorrência.

<img src="../images/input/PointerResultExample.png" style="max-width:100%;" alt="Pointer Result">

### <a name="disable-pointers"></a>Desabilitar ponteiros

Para habilitar e desabilitar ponteiros (por exemplo, para desabilitar o raio de mão), de definir o [`PointerBehavior`](xref:Microsoft.MixedReality.Toolkit.Input.PointerBehavior) para um determinado tipo de ponteiro via [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) .

```c#
// Disable the hand rays
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff);

// Disable hand rays for the right hand only
PointerUtils.SetHandRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Right);

// Disable the gaze pointer
PointerUtils.SetGazePointerBehavior(PointerBehavior.AlwaysOff);

// Set the behavior to match HoloLens 1
// Note, if on HoloLens 2, you must configure your pointer profile to make the GGV pointer show up for articulated hands.
public void SetHoloLens1()
{
    PointerUtils.SetPokePointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGrabPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetRayPointerBehavior(PointerBehavior.AlwaysOff, Handedness.Any);
    PointerUtils.SetGGVBehavior(PointerBehavior.Default);
}
```

Consulte [`PointerUtils`](xref:Microsoft.MixedReality.Toolkit.Input.PointerUtils) e para obter mais [`TurnPointersOnOff`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.DisablePointersExample) exemplos.

## <a name="pointer-interactions-via-editor"></a>Interações de ponteiro por meio do editor

Para eventos de ponteiro manipulados pelo , o MRTK fornece mais conveniência na forma do componente , que permite que os eventos de ponteiro sejam tratados diretamente por meio de [`IMixedRealityPointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityPointerHandler) [`PointerHandler`](xref:Microsoft.MixedReality.Toolkit.Input.PointerHandler) Eventos do Unity.

<img src="../images/pointers/PointerHandler.png" style="max-width:100%;" alt="Pointer Handler">

## <a name="pointer-extent"></a>Extensão do ponteiro

Ponteiros distantes têm configurações que limitam até que ponto eles serão raycast e interagirão com outros objetos na cena.
Por padrão, esse valor é definido como 10 metros. Esse valor foi escolhido para permanecer consistente com o comportamento do HoloLens shell.

Isso pode ser alterado atualizando os campos do componente do `DefaultControllerPointer` [`ShellHandRayPointer`](xref:Microsoft.MixedReality.Toolkit.Input.ShellHandRayPointer) pré-fab:

*Extensão do* Ponteiro – controla a distância máxima com a que os ponteiros interagirão.

*Extensão de Ponteiro* Padrão – controla o comprimento do raio/linha do ponteiro que será renderizar quando o ponteiro não estiver interagindo com nada.

## <a name="see-also"></a>Confira também

- [Arquitetura de ponteiro](../../architecture/controllers-pointers-and-focus.md)
- [Eventos de entrada](input-events.md)
