---
title: Seleção de destino de acompanhamento de olho
description: Como acessar dados olhars de olho e olho olhar eventos específicos para selecionar destinos no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, EyeTracking,
ms.openlocfilehash: 229903e01c597aefbb3fc29de8a49d79cbbd42d0
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144189"
---
# <a name="eye-supported-target-selection"></a>Seleção de destino com suporte de olho

![MRTK](../../images/eye-tracking/mrtk_et_targetselect.png)

Esta página discute diferentes opções para acessar dados olhars de olho e olho olhar eventos específicos para selecionar destinos em MRTK. O acompanhamento de olho permite seleções de destino rápidas e sem esforço usando uma combinação de informações sobre o que um usuário está vendo com entradas adicionais, como o _rastreamento manual_ e os _comandos de voz_:

- Procure & diga _"Select"_ (comando de voz padrão)
- Procure & diga _"explodir"_ ou _"pop"_ (comandos de voz personalizados)
- Procurar & botão Bluetooth
- Olhe & pinça (ou seja, mantenha sua mão na frente e traga seu polegar e um índice para o dedo)
  - Observe que, para que isso funcione, os [raios à mão precisam ser desabilitados](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray)

Para selecionar o conteúdo do Holographic usando olho olhar, há várias opções:

[**1. Use o ponteiro de foco principal:**](#1-use-generic-focus-and-pointer-handlers)

Isso pode ser compreendido como o cursor de prioridade.
Por padrão, se as mãos estiverem no modo de exibição, isso seria raios de mão.
Se nenhuma mão estiver na exibição, o ponteiro priorizado será de cabeça ou olho olhar.
Portanto, observe que, com base no cabeçalho de design atual ou no olhar de olho, é suprimido como uma entrada de cursor se os raios à mão forem usados.

Por exemplo:

Um usuário deseja selecionar um botão de Holographic distante.
Como desenvolvedor, você deseja fornecer uma solução flexível que permita ao usuário obter essas tarefas em várias condições:

- Ir para o botão e examiná-lo
- Examine-o de uma distância e diga "Select"
- Direcione o botão usando um raio de mão e realizando um pinça nesse caso, a solução mais flexível é usar o manipulador de foco principal, pois ele o notificará sempre que o ponteiro de foco principal priorizado atualmente disparar um evento. Observe que, se os raios à mão estiverem habilitados, o ponteiro de foco olhar de cabeça ou olho será desabilitado assim que as mãos entrarem em vista.

> [!IMPORTANT]
> Observe que, se os raios à mão estiverem habilitados, o ponteiro de foco olhar de cabeça ou olho será desabilitado assim que as mãos entrarem em vista. Se você quiser dar suporte a uma interação de [ _' aparência e pinçar '_ , será necessário desabilitar a disposição de raio](eye-tracking-eyes-and-hands.md#how-to-disable-the-hand-ray). Em nossos bastidores de exemplo de acompanhamento de olho, desabilitamos o conjunto de posicionamento à mão para permitir interações mais ricas usando movimentos de olhos e outros-consulte para obter exemplos com [suporte](eye-tracking-eyes-and-hands.md).

[**2. Use o foco ocular e os raios à mão ao mesmo tempo:**](#2-independent-eye-gaze-specific-eyetrackingtarget)

Pode haver instâncias em que você deseja ser mais específico que o tipo de ponteiros de foco possa disparar determinados eventos e permitir simultaneamente usando várias técnicas de interação distantes.

Por exemplo: em seu aplicativo, um usuário pode usar raios de longe para manipular alguma configuração mecânica Holographic-por exemplo, pegar e manter algumas partes de mecanismo de Holographic distantes e mantê-las em vigor. Ao fazer isso, o usuário precisa passar por várias instruções e registrar seu andamento marcando algumas caixas de seleção. Se o usuário tiver suas mãos _não ocupadas_, seria instinctual simplesmente tocar na caixa de seleção ou selecioná-la usando um raio de mão. No entanto, se o usuário tiver suas mãos, como em nosso caso, mantendo algumas partes do mecanismo Holographic em vigor, você deseja permitir que o usuário percorra diretamente as instruções usando suas olhar de olho e simplesmente examine uma caixa de seleção e diga "check-in!".

Para habilitar isso, você precisa usar um script EyeTrackingTarget específico para os olhos que é independente do MRTK de FocusHandlers principal e será discutido mais adiante.

## <a name="1-use-generic-focus-and-pointer-handlers"></a>1. usar manipuladores de foco e ponteiro genérico

Se o acompanhamento ocular estiver configurado corretamente (consulte Configuração básica do [MRTK](eye-tracking-basic-setup.md)para usar o acompanhamento ocular), permitir que os usuários selecionem hologramas usando os olhos será o mesmo que qualquer outra entrada de foco (por exemplo, foco com a cabeça ou raio de mão). Isso oferece a grande vantagem de uma maneira flexível de interagir com seus hologramas definindo o tipo de foco principal em seu Perfil de Ponteiro de Entrada do MRTK, dependendo das necessidades do usuário, deixando seu código inalterado. Isso permite alternar entre o olhar ou a cabeça sem alterar uma linha de código ou substituir raios de mão por direcionamento ocular para interações distantes.

### <a name="focusing-on-a-hologram"></a>Concentrando-se em um holograma

Para detectar quando um holograma está focalizado, use a interface _'IMixedRealityFocusHandler'_ que fornece dois membros de interface: _OnFocusEnter_ e _OnFocusExit_.

Aqui está um exemplo simples de [ColorTap.cs](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ColorTap) para alterar a cor de um holograma ao ser procurado.

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler
{
    void IMixedRealityFocusHandler.OnFocusEnter(FocusEventData eventData)
    {
        material.color = color_OnHover;
    }

    void IMixedRealityFocusHandler.OnFocusExit(FocusEventData eventData)
    {
        material.color = color_IdleState;
    }
    ...
}
```

### <a name="selecting-a-focused-hologram"></a>Selecionando um holograma focalizado

Para selecionar um holograma focalizado, use _PointerHandler_ para escutar eventos de entrada para confirmar uma seleção.
Por exemplo, adicionar _o IMixedRealityPointerHandler_ fará com que eles reajam à entrada de ponteiro simples.
A interface _IMixedRealityPointerHandler_ requer a implementação dos três membros de interface a seguir: _OnPointerUp,_ _OnPointerDown_ e _OnPointerClicked_.

No exemplo a seguir, alteramos a cor de um holograma observando-o e pinçando ou dizendo "selecionar".
A ação necessária para disparar o evento é definida pelo qual podemos definir o tipo de no Editor do Unity – por padrão, é a `eventData.MixedRealityInputAction == selectAction` `selectAction` ação "Selecionar". Os tipos de [MixedRealityInputActions](../input-actions.md) disponíveis podem ser configurados no Perfil do MRTK por meio das Ações de Entrada de Entrada do Perfil de Configuração do _MRTK._  ->    ->  

```c#
public class ColorTap : MonoBehaviour, IMixedRealityFocusHandler, IMixedRealityPointerHandler
{
    // Allow for editing the type of select action in the Unity Editor.
    [SerializeField]
    private MixedRealityInputAction selectAction = MixedRealityInputAction.None;
    ...

    void IMixedRealityPointerHandler.OnPointerUp(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnHover;
        }
    }

    void IMixedRealityPointerHandler.OnPointerDown(MixedRealityPointerEventData eventData)
    {
        if (eventData.MixedRealityInputAction == selectAction)
        {
            material.color = color_OnSelect;
        }
    }

    void IMixedRealityPointerHandler.OnPointerClicked(MixedRealityPointerEventData eventData) { }
}
```

### <a name="eye-gaze-specific-baseeyefocushandler"></a>BaseEyeFocusHandler específica do foco com o olhar

Considerando que o foco com o olhar pode ser muito diferente de outras entradas de  ponteiro, talvez você queira garantir que reaja apenas à entrada de foco se ele for foco com o olhar e ele for atualmente o ponteiro de entrada primário.
Para essa finalidade, você usaria o [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) que é específico para acompanhamento de olho e que deriva do [`BaseFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseFocusHandler) .
Como mencionado anteriormente, ele só será disparado se o foco olhar direcionamento for a entrada do ponteiro principal (ou seja, não há um raio de disposição ativo). Para obter mais informações, consulte [como dar suporte a gestos de olho olhar + Hand](eye-tracking-eyes-and-hands.md).

Aqui está um exemplo de `EyeTrackingDemo-03-Navigation` (ativos/MRTK/exemplos/demos/EyeTracking/cenas).
Nesta demonstração, há dois hologramas 3D que serão ativados dependendo de qual parte do objeto é examinada: se o usuário olhar para o lado esquerdo do holograma, essa parte se moverá lentamente para a frente do usuário.
Se o lado direito for examinado, essa parte será movida lentamente para a frente.
Esse é um comportamento que você talvez não queira que seja sempre ativo e também algo que talvez você não queira disparar acidentalmente por um olhar de raio ou cabeça.
Tendo o [`OnLookAtRotateByEyeGaze`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.OnLookAtRotateByEyeGaze) anexo, um gameobject será girado enquanto estiver sendo examinado.

```c#
public class OnLookAtRotateByEyeGaze : BaseEyeFocusHandler
{
    ...

    protected override void OnEyeFocusStay()
    {
        // Update target rotation
        RotateHitTarget();
    }

    ...

    ///
    /// This function computes the rotation of the target to move the currently
    /// looked at aspect slowly to the front.
    ///
    private void RotateHitTarget()
    {
        // Example for querying the hit position of the eye gaze ray using EyeGazeProvider
        Vector3 TargetToHit = (this.gameObject.transform.position - InputSystem.EyeGazeProvider.HitPosition).normalized;

        ...
    }
}
```

Consulte a documentação da API para obter uma lista completa dos eventos disponíveis do [`BaseEyeFocusHandler`](xref:Microsoft.MixedReality.Toolkit.Input.BaseEyeFocusHandler) :

- **OnEyeFocusStart:** Disparado quando o olho olhar Ray *começa* a se Interseccionar com o colisor de destino.
- **OnEyeFocusStay:** Disparado *enquanto* o olho olhar Ray está interseccionando com o colisor de destino.
- **OnEyeFocusStop:** Disparado quando o olho olhar Ray *pára* de interseção com o colisor de destino.
- **OnEyeFocusDwell:** Disparado quando o olho olhar Ray se cruzou com o colisor de destino por um período de tempo especificado.

## <a name="2-independent-eye-gaze-specific-eyetrackingtarget"></a>2. olho independente – EyeTrackingTarget específico do olhar

Por fim, fornecemos uma solução que permite que você trate a entrada baseada em olho completamente independente de outros ponteiros de foco por meio do [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script.

Isso tem três _vantagens_:

- Você pode se certificar de que o holograma está apenas se reagindo ao olhar de olhos do usuário.
- Isso é independente da entrada primária ativa no momento. Portanto, você pode processar várias entradas de uma só vez– por exemplo, combinando direcionamento de olho rápido com gestos de mão.
- Vários eventos do Unity já foram definidos para torná-lo rápido e conveniente para lidar e reutilizar comportamentos existentes de dentro do Editor do Unity ou por meio de código.

Também há algumas _desvantagens:_

- Mais esforço para lidar com entradas separadas individualmente.
- Nenhuma degradação elegante: ele dá suporte apenas ao direcionamento ocular. Se o acompanhamento ocular não estiver funcionando, você exigirá algum fallback adicional.

Semelhante ao _BaseFocusHandler_, o _EyeTrackingTarget_ vem pronto com vários eventos específicos do Unity que você pode escutar convenientemente por meio do Editor do Unity (veja o exemplo abaixo) ou usando _AddListener()_ no código:

- OnLookAtStart()
- WhileLookingAtTarget()
- OnLookAway()
- OnDwell()
- OnSelected()

A seguir, explicamos alguns exemplos de como usar _EyeTrackingTarget._

### <a name="example-1-eye-supported-smart-notifications"></a>Exemplo #1: notificações inteligentes com suporte ocular

Em `EyeTrackingDemo-02-TargetSelection` (Ativos/MRTK/Exemplos/Demonstrações/EyeTracking/Scenes), você pode encontrar um exemplo de _'notificações_ inteligentes de notificação de notificação' que reagem ao seu olhar.
Essas são caixas de texto 3D que podem ser colocadas na cena e que aumentarão suavemente e se voltarão para o usuário ao serem olhadas para facilitar a legibilidade. Enquanto o usuário estiver lendo a notificação, as informações continuarão sendo exibidas claras e claras. Depois de lê-la e olhar para fora da notificação, a notificação será automaticamente descartada e esmaeça. Para fazer tudo isso, há alguns scripts de comportamento genéricos que não são específicos do acompanhamento ocular, como:

- [`FaceUser`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.FaceUser)
- [`ChangeSize`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.ChangeSize)
- [`BlendOut`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.BlendOut)

A vantagem dessa abordagem é que os mesmos scripts podem ser reutilizado por vários eventos. Por exemplo, um holograma pode começar a ser voltado para o usuário com base em comandos de voz ou depois de pressionar um botão virtual. Para disparar esses eventos, você pode simplesmente referenciar os métodos que devem ser executados no [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script que está anexado ao gameobject.

Para o exemplo de _' notificações do Smart cuidadosa '_, acontece o seguinte:

- **OnLookAtStart ()**: a notificação começa...
  - *FaceUser. envolver:* ... Mude para o usuário.
  - *Alterações. envolver:* ... aumento de tamanho _(até uma escala máxima especificada)_.
  - *Blendout. entrave:* ... começa a misturar em mais _(depois de estar em um estado ocioso mais sutil)_.  

- **()**: Informa ao script _blendout_ que a notificação foi examinada de forma suficiente.

- **OnLookAway ()**: a notificação começa...
  - *FaceUser. Solte:* ... retorne à sua orientação original.
  - *ChangeSize. Solte:* ... diminuir de volta para seu tamanho original.
  - *Blendout. Solte:* ... começa a Mesclar-se o _()_ foi disparado, mesclar completamente e destruir, de outra forma, de volta ao estado ocioso.

**Consideração de design:** A chave para uma experiência agradável aqui é ajustar cuidadosamente a velocidade de qualquer um desses comportamentos para evitar a causa de discomfort, reagindo ao olho do usuário olhar muito rápido o tempo todo.
Caso contrário, isso pode rapidamente ser extremamente impressionante.

<img src="../../images/eye-tracking/mrtk_et_EyeTrackingTarget_Notification.jpg" width="750" alt="Target Notification">

### <a name="example-2-holographic-gem-rotates-slowly-when-looking-at-it"></a>Exemplo #2: o gem Holographic gira lentamente ao olhar para ele

Semelhante ao exemplo #1, podemos criar facilmente um comentário em foco para nossos Holographic Gems na `EyeTrackingDemo-02-TargetSelection` cena (ativos/MRTK/exemplos/demos/EyeTracking/cenas) que irão girar lentamente em uma direção constante e em uma velocidade constante (em oposição ao exemplo de rotação acima) quando examinado. Tudo o que você precisa é disparar a rotação do GEM Holographic do evento _WhileLookingAtTarget ()_ do _EyeTrackingTarget_. Aqui estão alguns detalhes:

1. Crie um script genérico que inclua uma função pública para girar o gameobject ao qual ele está anexado. Veja abaixo um exemplo de _RotateWithConstSpeedDir. cs_ , onde podemos ajustar a direção e a velocidade da rotação do editor do Unity.

    ```c#
    using UnityEngine;

    namespace Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking
    {
        /// <summary>
        /// The associated GameObject will rotate when RotateTarget() is called based on a given direction and speed.
        /// </summary>
        public class RotateWithConstSpeedDir : MonoBehaviour
        {
            [Tooltip("Euler angles by which the object should be rotated by.")]
            [SerializeField]
            private Vector3 RotateByEulerAngles = Vector3.zero;

            [Tooltip("Rotation speed factor.")]
            [SerializeField]
            private float speed = 1f;

            /// <summary>
            /// Rotate game object based on specified rotation speed and Euler angles.
            /// </summary>
            public void RotateTarget()
            {
                transform.eulerAngles = transform.eulerAngles + RotateByEulerAngles * speed;
            }
        }
    }
    ```

1. Adicione o [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script ao gameobject de destino e faça referência à função _RotateTarget ()_ no gatilho UnityEvent, conforme mostrado na captura de tela abaixo:

    ![Exemplo de EyeTrackingTarget](../../images/eye-tracking/mrtk_et_EyeTrackingTargetSample.jpg)

### <a name="example-3-pop-those-gems-aka-_multi-modal-eye-gaze-supported-target-selection_"></a>Exemplo #3: pop essas Gems que _têm o olho multimodal-olhar-seleção de destino com suporte_

No exemplo anterior, mostramos como é fácil detectar se um destino é examinado e como disparar uma reação a isso. Em seguida, vamos fazer o detalhamento das Gems usando o evento _OnSelected ()_ do [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) . A parte interessante é *como* a seleção é disparada. O [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) permite atribuir rapidamente maneiras diferentes de invocar uma seleção:

- _Gesto de pinçar_: a configuração de ' Selecionar ação ' como ' selecionar ' usa o gesto de mão padrão para disparar a seleção.
Isso significa que o usuário pode simplesmente aumentar sua mão e pinçar seu polegar e indexar o dedo para confirmar a seleção.

- Diga _"Select"_: Use o comando de voz padrão _"Select"_ para selecionar um holograma.

- Diga _"explosão"_ ou _"pop"_: para usar comandos de voz personalizados, você precisa seguir duas etapas:
    1. Configurar uma ação personalizada, como _"DestroyTarget"_
        - Navegue até _MRTK-> entrada-> ações de entrada_
        - Clique em "adicionar uma nova ação"

    2. Configurar os comandos de voz que disparam essa ação, como _"explodir"_ ou _"pop"_
        - Navegue até _MRTK-> de entrada-> fala_
        - Clique em "adicionar um novo comando de fala"
            - Associar a ação que você acabou de criar
            - Atribuir um _código_ de Key-prima para permitir o acionamento da ação por meio de um pressionamento de botão

![Exemplo de Comandos de voz EyeTrackingTarget](../../images/eye-tracking/mrtk_et_voicecmdsample.jpg)

Quando uma gema é selecionada, ela vai estourar, fazendo um som e desaparecendo. Isso é tratado pelo [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script. Você tem duas opções:

- **No Editor do Unity:** Você pode simplesmente vincular o script anexado a cada um dos nossos modelos gem ao evento OnSelected() Unity no Editor do Unity.
- **No código:** Se você não quiser arrastar e soltar GameObjects, também poderá simplesmente adicionar um ouvinte de eventos diretamente ao script.  
Veja um exemplo de como fizemos isso no [`HitBehaviorDestroyOnSelect`](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.HitBehaviorDestroyOnSelect) script:

```c#
/// <summary>
/// Destroys the game object when selected and optionally plays a sound or animation when destroyed.
/// </summary>
[RequireComponent(typeof(EyeTrackingTarget))] // This helps to ensure that the EyeTrackingTarget is attached
public class HitBehaviorDestroyOnSelect : MonoBehaviour
{
    ...
    private EyeTrackingTarget myEyeTrackingTarget = null;

    private void Start()
    {
        myEyeTrackingTarget = this.GetComponent<EyeTrackingTarget>();

        if (myEyeTrackingTarget != null)
        {
            myEyeTrackingTarget.OnSelected.AddListener(TargetSelected);
        }
    }

    ...

    ///
    /// This is called once the EyeTrackingTarget detected a selection.
    ///
    public void TargetSelected()
    {
        // Play some animation
        // Play some audio effect
        // Handle destroying the target appropriately
    }
}
```

### <a name="example-4-use-hand-rays-and-eye-gaze-input-together"></a>Exemplo #4: usar raios de mão e entrada de olhar juntos

Os raios de mão têm prioridade sobre o direcionamento do olhar e da cabeça. Isso significa que, se os raios de mão estão habilitados, no momento em que as mãos são vistas, o raio de mão atuará como o ponteiro primário.
No entanto, pode haver situações em que você deseja usar raios de mão enquanto ainda detecta se um usuário está olhando para um determinado holograma. Muito fácil. Essencialmente, você precisa de duas etapas:

**1. Habilitar o** raio de mão: para habilitar o raio de mão, acesse Kit de Ferramentas de Realidade Misturada _-> Entrada -> Ponteiros_.
No _EyeTrackingDemo-00-RootScene_ em que o Kit de Ferramentas de Realidade Misturada é configurado uma vez para todas as cenas de demonstração de acompanhamento ocular, você deve ver _o EyeTrackingDemoPointerProfile_.
Você pode criar um novo Perfil _de Entrada do_ zero ou adaptar o acompanhamento ocular atual:

- **Do zero:** Na guia _Ponteiros,_ selecione _DefaultMixedRealityInputPointerProfile_ no menu de contexto.
Esse é o perfil de ponteiro padrão que já tem o raio de mão habilitado!
Para alterar o cursor padrão (um ponto branco opaco), basta clonar o perfil e criar seu próprio perfil de ponteiro personalizado.
Em seguida, _substitua DefaultCursor_ por _EyeGazeCursor em_ _Prefab do Cursor de_ Olhar.  
- **Com base no _EyeTrackingDemoPointerProfile_ existente:** clique duas vezes no _EyeTrackingDemoPointerProfile_ e adicione a seguinte entrada em Opções _de Ponteiro:_
  - **Tipo de controlador:** "Mão articulada", "realidade misturada do Windows"
  - **Destromente:** Outro
  - **Pré-fabricado do ponteiro:** DefaultControllerPointer

**2. detecte que um holograma é examinado:** use o [`EyeTrackingTarget`](xref:Microsoft.MixedReality.Toolkit.Input.EyeTrackingTarget) script para habilitar a detecção de um holograma examinado conforme descrito acima. Você também pode dar uma olhada no `FollowEyeGaze` script de exemplo para inspiração, pois isso mostra um holograma seguindo o olhar de olho (por exemplo, um cursor) se os raios à mão estão habilitados ou não.

Agora, ao iniciar os bastidores de demonstração de controle de olho, você verá um raio vindo de suas mãos.
Por exemplo, na demonstração de seleção de destino de acompanhamento de olho, o círculo semitransparente ainda está seguindo seus olhos olhar e as Gems respondem se eles são examinados ou não, enquanto os botões de menu de cena superior usam o ponteiro de entrada primário (suas mãos) em vez disso.

---
[Voltar para "acompanhamento de olho no MixedRealityToolkit"](eye-tracking-main.md)
