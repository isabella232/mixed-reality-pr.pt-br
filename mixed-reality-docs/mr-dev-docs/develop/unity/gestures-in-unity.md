---
title: Gestos no Unity
description: Saiba como agir em sua olhar no Unity com entrada de gestos à mão usando as APIs de botão e de botões comuns e de eixo.
author: hferrone
ms.author: alexturn
ms.date: 12/1/2020
ms.topic: article
keywords: gestos, Unity, olhar, entrada, headset de realidade misturada, headset de realidade mista do Windows, headset da realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 523f05f9b3dd05a140bb40168b654a2dc0b00bb5
ms.sourcegitcommit: 1c9035487270af76c6eaba11b11f6fc56c008135
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107299711"
---
# <a name="gestures-in-unity"></a><span data-ttu-id="7ca6e-104">Gestos no Unity</span><span class="sxs-lookup"><span data-stu-id="7ca6e-104">Gestures in Unity</span></span>

<span data-ttu-id="7ca6e-105">Há duas maneiras principais de agir em sua [olhar no Unity](gaze-in-unity.md), [gestos de mão](../../design/gaze-and-commit.md#composite-gestures) e [controladores de movimento](../../design/motion-controllers.md) no HoloLens e HMD de imersão.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-105">There are two key ways to take action on your [gaze in Unity](gaze-in-unity.md), [hand gestures](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) in HoloLens and Immersive HMD.</span></span> <span data-ttu-id="7ca6e-106">Você acessa os dados de ambas as fontes de entrada espacial por meio das mesmas APIs no Unity.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-106">You access the data for both sources of spatial input through the same APIs in Unity.</span></span>

<span data-ttu-id="7ca6e-107">O Unity fornece duas maneiras principais de acessar dados de entrada espaciais para a realidade mista do Windows.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-107">Unity provides two primary ways to access spatial input data for Windows Mixed Reality.</span></span> <span data-ttu-id="7ca6e-108">As APIs comuns *Input. getbutton/Input. getaxis* funcionam em vários SDKs do Unity XR, enquanto a API *interactionmanager/GestureRecognizer* específica para a realidade mista do Windows expõe o conjunto completo de dados de entrada espaciais.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-108">The common *Input.GetButton/Input.GetAxis* APIs work across multiple Unity XR SDKs, while the *InteractionManager/GestureRecognizer* API specific to Windows Mixed Reality exposes the full set of spatial input data.</span></span>

## <a name="high-level-composite-gesture-apis-gesturerecognizer"></a><span data-ttu-id="7ca6e-109">APIs de gesto de composição de alto nível (GestureRecognizer)</span><span class="sxs-lookup"><span data-stu-id="7ca6e-109">High-level composite gesture APIs (GestureRecognizer)</span></span>

<span data-ttu-id="7ca6e-110">**Namespace:** *UnityEngine. XR. WSA. Input*</span><span class="sxs-lookup"><span data-stu-id="7ca6e-110">**Namespace:** *UnityEngine.XR.WSA.Input*</span></span><br>
<span data-ttu-id="7ca6e-111">**Tipos**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span><span class="sxs-lookup"><span data-stu-id="7ca6e-111">**Types**: *GestureRecognizer*, *GestureSettings*, *InteractionSourceKind*</span></span>

<span data-ttu-id="7ca6e-112">Seu aplicativo também pode reconhecer gestos de composição de nível superior para fontes de entrada espaciais, toque, retenção, manipulação e gestos de navegação.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-112">Your app can also recognize higher-level composite gestures for spatial input sources, Tap, Hold, Manipulation, and Navigation gestures.</span></span> <span data-ttu-id="7ca6e-113">Você pode reconhecer esses gestos compostos entre os controladores de [mão](../../design/gaze-and-commit.md#composite-gestures) e de [movimento](../../design/motion-controllers.md) usando o GestureRecognizer.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-113">You can recognize these composite gestures across both [hands](../../design/gaze-and-commit.md#composite-gestures) and [motion controllers](../../design/motion-controllers.md) using the GestureRecognizer.</span></span>

<span data-ttu-id="7ca6e-114">Cada evento de gesto no GestureRecognizer fornece o SourceKind para a entrada, bem como a cabeça de destino Ray no momento do evento.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-114">Each Gesture event on the GestureRecognizer provides the SourceKind for the input as well as the targeting head ray at the time of the event.</span></span> <span data-ttu-id="7ca6e-115">Alguns eventos fornecem informações adicionais específicas do contexto.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-115">Some events provide additional context-specific information.</span></span>

<span data-ttu-id="7ca6e-116">Há apenas algumas etapas necessárias para capturar gestos usando um reconhecedor de gestos:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-116">There are only a few steps required to capture gestures using a Gesture Recognizer:</span></span>
1. <span data-ttu-id="7ca6e-117">Criar um novo reconhecedor de gestos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-117">Create a new Gesture Recognizer</span></span>
2. <span data-ttu-id="7ca6e-118">Especificar quais gestos observar</span><span class="sxs-lookup"><span data-stu-id="7ca6e-118">Specify which gestures to watch for</span></span>
3. <span data-ttu-id="7ca6e-119">Assinar eventos para esses gestos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-119">Subscribe to events for those gestures</span></span>
4. <span data-ttu-id="7ca6e-120">Começar a capturar gestos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-120">Start capturing gestures</span></span>

### <a name="create-a-new-gesture-recognizer"></a><span data-ttu-id="7ca6e-121">Criar um novo reconhecedor de gestos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-121">Create a new Gesture Recognizer</span></span>

<span data-ttu-id="7ca6e-122">Para usar o *GestureRecognizer*, você deve ter criado um *GestureRecognizer*:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-122">To use the *GestureRecognizer*, you must have created a *GestureRecognizer*:</span></span>

```cs
GestureRecognizer recognizer = new GestureRecognizer();
```

### <a name="specify-which-gestures-to-watch-for"></a><span data-ttu-id="7ca6e-123">Especificar quais gestos observar</span><span class="sxs-lookup"><span data-stu-id="7ca6e-123">Specify which gestures to watch for</span></span>

<span data-ttu-id="7ca6e-124">Especifique em quais gestos você está interessado por meio de *SetRecognizableGestures ()*:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-124">Specify which gestures you're interested in via *SetRecognizableGestures()*:</span></span>

```cs
recognizer.SetRecognizableGestures(GestureSettings.Tap | GestureSettings.Hold);
```

### <a name="subscribe-to-events-for-those-gestures"></a><span data-ttu-id="7ca6e-125">Assinar eventos para esses gestos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-125">Subscribe to events for those gestures</span></span>

<span data-ttu-id="7ca6e-126">Assine eventos para os gestos nos quais você está interessado.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-126">Subscribe to events for the gestures you're interested in.</span></span>

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
><span data-ttu-id="7ca6e-127">Os gestos de navegação e manipulação são mutuamente exclusivos em uma instância de um *GestureRecognizer*.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-127">Navigation and Manipulation gestures are mutually exclusive on an instance of a *GestureRecognizer*.</span></span>

### <a name="start-capturing-gestures"></a><span data-ttu-id="7ca6e-128">Começar a capturar gestos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-128">Start capturing gestures</span></span>

<span data-ttu-id="7ca6e-129">Por padrão, um *GestureRecognizer* não monitora a entrada até que *StartCapturingGestures ()* seja chamado.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-129">By default, a *GestureRecognizer* doesn't monitor input until *StartCapturingGestures()* is called.</span></span> <span data-ttu-id="7ca6e-130">É possível que um evento de gesto possa ser gerado após *StopCapturingGestures ()* ser chamado se a entrada tiver sido executada antes do quadro em que *StopCapturingGestures ()* foi processado.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-130">It's possible that a gesture event may be generated after *StopCapturingGestures()* is called if input was performed before the frame where *StopCapturingGestures()* was processed.</span></span> <span data-ttu-id="7ca6e-131">O *GestureRecognizer* se lembrará de estar ligado ou desligado durante o quadro anterior no qual o gesto realmente ocorreu e, portanto, é confiável iniciar e parar o monitoramento de gestos com base no direcionamento de olhar do quadro.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-131">The *GestureRecognizer* will remember whether it was on or off during the previous frame in which the gesture actually occurred, and so it's reliable to start and stop gesture monitoring based on this frame's gaze targeting.</span></span>

```cs
recognizer.StartCapturingGestures();
```

### <a name="stop-capturing-gestures"></a><span data-ttu-id="7ca6e-132">Parar a captura de gestos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-132">Stop capturing gestures</span></span>

<span data-ttu-id="7ca6e-133">Para interromper o reconhecimento de gesto:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-133">To stop gesture recognition:</span></span>

```cs
recognizer.StopCapturingGestures();
```

### <a name="removing-a-gesture-recognizer"></a><span data-ttu-id="7ca6e-134">Removendo um reconhecedor de gesto</span><span class="sxs-lookup"><span data-stu-id="7ca6e-134">Removing a gesture recognizer</span></span>

<span data-ttu-id="7ca6e-135">Lembre-se de cancelar a assinatura de eventos assinados antes de destruir um objeto *GestureRecognizer* .</span><span class="sxs-lookup"><span data-stu-id="7ca6e-135">Remember to unsubscribe from subscribed events before destroying a *GestureRecognizer* object.</span></span>

```cs
void OnDestroy()
{
    recognizer.Tapped -= GestureRecognizer_Tapped;
    recognizer.HoldStarted -= GestureRecognizer_HoldStarted;
    recognizer.HoldCompleted -= GestureRecognizer_HoldCompleted;
    recognizer.HoldCanceled -= GestureRecognizer_HoldCanceled;
}
```

## <a name="rendering-the-motion-controller-model-in-unity"></a><span data-ttu-id="7ca6e-136">Renderizando o modelo de controlador de movimento no Unity</span><span class="sxs-lookup"><span data-stu-id="7ca6e-136">Rendering the motion controller model in Unity</span></span>

<span data-ttu-id="7ca6e-137">![Modelo de controlador de movimento e teleportação](images/motioncontrollertest-teleport-1000px.png)</span><span class="sxs-lookup"><span data-stu-id="7ca6e-137">![Motion Controller model and teleportation](images/motioncontrollertest-teleport-1000px.png)</span></span><br>
<span data-ttu-id="7ca6e-138">*Modelo de controlador de movimento e teleportação*</span><span class="sxs-lookup"><span data-stu-id="7ca6e-138">*Motion controller model and teleportation*</span></span>

<span data-ttu-id="7ca6e-139">Para renderizar os controladores de movimento em seu aplicativo que correspondam aos controladores físicos que os usuários estão mantendo e articulados conforme vários botões são pressionados, você pode usar o **MotionController pré-fabricado** no [Kit de ferramentas da realidade misturada](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span><span class="sxs-lookup"><span data-stu-id="7ca6e-139">To render motion controllers in your app that match the physical controllers your users are holding and articulate as various buttons are pressed, you can use the **MotionController prefab** in the [Mixed Reality Toolkit](https://github.com/Microsoft/MixedRealityToolkit-Unity/).</span></span>  <span data-ttu-id="7ca6e-140">Esse pré-fabricado dinamicamente carrega o modelo de glTF correto em tempo de execução do driver do controlador de movimento instalado do sistema.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-140">This prefab dynamically loads the correct glTF model at runtime from the system's installed motion controller driver.</span></span>  <span data-ttu-id="7ca6e-141">É importante carregar esses modelos dinamicamente, em vez de importá-los manualmente no editor, para que seu aplicativo mostre modelos 3D fisicamente precisos para todos os controladores atuais e futuros que seus usuários possam ter.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-141">It's important to load these models dynamically rather than importing them manually in the editor, so that your app will show physically accurate 3D models for any current and future controllers your users may have.</span></span>

1. <span data-ttu-id="7ca6e-142">Siga as instruções de [introdução](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) para baixar o kit de ferramentas de realidade misturada e adicioná-lo ao seu projeto do Unity.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-142">Follow the [Getting Started](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/GettingStarted.md) instructions to download the Mixed Reality Toolkit and add it to your Unity project.</span></span>
2. <span data-ttu-id="7ca6e-143">Se você substituiu a câmera pelo *MixedRealityCameraParent* pré-fabricado como parte das etapas introdução, está pronto!</span><span class="sxs-lookup"><span data-stu-id="7ca6e-143">If you replaced your camera with the *MixedRealityCameraParent* prefab as part of the Getting Started steps, you're good to go!</span></span>  <span data-ttu-id="7ca6e-144">Esse pré-fabricado inclui a renderização do controlador de movimento.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-144">That prefab includes motion controller rendering.</span></span>  <span data-ttu-id="7ca6e-145">Caso contrário, adicione *assets/HoloToolkit/Input/pré-fabricados/MotionControllers. pré-fabricado* à sua cena no painel do projeto.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-145">Otherwise, add *Assets/HoloToolkit/Input/Prefabs/MotionControllers.prefab* into your scene from the Project pane.</span></span>  <span data-ttu-id="7ca6e-146">Você desejará adicionar esse pré-fabricado como um filho de qualquer objeto pai usado para mover a câmera quando o usuário estiver em sua cena, para que os controladores acompanhem o usuário.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-146">You'll want to add that prefab as a child of whatever parent object you use to move the camera around when the user teleports within your scene, so that the controllers come along with the user.</span></span>  <span data-ttu-id="7ca6e-147">Se seu aplicativo não envolver a teleportabilidade, basta adicionar o pré-fabricado na raiz da sua cena.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-147">If your app doesn't involve teleporting, just add the prefab at the root of your scene.</span></span>

## <a name="throwing-objects"></a><span data-ttu-id="7ca6e-148">Lançando objetos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-148">Throwing objects</span></span>

<span data-ttu-id="7ca6e-149">Lançar objetos na realidade virtual é um problema mais difícil do que parece, na primeira vez.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-149">Throwing objects in virtual reality is a harder problem than it may at first seem.</span></span> <span data-ttu-id="7ca6e-150">Assim como acontece com a maioria das interações com base fisicamente, quando o jogo atua de forma inesperada, ele é imediatamente óbvio e quebra imersão.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-150">As with most physically based interactions, when throwing in game acts in an unexpected way, it's immediately obvious and breaks immersion.</span></span> <span data-ttu-id="7ca6e-151">Já gastamos algum tempo pensando em como representar um comportamento de lançamento fisicamente correto e apresentamos algumas diretrizes, habilitadas por meio de atualizações em nossa plataforma, que gostaríamos de compartilhar com você.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-151">We've spent some time thinking deeply about how to represent a physically correct throwing behavior, and have come up with a few guidelines, enabled through updates to our platform, that we would like to share with you.</span></span>

<span data-ttu-id="7ca6e-152">Você pode encontrar um exemplo de como é recomendável implementar o lançamento [aqui](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span><span class="sxs-lookup"><span data-stu-id="7ca6e-152">You can find an example of how we recommend to implement throwing [here](https://github.com/keluecke/MixedRealityToolkit-Unity/blob/master/External/Unitypackages/ThrowingStarter.unitypackage).</span></span> <span data-ttu-id="7ca6e-153">Este exemplo segue estas quatro diretrizes:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-153">This sample follows these four guidelines:</span></span>
* <span data-ttu-id="7ca6e-154">**Use a *velocidade* do controlador em vez da posição**.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-154">**Use the controller’s *velocity* instead of position**.</span></span> <span data-ttu-id="7ca6e-155">Na atualização de novembro do Windows, apresentamos uma alteração no comportamento no estado de [controle posicional ' ' aproximado](../../design/motion-controllers.md#controller-tracking-state)'.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-155">In the November update to Windows, we introduced a change in behavior when in the [''Approximate'' positional tracking state](../../design/motion-controllers.md#controller-tracking-state).</span></span> <span data-ttu-id="7ca6e-156">Quando nesse estado, as informações de velocidade sobre o controlador continuarão sendo relatadas pelo tempo que acreditarem em sua precisão alta, o que geralmente é maior que a posição permanece com alta precisão.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-156">When in this state, velocity information about the controller will continue to be reported for as long as we believe its high accuracy, which is often longer than position remains high accuracy.</span></span>
* <span data-ttu-id="7ca6e-157">**Incorpore a *velocidade angular* do controlador**.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-157">**Incorporate the *angular velocity* of the controller**.</span></span> <span data-ttu-id="7ca6e-158">Essa lógica está todas contidas no `throwing.cs` arquivo no `GetThrownObjectVelAngVel` método estático, dentro do pacote vinculado acima:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-158">This logic is all contained in the `throwing.cs` file in the `GetThrownObjectVelAngVel` static method, within the package linked above:</span></span>
   1. <span data-ttu-id="7ca6e-159">À medida que a velocidade angular é conservada, o objeto gerado deve manter a mesma velocidade angular que tinha no momento do lançamento: `objectAngularVelocity = throwingControllerAngularVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7ca6e-159">As angular velocity is conserved, the thrown object must maintain the same angular velocity as it had at the moment of the throw: `objectAngularVelocity = throwingControllerAngularVelocity;`</span></span>
   2. <span data-ttu-id="7ca6e-160">Como o centro da massa do objeto gerado provavelmente não está na origem da pose de alça, ele provavelmente tem uma velocidade diferente daquela do controlador no quadro de referência do usuário.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-160">As the center of mass of the thrown object is likely not at the origin of the grip pose, it likely has a different velocity than that of the controller in the frame of reference of the user.</span></span> <span data-ttu-id="7ca6e-161">A parte da velocidade do objeto que contribuiu dessa forma é a velocidade tangential instantânea do centro da massa do objeto gerado em relação à origem do controlador.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-161">The portion of the object’s velocity contributed in this way is the instantaneous tangential velocity of the center of mass of the thrown object around the controller origin.</span></span> <span data-ttu-id="7ca6e-162">Essa velocidade de tangential é o produto cruzado da velocidade angular do controlador com o vetor que representa a distância entre a origem do controlador e o centro da massa do objeto gerado.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-162">This tangential velocity is the cross product of the angular velocity of the controller with the vector representing the distance between the controller origin and the center of mass of the thrown object.</span></span>

      ```cs
      Vector3 radialVec = thrownObjectCenterOfMass - throwingControllerPos;
      Vector3 tangentialVelocity = Vector3.Cross(throwingControllerAngularVelocity, radialVec);
      ```

   3. <span data-ttu-id="7ca6e-163">A velocidade total do objeto gerado é a soma da velocidade do controlador e dessa velocidade de tangential: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span><span class="sxs-lookup"><span data-stu-id="7ca6e-163">The total velocity of the thrown object is the sum of velocity of the controller and this tangential velocity: `objectVelocity = throwingControllerVelocity + tangentialVelocity;`</span></span>

* <span data-ttu-id="7ca6e-164">**Preste muita atenção à *hora* em que aplicamos a velocidade**.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-164">**Pay close attention to the *time* at which we apply the velocity**.</span></span> <span data-ttu-id="7ca6e-165">Quando um botão é pressionado, pode levar até 20 ms para que esse evento seja emergido por meio do Bluetooth para o sistema operacional.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-165">When a button is pressed, it can take up to 20 ms for that event to bubble up through Bluetooth to the operating system.</span></span> <span data-ttu-id="7ca6e-166">Isso significa que, se você sondar uma alteração de estado do controlador de pressionado para não pressionado ou o contrário, o controlador apresentará as informações que você obtém com ele, na verdade, estará à frente dessa alteração no estado.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-166">This means that if you poll for a controller state change from pressed to not pressed or the other way around, the controller pose information you get with it will actually be ahead of this change in state.</span></span> <span data-ttu-id="7ca6e-167">Além disso, a pose do controlador apresentada por nossa API de sondagem está prevista para refletir uma causa provável no momento em que o quadro será exibido, o que poderia ser mais de 20 ms no futuro.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-167">Further, the controller pose presented by our polling API is forward predicted to reflect a likely pose at the time the frame will be displayed which could be more than 20 ms in the future.</span></span> <span data-ttu-id="7ca6e-168">Isso é bom para *renderizar* objetos mantidos, mas aumenta nosso problema de tempo para *direcionar* o objeto à medida que calculamos a trajetória para o momento em que o usuário lançou o lançamento.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-168">This is good for *rendering* held objects, but compounds our time problem for *targeting* the object as we calculate the trajectory for the moment the user released the throw.</span></span> <span data-ttu-id="7ca6e-169">Felizmente, com a atualização de novembro, quando um evento do Unity como *InteractionSourcePressed* ou *InteractionSourceReleased* é enviado, o estado inclui os dados históricos de back quando o botão foi pressionado ou liberado.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-169">Fortunately, with the November update, when a Unity event like *InteractionSourcePressed* or *InteractionSourceReleased* is sent, the state includes the historical pose data from back when the button was pressed or released.</span></span>  <span data-ttu-id="7ca6e-170">Para obter a renderização de controlador e o direcionamento de controlador mais precisos durante as jogadas, você deve usar corretamente a sondagem e o evento, conforme apropriado:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-170">To get the most accurate controller rendering and controller targeting during throws, you must correctly use polling and eventing, as appropriate:</span></span>
   * <span data-ttu-id="7ca6e-171">Para **renderizar** cada quadro do controlador, seu aplicativo deve posicionar o *gameobject* do controlador no controlador previsto para o momento da Photon do quadro atual.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-171">For **controller rendering** each frame, your app should position the controller's *GameObject* at the forward-predicted controller pose for the current frame’s photon time.</span></span>  <span data-ttu-id="7ca6e-172">Você obtém esses dados de APIs de sondagem do Unity como a *[XR. InputTracking. GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* ou *[XR. WSA. Entrada. interactionmanager. GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-172">You get this data from Unity polling APIs like *[XR.InputTracking.GetLocalPosition](https://docs.unity3d.com/ScriptReference/XR.InputTracking.GetLocalPosition.html)* or *[XR.WSA.Input.InteractionManager.GetCurrentReading](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.GetCurrentReading.html)*.</span></span>
   * <span data-ttu-id="7ca6e-173">Para **direcionamento de controlador** em uma prensa ou liberação, seu aplicativo deve Raycast e calcular as trajetórias com base na pose do controlador histórico para esse evento de Press ou Release.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-173">For **controller targeting** upon a press or release, your app should raycast and calculate trajectories based on the historical controller pose for that press or release event.</span></span>  <span data-ttu-id="7ca6e-174">Você obtém esses dados das APIs de eventos do Unity, como *[interactionmanager. InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-174">You get this data from Unity eventing APIs, like *[InteractionManager.InteractionSourcePressed](https://docs.unity3d.com/ScriptReference/XR.WSA.Input.InteractionManager.InteractionSourcePressed.html)*.</span></span>
* <span data-ttu-id="7ca6e-175">**Use a pose de alça**.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-175">**Use the grip pose**.</span></span> <span data-ttu-id="7ca6e-176">A velocidade angular e a velocidade são relatadas em relação à pose de alça, não à pose de ponteiro.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-176">Angular velocity and velocity are reported relative to the grip pose, not pointer pose.</span></span>

<span data-ttu-id="7ca6e-177">O lançamento continuará a melhorar com futuras atualizações do Windows e você poderá esperar mais informações sobre ela aqui.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-177">Throwing will continue to improve with future Windows updates, and you can expect to find more information on it here.</span></span>

## <a name="gesture-and-motion-controllers-in-mrtk"></a><span data-ttu-id="7ca6e-178">Controladores de gesto e movimento no MRTK</span><span class="sxs-lookup"><span data-stu-id="7ca6e-178">Gesture and Motion Controllers in MRTK</span></span>

<span data-ttu-id="7ca6e-179">Você pode acessar o gesto e o controlador de movimento do Gerenciador de entrada.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-179">You can access gesture and motion controller from the input Manager.</span></span>

* [<span data-ttu-id="7ca6e-180">Gesto em MRTK</span><span class="sxs-lookup"><span data-stu-id="7ca6e-180">Gesture in MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/gestures)
* [<span data-ttu-id="7ca6e-181">Controlador de movimento no MRTK</span><span class="sxs-lookup"><span data-stu-id="7ca6e-181">Motion Controller in MRTK</span></span>](https://docs.microsoft.com/windows/mixed-reality/mrtk-unity/features/input/controllers)

## <a name="follow-along-with-tutorials"></a><span data-ttu-id="7ca6e-182">Acompanhe com tutoriais</span><span class="sxs-lookup"><span data-stu-id="7ca6e-182">Follow along with tutorials</span></span>

<span data-ttu-id="7ca6e-183">Os tutoriais passo a passo, com exemplos de personalização mais detalhados, estão disponíveis na Academia de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-183">Step-by-step tutorials, with more detailed customization examples, are available in the Mixed Reality Academy:</span></span>

- [<span data-ttu-id="7ca6e-184">Entrada do MR 211: gesto</span><span class="sxs-lookup"><span data-stu-id="7ca6e-184">MR Input 211: Gesture</span></span>](tutorials/holograms-211.md)
- [<span data-ttu-id="7ca6e-185">Entrada do MR 213: controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-185">MR Input 213: Motion controllers</span></span>](../../deprecated/mixed-reality-213.md)

<span data-ttu-id="7ca6e-186">[![Entrada MR 213-controlador de movimento](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span><span class="sxs-lookup"><span data-stu-id="7ca6e-186">[![MR Input 213 - Motion controller](images/mr213-main-600px.jpg)](/windows/mixed-reality/mixed-reality-213)</span></span><br>
<span data-ttu-id="7ca6e-187">*Entrada MR 213-controlador de movimento*</span><span class="sxs-lookup"><span data-stu-id="7ca6e-187">*MR Input 213 - Motion controller*</span></span>

## <a name="next-development-checkpoint"></a><span data-ttu-id="7ca6e-188">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="7ca6e-188">Next Development Checkpoint</span></span>

<span data-ttu-id="7ca6e-189">Se você estiver seguindo a jornada de desenvolvimento do Unity que apresentamos, você está no meio da exploração dos blocos de construção do MRTK Core.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-189">If you're following the Unity development journey we've laid out, you're in the midst of exploring the MRTK core building blocks.</span></span> <span data-ttu-id="7ca6e-190">Deste ponto, você pode prosseguir para o próximo bloco de construção:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-190">From here, you can continue to the next building block:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ca6e-191">Acompanhamento de mãos e olhos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-191">Hand and eye tracking</span></span>](./hand-eye-in-unity.md)

<span data-ttu-id="7ca6e-192">Ou vá diretamente para as funcionalidades e APIs da plataforma de Realidade Misturada:</span><span class="sxs-lookup"><span data-stu-id="7ca6e-192">Or jump to Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7ca6e-193">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="7ca6e-193">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="7ca6e-194">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="7ca6e-194">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ca6e-195">Veja também</span><span class="sxs-lookup"><span data-stu-id="7ca6e-195">See also</span></span>

* [<span data-ttu-id="7ca6e-196">Focar com a cabeça e confirmar</span><span class="sxs-lookup"><span data-stu-id="7ca6e-196">Head-gaze and commit</span></span>](../../design/gaze-and-commit.md)
* [<span data-ttu-id="7ca6e-197">Controladores de movimentos</span><span class="sxs-lookup"><span data-stu-id="7ca6e-197">Motion controllers</span></span>](../../design/motion-controllers.md)