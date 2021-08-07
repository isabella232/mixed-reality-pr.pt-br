---
title: Gestos no Unity
description: Saiba como tomar medidas em seu olhar no Unity com entrada de gesto de mão usando XR e APIs comuns de botão e eixo.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: gestos, unity, olhar, entrada, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, MRTK, Realidade Misturada Toolkit
ms.openlocfilehash: 8dd6b64dd0bb52e64515a43d69713ecc5dc6bcec203a987568f7c25ac492a864
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115214742"
---
# <a name="gestures-in-unity"></a>Gestos no Unity

Há duas maneiras principais de tomar medidas em seu [](../../design/motion-controllers.md) olhar no [Unity,](gaze-in-unity.md) [gestos](../../design/gaze-and-commit.md#composite-gestures) de mão e controladores de movimento HoloLens e HMD imersivo. Você acessa os dados de ambas as fontes de entrada espacial por meio das mesmas APIs no Unity.

O Unity fornece duas maneiras principais de acessar dados de entrada espaciais para Windows Mixed Reality. As APIs *Input.GetButton/Input.GetAxis* comuns funcionam em vários SDKs XR do Unity, enquanto a API *InteractionManager/GestureRecognizer* específica Windows Mixed Reality expõe o conjunto completo de dados de entrada espaciais.

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a>APIs de gesto composto de alto nível (GestureRecognizer)

**Namespace:** *UnityEngine.XR.WSA.Input*<br>
**Tipos:** *GestureRecognizer,* *GestureSettings,* *InteractionSourceKind*

Seu aplicativo também pode reconhecer gestos compostos de nível superior para fontes de entrada espaciais, gestos de Toque, Espera, Manipulação e Navegação. Você pode reconhecer esses gestos compostos entre as [mãos e](../../design/gaze-and-commit.md#composite-gestures) os [controladores de movimento](../../design/motion-controllers.md) usando o GestureRecognizer.

Cada evento Gesture no GestureRecognizer fornece o SourceKind para a entrada, bem como o raio de cabeça de direcionamento no momento do evento. Alguns eventos fornecem informações adicionais específicas do contexto.

Há apenas algumas etapas necessárias para capturar gestos usando um Reconhecedor de Gestos:
1. Criar um reconhecedor de gestos
2. Especificar quais gestos observar
3. Assinar eventos para esses gestos
4. Iniciar a captura de gestos

### <a name="create-a-new-gesture-recognizer"></a>Criar um reconhecedor de gestos

Para usar *o GestureRecognizer*, você deve ter criado um *GestureRecognizer:*

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a>Especificar quais gestos observar

Especifique em quais gestos você está interessado por meio *de SetRecognizableGestures():*

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a>Assinar eventos para esses gestos

Assine eventos para os gestos em que você está interessado.

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
>Os gestos de navegação e manipulação são mutuamente exclusivos em uma instância de *um GestureRecognizer.*

### <a name="start-capturing-gestures"></a>Iniciar a captura de gestos

Por padrão, *um GestureRecognizer* não monitora a entrada até *que StartCapturingGestures()* seja chamado. É possível que um evento de gesto possa ser gerado depois que *StopCapturingGestures()* for chamado se a entrada tiver sido executada antes do quadro em que *StopCapturingGestures()* foi processado. O *GestureRecognizer* lembrará se ele estava ou não desligado durante o quadro anterior no qual o gesto realmente ocorreu e, portanto, é confiável iniciar e parar o monitoramento de gestos com base no direcionamento de olhar desse quadro.

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a>Parar a captura de gestos

Para interromper o reconhecimento de gesto:

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a>Removendo um reconhecedor de gestos

Lembre-se de cancelar a assinatura de eventos inscritos antes de destruir *um objeto GestureRecognizer.*

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a>Renderizar o modelo do controlador de movimento no Unity

![Modelo e modelagem do Controlador de Movimento](images/motioncontrollertest-teleport-1000px.png)<br>
*Modelo e modelagem do controlador de movimento*

Para renderizar controladores de movimento em seu aplicativo que corresponderem aos controladores físicos que os usuários estão mantendo e articulam conforme vários botões são pressionados, você pode usar o **pré-fab MotionController** no Toolkit [.](https://github.com/Microsoft/MixedRealityToolkit-Unity/)  Esse pré-fab carrega dinamicamente o modelo glTF correto em runtime do driver do controlador de movimento instalado do sistema.  É importante carregar esses modelos dinamicamente em vez de importá-los manualmente no editor, para que seu aplicativo mostre modelos 3D fisicamente precisos para quaisquer controladores atuais e futuros que seus usuários possam ter.

1. Siga as [Ponto de Partida](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) para baixar o Toolkit realidade misturada e adicioná-lo ao seu projeto do Unity.
2. Se você substituiu sua câmera pelo pré-fab *MixedRealityCameraParent* como parte das etapas Ponto de Partida, você pode ir!  Esse pré-fab inclui a renderização do controlador de movimento.  Caso contrário, *adicione Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* à sua cena no painel Project aplicativo.  Você deseja adicionar esse pré-fab como um filho de qualquer objeto pai que você usa para mover a câmera quando o usuário se move dentro de sua cena, para que os controladores sejam acompanhados pelo usuário.  Se seu aplicativo não envolver a avaliação, basta adicionar o pré-fab na raiz da cena.

## <a name="throwing-objects"></a>Lançando objetos

Lançar objetos na realidade virtual é um problema mais difícil do que pode parecer inicialmente. Assim como acontece com a maioria das interações baseadas fisicamente, ao lançar o jogo atua de maneira inesperada, isso é imediatamente óbvio e interrompe a imersão. Passamos algum tempo pensando profundamente sobre como representar um comportamento de lançamento fisicamente correto e encontramos algumas diretrizes, habilitadas por meio de atualizações para nossa plataforma, que queremos compartilhar com você.

Você pode encontrar um exemplo de como recomendamos implementar a aplicação [aqui.](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage) Este exemplo segue estas quatro diretrizes:
* **Use a velocidade do controlador *em vez* da posição**. Na atualização de novembro para Windows, introduzimos uma alteração no comportamento quando no estado de acompanhamento [posicional ''Aproximado''.](../../design/motion-controllers.md#controller-tracking-state) Nesse estado, as informações de velocidade sobre o controlador continuarão a ser relatadas desde que acreditamos que sua alta precisão, que geralmente é maior do que a posição, permanece com alta precisão.
* **Incorpore *a velocidade angular* do controlador**. Essa lógica está contida no arquivo `throwing.cs` no método `GetThrownObjectVelAngVel` estático, dentro do pacote vinculado acima:
   1. Como a velocidade angular é preservada, o objeto lançado deve manter a mesma velocidade angular que tinha no momento do lançamento: `objectAngularVelocity = throwingControllerAngularVelocity;`
   2. Como o centro de massa do objeto lançado provavelmente não está na origem da pose da mão, ele provavelmente tem uma velocidade diferente da do controlador no quadro de referência do usuário. A parte da velocidade do objeto contribuiu dessa maneira é a velocidade tangencial instantânea do centro da massa do objeto lançado em torno da origem do controlador. Essa velocidade tangencial é o produto cruzado da velocidade angular do controlador com o vetor que representa a distância entre a origem do controlador e o centro da massa do objeto lançado.

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. A velocidade total do objeto lançado é a soma da velocidade do controlador e essa velocidade tangencial: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`

* **Preste muita atenção ao *tempo em* que aplicamos a velocidade**. Quando um botão é pressionado, pode levar até 20 ms para que esse evento se esgoe por meio Bluetooth para o sistema operacional. Isso significa que, se você sondar uma alteração de estado do controlador de pressionado para não pressionado ou o contrário, as informações de pose do controlador que você obter com ela realmente estarão à frente dessa alteração no estado. Além disso, a pose do controlador apresentada por nossa API de sondagem é prevista para refletir uma provável pose no momento em que o quadro será exibido, o que pode ter mais de 20 ms no futuro. Isso é bom *para* renderizar objetos mantidos, mas também nosso problema de tempo para direcionar o objeto à medida que calculamos a história para o momento em que o usuário lançou o lançamento.  Felizmente, com a atualização de novembro, quando um evento do Unity como *InteractionSourcePressed* ou *InteractionSourceReleased* é enviado, o estado inclui os dados de pose históricos de volta quando o botão foi pressionado ou liberado.  Para obter a renderização e o direcionamento do controlador mais precisos durante lançamentos, você deve usar corretamente sondagem e eventos, conforme apropriado:
   * Para **o controlador renderizar** cada quadro, seu aplicativo deve posicionar o *GameObject* do controlador na pose do controlador previsto para o tempo de foton do quadro atual.  Você obterá esses dados de APIs de sondagem do Unity, como *[XR. InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* ou *[XR. Wsa. Input.InteractionManager.GetCurrentReading.](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*
   * Para **o controlador destinado** a uma press ou versão, seu aplicativo deve raycast e calcular as marcações com base na pose do controlador histórico para esse evento de press ou release.  Você obterá esses dados de APIs de eventos do Unity, como *[InteractionManager.InteractionSourcePressed.](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*
* **Use a pose de segurar**. Angular velocidade e velocidade são relatadas em relação à pose da mão, não à pose do ponteiro.

O lançamento continuará a melhorar com Windows futuras atualizações, e você pode esperar encontrar mais informações sobre ele aqui.

## <a name="gesture-and-motion-controllers-in-mrtk"></a>Controladores de gesto e movimento no MRTK

Você pode acessar o gesto e o controlador de movimento do Gerenciador de entrada.

* [Gesto no MRTK](/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [Controlador de movimento no MRTK](/windows/mixed-reality/mrtk-unity/features/input/controllers)

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