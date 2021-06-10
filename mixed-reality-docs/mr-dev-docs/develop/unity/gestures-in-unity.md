---
title: Gestos no Unity
description: Saiba como agir em sua olhar no Unity com entrada de gestos à mão usando as APIs de botão e de botões comuns e de eixo.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: gestos, Unity, olhar, entrada, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 87666c120686547b1a07f6da41519219d4a47720
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600635"
---
# <a name="gestures-in-unity"></a>Gestos no Unity

Há duas maneiras principais de agir em sua [olhar no Unity](gaze-in-unity.md), [gestos de mão](../../design/gaze-and-commit.md#composite-gestures) e [controladores de movimento](../../design/motion-controllers.md) no HoloLens e HMD de imersão. Você acessa os dados de ambas as fontes de entrada espacial por meio das mesmas APIs no Unity.

O Unity fornece duas maneiras principais de acessar dados de entrada espaciais para a realidade mista do Windows. As APIs comuns *Input. getbutton/Input. getaxis* funcionam em vários SDKs do Unity XR, enquanto a API *interactionmanager/GestureRecognizer* específica para a realidade mista do Windows expõe o conjunto completo de dados de entrada espaciais.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>APIs de gesto de composição de alto nível (GestureRecognizer)

**Namespace:** *UnityEngine. XR. WSA. Input*<br>
**Tipos**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*

Seu aplicativo também pode reconhecer gestos de composição de nível superior para fontes de entrada espaciais, toque, retenção, manipulação e gestos de navegação. Você pode reconhecer esses gestos compostos entre os controladores de [mão](../../design/gaze-and-commit.md#composite-gestures) e de [movimento](../../design/motion-controllers.md) usando o GestureRecognizer.

Cada evento de gesto no GestureRecognizer fornece o SourceKind para a entrada, bem como a cabeça de destino Ray no momento do evento. Alguns eventos fornecem informações adicionais específicas do contexto.

Há apenas algumas etapas necessárias para capturar gestos usando um reconhecedor de gestos:
1. Criar um novo reconhecedor de gestos
2. Especificar quais gestos observar
3. Assinar eventos para esses gestos
4. Começar a capturar gestos

### <a name="create-a-new-gesture-recognizer"></a>Criar um novo reconhecedor de gestos

Para usar o *GestureRecognizer*, você deve ter criado um *GestureRecognizer*:

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Especificar quais gestos observar

Especifique em quais gestos você está interessado por meio de *SetRecognizableGestures ()*:

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Assinar eventos para esses gestos

Assine eventos para os gestos nos quais você está interessado.

```cs
void Start()
{
    recognizer.Tapped += GestureRecognizer_Tapped;
    recognizer.HoldStarted += GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted += GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled += GestureRecognizer_HoldCanceled;
}
```

>[!NOTE]
>Os gestos de navegação e manipulação são mutuamente exclusivos em uma instância de um *GestureRecognizer*.

### <a name="start-capturing-gestures"></a>Começar a capturar gestos

Por padrão, um *GestureRecognizer* não monitora a entrada até que *StartCapturingGestures ()* seja chamado. É possível que um evento de gesto possa ser gerado após *StopCapturingGestures ()* ser chamado se a entrada tiver sido executada antes do quadro em que *StopCapturingGestures ()* foi processado. O *GestureRecognizer* se lembrará de estar ligado ou desligado durante o quadro anterior no qual o gesto realmente ocorreu e, portanto, é confiável iniciar e parar o monitoramento de gestos com base no direcionamento de olhar do quadro.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Parar a captura de gestos

Para interromper o reconhecimento de gesto:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Removendo um reconhecedor de gesto

Lembre-se de cancelar a assinatura de eventos assinados antes de destruir um objeto *GestureRecognizer* .

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Renderizando o modelo de controlador de movimento no Unity

![Modelo de controlador de movimento e teleportação](images/motioncontrollertest-teleport-1000px.png)<br>
*Modelo de controlador de movimento e teleportação*

Para renderizar os controladores de movimento em seu aplicativo que correspondam aos controladores físicos que os usuários estão mantendo e articulados conforme vários botões são pressionados, você pode usar o **MotionController pré-fabricado** no [Kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity/).  Esse pré-fabricado dinamicamente carrega o modelo de glTF correto em tempo de execução do driver do controlador de movimento instalado do sistema.  É importante carregar esses modelos dinamicamente, em vez de importá-los manualmente no editor, para que seu aplicativo mostre modelos 3D fisicamente precisos para todos os controladores atuais e futuros que seus usuários possam ter.

1. Siga as instruções de [introdução](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) para baixar o kit de ferramentas de realidade misturada e adicioná-lo ao seu projeto do Unity.
2. Se você substituiu a câmera pelo *MixedRealityCameraParent* pré-fabricado como parte das etapas introdução, está pronto!  Esse pré-fabricado inclui a renderização do controlador de movimento.  Caso contrário, adicione *assets/HoloToolkit/Input/pré-fabricados/MotionControllers. pré-fabricado* à sua cena no painel do projeto.  Você desejará adicionar esse pré-fabricado como um filho de qualquer objeto pai usado para mover a câmera quando o usuário estiver em sua cena, para que os controladores acompanhem o usuário.  Se seu aplicativo não envolver a teleportabilidade, basta adicionar o pré-fabricado na raiz da sua cena.

## <a name="throwing-objects"></a>Lançando objetos

Lançar objetos na realidade virtual é um problema mais difícil do que parece, na primeira vez. Assim como acontece com a maioria das interações com base fisicamente, quando o jogo atua de forma inesperada, ele é imediatamente óbvio e quebra imersão. Já gastamos algum tempo pensando em como representar um comportamento de lançamento fisicamente correto e apresentamos algumas diretrizes, habilitadas por meio de atualizações em nossa plataforma, que gostaríamos de compartilhar com você.

Você pode encontrar um exemplo de como é recomendável implementar o lançamento [aqui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage). Este exemplo segue estas quatro diretrizes:
* **Use a *velocidade* do controlador em vez da posição**. Na atualização de novembro do Windows, apresentamos uma alteração no comportamento no estado de [controle posicional ' ' aproximado](../../design/motion-controllers.md#controller-tracking-state)'. Quando nesse estado, as informações de velocidade sobre o controlador continuarão sendo relatadas pelo tempo que acreditarem em sua precisão alta, o que geralmente é maior que a posição permanece com alta precisão.
* **Incorpore a *velocidade angular* do controlador**. Essa lógica está todas contidas no `throwing.cs` arquivo no `GetThrownObjectVelAngVel` método estático, dentro do pacote vinculado acima:
   1. À medida que a velocidade angular é conservada, o objeto gerado deve manter a mesma velocidade angular que tinha no momento do lançamento: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Como o centro da massa do objeto gerado provavelmente não está na origem da pose de alça, ele provavelmente tem uma velocidade diferente daquela do controlador no quadro de referência do usuário. A parte da velocidade do objeto que contribuiu dessa forma é a velocidade tangential instantânea do centro da massa do objeto gerado em relação à origem do controlador. Essa velocidade de tangential é o produto cruzado da velocidade angular do controlador com o vetor que representa a distância entre a origem do controlador e o centro da massa do objeto gerado.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. A velocidade total do objeto gerado é a soma da velocidade do controlador e dessa velocidade de tangential: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Preste muita atenção à *hora* em que aplicamos a velocidade**. Quando um botão é pressionado, pode levar até 20 ms para que esse evento seja emergido por meio do Bluetooth para o sistema operacional. Isso significa que, se você sondar uma alteração de estado do controlador de pressionado para não pressionado ou o contrário, o controlador apresentará as informações que você obtém com ele, na verdade, estará à frente dessa alteração no estado. Além disso, a pose do controlador apresentada por nossa API de sondagem está prevista para refletir uma causa provável no momento em que o quadro será exibido, o que poderia ser mais de 20 ms no futuro. Isso é bom para *renderizar* objetos mantidos, mas aumenta nosso problema de tempo para *direcionar* o objeto à medida que calculamos a trajetória para o momento em que o usuário lançou o lançamento. Felizmente, com a atualização de novembro, quando um evento do Unity como *InteractionSourcePressed* ou *InteractionSourceReleased* é enviado, o estado inclui os dados históricos de back quando o botão foi pressionado ou liberado.  Para obter a renderização de controlador e o direcionamento de controlador mais precisos durante as jogadas, você deve usar corretamente a sondagem e o evento, conforme apropriado:
   * Para **renderizar** cada quadro do controlador, seu aplicativo deve posicionar o *gameobject* do controlador no controlador previsto para o momento da Photon do quadro atual.  Você obtém esses dados de APIs de sondagem do Unity como a *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* ou *[XR. WSA. Entrada. interactionmanager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.
   * Para **direcionamento de controlador** em uma prensa ou liberação, seu aplicativo deve Raycast e calcular as trajetórias com base na pose do controlador histórico para esse evento de Press ou Release.  Você obtém esses dados das APIs de eventos do Unity, como *[interactionmanager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.
* **Use a pose de alça**. A velocidade angular e a velocidade são relatadas em relação à pose de alça, não à pose de ponteiro.

O lançamento continuará a melhorar com futuras atualizações do Windows e você poderá esperar mais informações sobre ela aqui.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Controladores de gesto e movimento no MRTK

Você pode acessar o gesto e o controlador de movimento do Gerenciador de entrada.

* [Gesto em MRTK](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [Controlador de movimento no MRTK](/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a>Acompanhe com tutoriais

Os tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis na Academia de realidade misturada:

- [Entrada do MR 211: gesto](tutorials/holograms-211.md)
- [Entrada do MR 213: controladores de movimentos](../../deprecated/mixed-reality-213.md)

[![Entrada MR 213-controlador de movimento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)<br>
*Entrada MR 213-controlador de movimento*

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core. Deste ponto, você pode prosseguir para o próximo bloco de construção:

> [!div class="nextstepaction"]
> [Acompanhamento de mãos e olhos](./hand-eye-in-unity.md)

Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.

## <a name="see-also"></a>Veja também

* [Focar com a cabeça e confirmar](../../design/gaze-and-commit.md)
* [Controladores de movimentos](../../design/motion-controllers.md)