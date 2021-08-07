---
title: Controladores de movimento no Unity
description: Saiba como agir em seu olhar no Unity com a entrada do controlador de movimento usando a XR e as APIs de botão e de eixo comuns.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: controladores de movimento, Unity, entrada, a realidade misturada Headset, headset de realidade mista do Windows, headset da realidade virtual, MRTK, realidade misturada Toolkit
ms.openlocfilehash: ccda5b11190e829ccc655989a6f679ef6ef647a920c01a3182548b23a3d85084
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115216232"
---
# <a name="motion-controllers-in-unity"></a>Controladores de movimento no Unity

há duas maneiras principais de agir em seu [olhar no Unity](gaze-in-unity.md), [gestos de mão](../../design/gaze-and-commit.md#composite-gestures) e [controladores de movimento](../../design/motion-controllers.md) em HoloLens e HMD de imersão. Você acessa os dados de ambas as fontes de entrada espacial por meio das mesmas APIs no Unity.

O Unity fornece duas maneiras principais de acessar dados de entrada espaciais para Windows Mixed Reality. as APIs comuns *input. getbutton/input. getaxis* funcionam em vários SDKs do Unity XR, enquanto a API *interactionmanager/GestureRecognizer* específica para Windows Mixed Reality expõe o conjunto completo de dados de entrada espaciais.

## <a name="unity-xr-input-apis"></a>APIs de entrada do Unity XR

Para novos projetos, é recomendável usar as novas APIs de entrada XR desde o início. 

Você pode encontrar mais informações sobre as [APIs XR aqui](https://docs.unity3d.com/Manual/xr_input.html).

## <a name="unity-buttonaxis-mapping-table"></a>Tabela de mapeamento de botões/eixos do Unity

o gerenciador de entrada do Unity para controladores de Windows Mixed Reality motion dá suporte às IDs de botão e eixo listadas abaixo por meio das APIs *Input. getbutton/getaxis* . a coluna "Windows MR-specific" refere-se às propriedades disponíveis do tipo *InteractionSourceState* . Cada uma dessas APIs é descrita detalhadamente nas seções a seguir.

os mapeamentos de ID de botão/eixo para Windows Mixed Reality geralmente correspondem às IDs de eixo/botão Oculus.

os mapeamentos de ID de botão/eixo para Windows Mixed Reality diferem dos mapeamentos de OpenVR de duas maneiras:
1. O mapeamento usa IDs de touchpad que são diferentes de Thumbstick para dar suporte a controladores com Thumbsticks e touchpads.
2. O mapeamento evita sobrecarregar as IDs de botão a e X para os botões de menu para deixá-los disponíveis para os botões físicos de ABXY.

<table>
<tr>
<th rowspan="2">Entrada </th><th colspan="2"><a href="motion-controllers-in-unity.md#common-unity-apis-inputgetbuttongetaxis">APIs comuns do Unity</a><br />(Input. getbutton/getaxis) </th><th rowspan="2"><a href="motion-controllers-in-unity.md#windows-specific-apis-xrwsainput">Windows API de entrada específica do MR</a><br />XR. WSA. Entrada</th>
</tr><tr>
<th> À esquerda </th><th> À direita</th>
</tr><tr>
<td> Selecionar gatilho pressionado </td><td> Eixo 9 = 1,0 </td><td> Eixo 10 = 1,0 </td><td> selectPressed</td>
</tr><tr>
<td> Selecionar valor analógico do gatilho </td><td> Eixo 9 </td><td> Eixo 10 </td><td> selectPressedAmount</td>
</tr><tr>
<td> Selecionar gatilho parcialmente pressionado </td><td> Botão 14 <i>(compatível com gamepad)</i> </td><td> Botão 15 <i>(compatível com gamepad)</i> </td><td> selectPressedAmount &gt; 0,0</td>
</tr><tr>
<td> Botão de menu pressionado </td><td> Botão 6 * </td><td> Botão 7 * </td><td> menuPressed</td>
</tr><tr>
<td> Botão de alça pressionado </td><td> Eixo 11 = 1,0 (sem valores analógicos)<br />Botão 4 <i>(compatível com gamepad)</i> </td><td> Eixo 12 = 1,0 (sem valores analógicos)<br />Botão 5 <i>(compatível com gamepad)</i> </td><td> compreenderam</td>
</tr><tr>
<td> Thumbstick X <i>(esquerda:-1,0, direita: 1,0)</i> </td><td> Eixo 1 </td><td> Eixo 4 </td><td> thumbstickPosition. x</td>
</tr><tr>
<td> Thumbstick Y <i>(superior:-1,0, inferior: 1,0)</i> </td><td> Eixo 2 </td><td> Eixo 5 </td><td> thumbstickPosition. y</td>
</tr><tr>
<td> Thumbstick pressionado </td><td> Botão 8 </td><td> Botão 9 </td><td> thumbstickPressed</td>
</tr><tr>
<td> Touchpad X <i>(esquerda:-1,0, direita: 1,0)</i> </td><td> Eixo 17 * </td><td> Eixo 19 * </td><td> touchpadPosition. x</td>
</tr><tr>
<td> Touchpad Y <i>(superior:-1,0, inferior: 1,0)</i> </td><td> Eixo 18 * </td><td> Eixo 20 * </td><td> touchpadPosition. y</td>
</tr><tr>
<td> Touchpad tocado </td><td> Botão 18 * </td><td> Botão 19 * </td><td> touchpadTouched</td>
</tr><tr>
<td> Touchpad pressionado </td><td> Botão 16 * </td><td> Botão 17 * </td><td> touchpadPressed</td>
</tr><tr>
<td> pose da alça de 6DoF de pose ou de ponteiro </td><td colspan="2"> <i>Segure</i> somente pose: <a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html">XR. InputTracking. GetLocalPosition</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalRotation.html">XR. InputTracking.GetLocalRotation</a></td><td> Passar <i>alça</i> ou <i>ponteiro</i> como um argumento: SourceState. sourcePose. TryGetPosition<br />origemstate. sourcePose. TryGetRotation<br /></td>
</tr><tr>
<td> Estado de acompanhamento </td><td colspan="2"> <i>A precisão da posição e o risco de perda de origem só estão disponíveis por meio da API específica do MR</i> </td><td> <a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourcePose-positionAccuracy.html">origemstate. sourcePose. positionAccuracy</a><br /><a href="https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionSourceProperties-sourceLossRisk.html">SourceState. Properties. sourceLossRisk</a></td>
</tr>
</table>

>[!NOTE]
>Essas IDs de botão/eixo diferem das IDs que o Unity usa para OpenVR devido a colisões nos mapeamentos usados por gamepads, Oculus Touch e OpenVR.

<!-- ### Using HP Reverb G2 controllers

If you're using the HP Reverb G2 controllers, refer to the table below for button and axis IDs.

<table>
<tr>
<th rowspan="2"><a href="https://docs.unity3d.com/ScriptReference/XR.CommonUsages.html">Input </th><th colspan="2">Common Unity APIs</a><br />(Input.GetButton/GetAxis) </th><th rowspan="2">HP Reverb G2 Input API</a></th>
</tr><tr>
<th> Left hand </th><th> Right hand</th>
</tr><tr>
<td> Primary2DAxis </td><td> Axis 1 (X) / Axis 2 (Y) </td><td> Axis 4 (X) / Axis 5(Y) </td><td> Thumbstick</td>
</tr><tr>
<td> Trigger pressed </td><td> Axis 9 </td><td> Axis 10 </td><td> Index trigger</td>
</tr><tr>
<td> Grip </td><td> Axis 11d </td><td> Axis 12 </td><td> Grip trigger</td>
</tr><tr>
<td> PrimaryButton pressed </td><td> Button 2 </td><td> Button 0 </td><td> Menu button pressed</td>
</tr><tr>
<td> SecondaryButton pressed </td><td> Button 3 </td><td> Button 1 </td><td> A/X button</td>
</tr><tr>
<td> GripButton </td><td> Button 4 </td><td> Button 5 </td><td> Grip trigger</td>
</tr><tr>
<td> TriggerButton </td><td> Button 14 </td><td> Button 15 </td><td> Index trigger</td>
</tr><tr>
</tr>
</table> -->

### <a name="openxr"></a>OpenXR

Para aprender as noções básicas sobre interações de realidade misturada no Unity, visite o [manual do Unity para entrada do Unity XR](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html). Esta documentação do Unity aborda os mapeamentos de entradas específicas do controlador para **InputFeatureUsage** s mais generalizadas, como as entradas de XR disponíveis podem ser identificadas e categorizadas, como ler dados dessas entradas e muito mais.

O plug-in Mixed Reality OpenXR fornece perfis de interação de entrada adicionais, mapeados para os **InputFeatureUsage** padrão, conforme detalhado abaixo:

| InputFeatureUsage | Controlador do HP reverbo G2 (OpenXR) | HoloLens Mão (OpenXR) |
| ---- | ---- | ---- |
| primary2DAxis | Botões | |
| primary2DAxisClick | Joystick – clique em | |
| gatilho | Gatilho  | |
| Dimensiona | Dimensiona | Toque ou aperte o ar |
| primaryButton | [X/A]-Pressione | Fechar e abrir dedos indicador e polegar |
| secondaryButton | [S/B]-Pressione | |
| gripButton | Segure a tecla | |
| triggerButton | Gatilho-Pressione | |
| menuButton | Menu | |

## <a name="grip-pose-vs-pointing-pose"></a>Segurar pose vs. ponto de apontar

o Windows Mixed Reality dá suporte a controladores de movimento em uma variedade de fatores forma. O design de cada controlador difere em sua relação entre a posição da mão do usuário e a direção natural "encaminhar" que os aplicativos devem usar para apontar ao renderizar o controlador.

Para representar melhor esses controladores, há dois tipos de poses que você pode investigar para cada origem de interação, a **pose de alça** e a pose do **ponteiro**. As coordenadas de pose pose e ponteiro representam expressas por todas as APIs do Unity nas coordenadas do mundo global do Unity.

### <a name="grip-pose"></a>Segurar pose

a **alça de pose** representa o local dos usuários palm, detectado por um HoloLens ou segurando um controlador de movimento.

Em headsets de imersão, a alça de pose é mais bem usada para renderizar **a mão do usuário** ou **um objeto mantido na mão do usuário**. A pose de alça também é usada ao visualizar um controlador de movimento. o **modelo renderizado** fornecido pelo Windows para um controlador de movimento usa a alça de pose como sua origem e o centro de rotação.

A pose de alça é definida especificamente da seguinte maneira:
* A **posição de alça**: o Palm centróide ao manter o controlador naturalmente, ajustado para a esquerda ou para a direita para centralizar a posição dentro da alça. no controlador de movimento de Windows Mixed Reality, essa posição geralmente se alinha com o botão compreender.
* O **eixo direito da orientação de alça**: quando você abre completamente a mão para formar uma pose plana de 5 dedos, o raio normal para o Palm (para frente do Palm esquerdo, para trás do Palm direito)
* O **eixo de encaminhamento da orientação de alça**: quando você fecha a sua mão parcialmente (como se você mantiver o controlador), o raio que aponta para "encaminhar" por meio do tubo formado por seus dedos não-thumbs.
* O **eixo superior da orientação de alça**: o eixo superior implícito pelas definições direita e avançar.

Você pode acessar a alça de pose por meio da API de entrada entre fornecedores do Unity (*[XR. InputTracking](https://docs.unity3d.com/ScriptReference/XR.InputTracking.html). GetLocalPosition/rotation*) ou por meio de Windows API específica do MR (*sourcestate. sourcePose. TryGetPosition/Rotation*, solicitando dados de pose para o nó de **fixação** ).

### <a name="pointer-pose"></a>Pose de ponteiro

A **pose do ponteiro** representa a ponta do controlador que está apontando para frente.

A pose de ponteiro fornecida pelo sistema é mais bem usada para Raycast quando você está **renderizando o próprio modelo de controlador**. Se estiver renderizando algum outro objeto virtual no lugar do controlador, como uma arma virtual, você deve apontar um raio mais natural para esse objeto virtual, como um Ray que viaja ao longo do cilindro do modelo de pressão definido pelo aplicativo. Como os usuários podem ver o objeto virtual e não o controlador físico, apontar com o objeto virtual provavelmente será mais natural para aqueles que usam seu aplicativo.

atualmente, a pose do ponteiro está disponível no Unity somente por meio do Windows API específica do MR, *sourcestate. sourcePose. TryGetPosition/Rotation*, passando *InteractionSourceNode. pointer* como o argumento.

### <a name="openxr"></a>OpenXR 

Você tem acesso a dois conjuntos de poses por meio de interações de entrada OpenXR:

* A alça representa a renderização de objetos à mão
* O objetivo se destaca no mundo.

Mais informações sobre esse design e as diferenças entre as duas poses podem ser encontradas na [especificação OpenXR-subcaminhos de entrada](https://www.khronos.org/registry/OpenXR/specs/1.0/html/xrspec.html#semantic-path-input).

As poses fornecidas pelo InputFeatureUsages **DevicePosition**, **DeviceRotation**, **DeviceVelocity** e **DeviceAngularVelocity** representam a pose de **alça** de OpenXR. Os InputFeatureUsages relacionados a pose são definidos no [CommonUsages](https://docs.unity3d.com/2020.2/Documentation/ScriptReference/XR.CommonUsages.html)do Unity.

As poses fornecidas pelo InputFeatureUsages **PointerPosition**, **PointerRotation**, **PointerVelocity** e **PointerAngularVelocity** representam a pose de **AIM** de OpenXR. Esses InputFeatureUsages não são definidos em nenhum arquivo C# incluído, portanto, você precisará definir seu próprio InputFeatureUsages da seguinte maneira:

``` cs
public static readonly InputFeatureUsage<Vector3> PointerPosition = new InputFeatureUsage<Vector3>("PointerPosition");
```

## <a name="haptics"></a>Haptics

Para obter informações sobre como usar o haptics no sistema de entrada XR da Unity, a documentação pode ser encontrada no [manual do Unity para o Unity XR Input-haptics](https://docs.unity3d.com/2020.2/Documentation/Manual/xr_input.html#Haptics).

## <a name="controller-tracking-state"></a>Estado de controle do controlador

como os headsets, o controlador de movimento de Windows Mixed Reality não requer nenhuma configuração de sensores de controle externo. Em vez disso, os controladores são acompanhados por sensores no próprio headset.

se o usuário mover os controladores para fora do campo de exibição do headset, Windows continuará inferindo as posições do controlador na maioria dos casos. Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada.

Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna. Muitos aplicativos que usam controladores para apontar e ativar elementos de interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba.

<!-- The best way to get a feel for this is to try it yourself. Check out this video with examples of immersive content that works with motion controllers across various tracking states:

<br>

 >[!VIDEO https://www.youtube.com/embed/QK_fOFDHj0g] -->

### <a name="reasoning-about-tracking-state-explicitly"></a>Raciocínio sobre o estado de rastreamento explicitamente

Os aplicativos que desejam tratar as posições de forma diferente com base no estado de controle podem ir além e inspecionar as propriedades no estado do controlador, como *SourceLossRisk* e *PositionAccuracy*:

<table>
<tr>
<th> Estado de acompanhamento </th><th> SourceLossRisk </th><th> PositionAccuracy </th><th> TryGetPosition</th>
</tr><tr>
<td> <b>Alta precisão</b> </td><td style="background-color: green; color: white"> &lt; 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Alta precisão (com risco de perda)</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: green; color: white"> Alto </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Precisão aproximada</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: green; color: white"> true</td>
</tr><tr>
<td> <b>Sem posição</b> </td><td style="background-color: orange"> = = 1,0 </td><td style="background-color: orange"> Aproximado </td><td style="background-color: orange"> false</td>
</tr>
</table>

Esses Estados de acompanhamento do controlador de movimento são definidos da seguinte maneira:
* **Alta precisão:** Embora o controlador de movimento esteja dentro do campo de exibição do headset, ele geralmente fornecerá posições de alta precisão, com base no rastreamento visual. Um controlador móvel que deixa momentaneamente o campo de exibição ou é momentaneamente obscurecido dos sensores do headset (por exemplo, por outro lado do usuário) continuará a retornar poses de alta precisão por um curto período, com base no acompanhamento inércia do próprio controlador.
* **Alta precisão (com risco de perda):** Quando o usuário move o controlador de movimento para cima da borda do campo de exibição do headset, o headset em breve não será capaz de rastrear visualmente a posição do controlador. O aplicativo sabe quando o controlador atingiu esse limite de FOV vendo o **SourceLossRisk** REACH 1,0. Nesse ponto, o aplicativo pode optar por pausar gestos do controlador que exigem um fluxo constante de poses de alta qualidade.
* **Precisão aproximada:** Quando o controlador tiver perdido o acompanhamento Visual por tempo suficiente, as posições do controlador serão descartadas para as posições de precisão aproximada. Neste ponto, o sistema bloqueará o corpo do controlador para o usuário, controlando a posição do usuário à medida que eles se movimentam, ao mesmo tempo em que ainda expõe a orientação verdadeira do controlador usando seus sensores de orientação interna. Muitos aplicativos que usam controladores para apontar para e ativar elementos da interface do usuário podem operar normalmente em precisão aproximada sem que o usuário perceba. Os aplicativos com requisitos de entrada mais pesados podem optar por detectar essa queda de **alta** precisão à precisão **aproximada** inspecionando a propriedade **PositionAccuracy** , por exemplo, para dar ao usuário um hitbox mais generosa em destinos fora da tela durante esse tempo.
* **Sem posição:** Embora o controlador possa operar com precisão aproximada por um longo tempo, às vezes o sistema sabe que até mesmo uma posição bloqueada pelo corpo não é significativa no momento. Por exemplo, um controlador que foi ativado pode nunca ter sido observado visualmente ou um usuário pode colocar um controlador selecionado por outra pessoa. Naqueles momentos, o sistema não fornecerá nenhuma posição ao aplicativo e *TryGetPosition* retornará false.

## <a name="common-unity-apis-inputgetbuttongetaxis"></a>APIs comuns do Unity (Input. getbutton/getaxis)

**Namespace:** *UnityEngine*, *UnityEngine. XR*<br>
**Tipos**: *Input*, *XR. InputTracking*

no momento, o Unity usa suas APIs de *entrada geral. getbutton/Input. getaxis* para expor a entrada para [o sdk do Oculus](https://docs.unity3d.com/Manual/OculusControllers.html), [o sdk do OpenVR e o](https://docs.unity3d.com/Manual/OpenVRControllers.html) Windows Mixed Reality, incluindo os controladores de mãos e de movimento. Se seu aplicativo usa essas APIs para entrada, ele pode facilmente dar suporte a controladores de movimento em vários SDKs de XR, incluindo Windows Mixed Reality.

### <a name="getting-a-logical-buttons-pressed-state"></a>Obtendo o estado pressionado de um botão lógico

Para usar as APIs de entrada gerais da Unity, você normalmente começará com a vinculação de botões e eixos a nomes lógicos no [Gerenciador de entrada do Unity](https://docs.unity3d.com/Manual/ConventionalGameInput.html), ligando um botão ou IDs de eixo a cada nome. Em seguida, você pode escrever código que se refere a esse botão lógico/nome do eixo.

por exemplo, para mapear o botão de gatilho do controlador de movimento à esquerda para a ação enviar, acesse **editar > Project Configurações > entrada** no Unity e expanda as propriedades da seção enviar em eixos. Altere o **botão positivo** ou a propriedade do **botão Alt positivo** para ler o **botão 14 do joystick**, desta forma:

![InputManager do Unity](images/unity-input-manager.png)<br>
*Unity InputManager*

Em seguida, o script pode verificar a ação Enviar usando *Input.GetButton:*

```cs
if (Input.GetButton("Submit"))
{
  // ...
}
```
Você pode adicionar mais botões lógicos alterando a **propriedade Tamanho** em **Eixos**.

### <a name="getting-a-physical-buttons-pressed-state-directly"></a>Obter o estado pressionado de um botão físico diretamente

Você também pode acessar os botões manualmente por seu nome totalmente qualificado, usando *Input.GetKey*:

```cs
if (Input.GetKey("joystick button 8"))
{
  // ...
}
```

### <a name="getting-a-hand-or-motion-controllers-pose"></a>Como obter uma pose do controlador de movimento ou de mão

Você pode acessar a posição e a rotação do controlador usando *XR. InputTracking:*

```cs
Vector3 leftPosition = InputTracking.GetLocalPosition(XRNode.LeftHand);
Quaternion leftRotation = InputTracking.GetLocalRotation(XRNode.LeftHand);
```

> [!NOTE] 
> O código acima representa a pose de mão do controlador (em que o usuário mantém o controlador), que é útil para renderizar uma lâmina ou umaada na mão do usuário ou um modelo do próprio controlador.
> 
> A relação entre essa pose de mão e a pose do ponteiro (em que a dica do controlador está apontando) pode ser diferente entre controladores. Neste momento, o acesso à pose de ponteiro do controlador só é possível por meio da API de entrada específica do MR, descrita nas seções abaixo.

## <a name="windows-specific-apis-xrwsainput"></a>Windows APIs específicas do Windows (XR). Wsa. Entrada)

> [!CAUTION]
> Se o projeto estiver usando qualquer um dos XR. APIs do WSA, elas estão sendo desaparadas em favor do SDK do XR em versões futuras do Unity. Para novos projetos, recomendamos usar o SDK do XR desde o início. Você pode encontrar mais informações sobre o sistema de [Entrada XR e as APIs aqui](https://docs.unity3d.com/Manual/xr_input.html).

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Tipos:** *InteractionManager,* *InteractionSourceState,* *InteractionSource*, *InteractionSourceProperties,* *InteractionSourceKind*, *InteractionSourceLocation*

Para obter informações mais detalhadas sobre Windows Mixed Reality entrada à mão (para HoloLens) e controladores de movimento, você pode optar por usar as APIs de entrada espacial específicas do Windows no namespace *UnityEngine.XR.WSA.Input.* Isso permite que você acesse informações adicionais, como a precisão da posição ou o tipo de origem, o que permite separar as mãos e os controladores.

### <a name="polling-for-the-state-of-hands-and-motion-controllers"></a>Sondagem para o estado de mãos e controladores de movimento

Você pode sondar o estado desse quadro para cada fonte de interação (mão ou controlador de movimento) usando o *método GetCurrentReading.*

```cs
var interactionSourceStates = InteractionManager.GetCurrentReading();
foreach (var interactionSourceState in interactionSourceStates) {
    // ...
}
```

Cada *InteractionSourceState* que você receber de volta representa uma fonte de interação no momento atual. O *InteractionSourceState* expõe informações como:
* Quais [tipos de pressionamentos](../../design/motion-controllers.md) estão ocorrendo (Selecionar/Menu/Compreensão/Touchpad/Thumbstick)

   ```cs
   if (interactionSourceState.selectPressed) {
       // ...
   }
   ```
* Outros dados específicos para controladores de movimento, como coordenadas XY do touchpad e/ou thumbstick e estado tocado

   ```cs
   if (interactionSourceState.touchpadTouched && interactionSourceState.touchpadPosition.x > 0.5) {
       // ...
   }
   ```

* O InteractionSourceKind para saber se a origem é uma mão ou um controlador de movimento

   ```cs
   if (interactionSourceState.source.kind == InteractionSourceKind.Hand) {
       // ...
   }
   ```

### <a name="polling-for-forward-predicted-rendering-poses"></a>Sondagem de poses de renderização previstas para a frente

* Ao sondar dados de origem de interação de mãos e controladores, as poses que você recebe são poses previstas para frente no momento em que os fótons desse quadro alcançarão os olhos do usuário.  As poses previstas para frente são mais bem usadas para **renderizar** o controlador ou um objeto mantido em cada quadro.  Se você estiver direcionando uma determinada press ou versão com o controlador, isso será mais preciso se você usar as APIs de evento histórico descritas abaixo.

   ```cs
   var sourcePose = interactionSourceState.sourcePose;
   Vector3 sourceGripPosition;
   Quaternion sourceGripRotation;
   if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Grip)) &&
       (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Grip))) {
       // ...
   }
   ```

* Você também pode obter a pose de cabeça prevista para frente para esse quadro atual.  Assim como acontece com **a** pose de origem, isso é útil para renderizar um cursor, embora o direcionamento a uma determinada press ou versão seja mais preciso se você usar as APIs de evento históricos descritas abaixo.

   ```cs
   var headPose = interactionSourceState.headPose;
   var headRay = new Ray(headPose.position, headPose.forward);
   RaycastHit raycastHit;
   if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
       var cursorPos = raycastHit.point;
       // ...
   }
   ```

### <a name="handling-interaction-source-events"></a>Manipulando eventos de origem de interação

Para manipular eventos de entrada conforme eles ocorrem com seus dados de pose históricos precisos, você pode manipular eventos de origem de interação em vez de sondagem.

Para manipular eventos de origem de interação:
* Registre-se *para um evento de entrada InteractionManager.* Para cada tipo de evento de interação no qual você está interessado, você precisa se inscrever nele.

   ```cs
   InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
   ```

* Manipular o evento. Depois de assinar um evento de interação, você receberá o retorno de chamada quando apropriado. No exemplo *SourcePressed,* isso ocorrerá depois que a origem for detectada e antes de ser liberada ou perdida.

   ```cs
   void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
       var interactionSourceState = args.state;

       // args.state has information about:
          // targeting head ray at the time when the event was triggered
          // whether the source is pressed or not
          // properties like position, velocity, source loss risk
          // source id (which hand id for example) and source kind like hand, voice, controller or other
   }
   ```

### <a name="how-to-stop-handling-an-event"></a>Como parar de manipular um evento

Você precisa parar de manipular um evento quando não estiver mais interessado no evento ou estiver destrói o objeto que assinou o evento. Para interromper o tratamento do evento, cancele a assinatura do evento.

```cs
InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
```

### <a name="list-of-interaction-source-events"></a>Lista de eventos de origem de interação

Os eventos de origem de interação disponíveis são:
* *InteractionSourceDetected (a* origem fica ativa)
* *InteractionSourceLost* (fica inativo)
* *InteractionSourcePressed* (toque, pressiona o botão ou "Selecionar" enunciado)
* *InteractionSourceReleased* (fim de um toque, botão liberado ou final de "Selecionar" enunciado)
* *InteractionSourceUpdated* (move ou altera algum estado)

### <a name="events-for-historical-targeting-poses-that-most-accurately-match-a-press-or-release"></a>Eventos para direcionamento histórico representam as que mais se combinam com uma press ou versão

As APIs de sondagem descritas anteriormente oferecem ao seu aplicativo poses previstas para o futuro.  Embora essas poses previstas sejam melhores para renderizar o controlador ou um objeto portátil virtual, as poses futuras não são ideais para direcionamento, por dois motivos principais:
* Quando o usuário pressiona um botão em um controlador, pode haver cerca de 20 ms de latência sem fio em Bluetooth antes que o sistema receba a pressão.
* Em seguida, se você estiver usando uma pose prevista para frente, haverá outra previsão de 10 a 20 ms aplicada para direcionar a hora em que os fótons do quadro atual alcançarão os olhos do usuário.

Isso significa que a sondagem oferece uma pose de origem ou uma pose de cabeça que é de 30 a 40 ms para frente de onde a cabeça e as mãos do usuário realmente estavam de volta quando a pressão ou a liberação aconteceu.  Para HoloLens entrada manual, embora não haja atraso na transmissão sem fio, há um atraso de processamento semelhante para detectar a pressão.

Para direcionar com precisão com base na intenção original do usuário para uma pressionamento de mão ou controlador, você deve usar a pose de origem histórica ou a pose de cabeça desse evento de entrada *InteractionSourcePressed* ou *InteractionSourceReleased.*

Você pode direcionar uma press ou versão com dados de pose históricos da cabeça do usuário ou do controlador:
* A posição da cabeça no momento em que ocorreu um  gesto ou pressionamento de controlador, que pode ser usado para direcionamento para determinar o que o usuário estava [olhando:](../../design/gaze-and-commit.md)

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args) {
       var interactionSourceState = args.state;
       var headPose = interactionSourceState.headPose;
       RaycastHit raycastHit;
       if (Physics.Raycast(headPose.position, headPose.forward, out raycastHit, 10)) {
           var targetObject = raycastHit.collider.gameObject;
           // ...
       }
   }
   ```

* A pose de origem no momento em que ocorreu  uma pressão do controlador de movimento, que pode ser usada para direcionamento para determinar em que o usuário estava apontando o controlador.  Esse será o estado do controlador que passou pela pressão.  Se você estiver renderizar o controlador em si, poderá solicitar a pose do ponteiro em vez da pose da mão, para disparar o raio de direcionamento do que o usuário considerará a dica natural desse controlador renderizado:

   ```cs
   void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs args)
   {
       var interactionSourceState = args.state;
       var sourcePose = interactionSourceState.sourcePose;
       Vector3 sourceGripPosition;
       Quaternion sourceGripRotation;
       if ((sourcePose.TryGetPosition(out sourceGripPosition, InteractionSourceNode.Pointer)) &&
           (sourcePose.TryGetRotation(out sourceGripRotation, InteractionSourceNode.Pointer))) {
           RaycastHit raycastHit;
           if (Physics.Raycast(sourceGripPosition, sourceGripRotation * Vector3.forward, out raycastHit, 10)) {
               var targetObject = raycastHit.collider.gameObject;
               // ...
           }
       }
   }
   ```

### <a name="event-handlers-example"></a>Exemplo de manipuladores de eventos

```cs
using UnityEngine.XR.WSA.Input;

void Start()
{
    InteractionManager.InteractionSourceDetected += InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost += InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed += InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased += InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated += InteractionManager_InteractionSourceUpdated;
}

void OnDestroy()
{
    InteractionManager.InteractionSourceDetected -= InteractionManager_InteractionSourceDetected;
    InteractionManager.InteractionSourceLost -= InteractionManager_InteractionSourceLost;
    InteractionManager.InteractionSourcePressed -= InteractionManager_InteractionSourcePressed;
    InteractionManager.InteractionSourceReleased -= InteractionManager_InteractionSourceReleased;
    InteractionManager.InteractionSourceUpdated -= InteractionManager_InteractionSourceUpdated;
}

void InteractionManager_InteractionSourceDetected(InteractionSourceDetectedEventArgs args)
{
    // Source was detected
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceLost(InteractionSourceLostEventArgs state)
{
    // Source was lost. This will be after a SourceDetected event and no other events for this
    // source id will occur until it is Detected again
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourcePressed(InteractionSourcePressedEventArgs state)
{
    // Source was pressed. This will be after the source was detected and before it is
    // released or lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceReleased(InteractionSourceReleasedEventArgs state)
{
    // Source was released. The source would have been detected and pressed before this point.
    // This event will not fire if the source is lost
    // args.state has the current state of the source including id, position, kind, etc.
}

void InteractionManager_InteractionSourceUpdated(InteractionSourceUpdatedEventArgs state)
{
    // Source was updated. The source would have been detected before this point
    // args.state has the current state of the source including id, position, kind, etc.
}
```

## <a name="motion-controllers-in-mrtk"></a>Controladores de movimento no MRTK

Você pode acessar [o gesto e o controlador de movimento](/windows/mixed-reality/mrtk-unity/features/input/controllers) do Gerenciador de entrada.

## <a name="follow-along-with-tutorials"></a>Acompanhe com tutoriais

Tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis no Mixed Reality Academy:

- [Entrada do MR 211: gesto](tutorials/holograms-211.md)
- [Entrada do MR 213: controladores de movimentos](../../deprecated/mixed-reality-213.md)

[![Entrada 213 do MR – Controlador de movimento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Entrada 213 do MR – Controlador de movimento*

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo o percurso de desenvolvimento do Unity que fizemos, você está no meio da exploração dos blocos de construção principais do MRTK. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Acompanhamento de mãos e olhos](./hand-eye-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Veja também

* [Focar com a cabeça e confirmar](../../design/gaze-and-commit.md)
* [Controladores de movimentos](../../design/motion-controllers.md)