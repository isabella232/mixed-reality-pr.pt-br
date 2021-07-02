---
title: Calibragem ocular
description: Como configurar a calibragem ocular do usuário no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK, EyeTracking, Calibragem,
ms.openlocfilehash: a2023a2d7f6a0254e8fef32f4faf09def956e94f
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177206"
---
# <a name="eye-calibration"></a><span data-ttu-id="a77ba-104">Calibragem ocular</span><span class="sxs-lookup"><span data-stu-id="a77ba-104">Eye calibration</span></span>

![Captura de tela da notificação de calibragem ocular](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a><span data-ttu-id="a77ba-106">Visão geral</span><span class="sxs-lookup"><span data-stu-id="a77ba-106">Overview</span></span>

<span data-ttu-id="a77ba-107">Se o acompanhamento ocular for uma parte fundamental da sua experiência de aplicativo, talvez seja melhor garantir que a calibragem ocular do usuário seja válida.</span><span class="sxs-lookup"><span data-stu-id="a77ba-107">If eye tracking is a fundamental part of your app experience, one may wish to ensure that the user's eye calibration is valid.</span></span>
<span data-ttu-id="a77ba-108">O principal motivo para ele ser inválido é que o usuário optou por ignorar a calibragem de acompanhamento ocular ao colocar no dispositivo.</span><span class="sxs-lookup"><span data-stu-id="a77ba-108">The main reason for it to be invalid is that the user has chosen to skip the eye tracking calibration when putting on the device.</span></span>

<span data-ttu-id="a77ba-109">Esta página aborda o seguinte:</span><span class="sxs-lookup"><span data-stu-id="a77ba-109">This page covers the following:</span></span>

- <span data-ttu-id="a77ba-110">Descreve como detectar que um usuário está calibrado com o olhar</span><span class="sxs-lookup"><span data-stu-id="a77ba-110">Describes how to detect that a user is eye calibrated</span></span>
- <span data-ttu-id="a77ba-111">Fornece um exemplo de como disparar uma notificação de usuário para instruir o usuário a passar pela calibragem ocular</span><span class="sxs-lookup"><span data-stu-id="a77ba-111">Provides a sample for how to trigger a user notification to instruct the user to go through the eye calibration</span></span>
  - <span data-ttu-id="a77ba-112">Descartar automaticamente a notificação se a calibragem ocular se tornar válida</span><span class="sxs-lookup"><span data-stu-id="a77ba-112">Automatically dismiss notification if eye calibration becomes valid</span></span>
  - <span data-ttu-id="a77ba-113">Descartar manualmente a notificação se o usuário optar por continuar sem calibragem</span><span class="sxs-lookup"><span data-stu-id="a77ba-113">Manually dismiss notification if user chooses to continue without calibration</span></span>

### <a name="how-to-detect-the-eye-calibration-state"></a><span data-ttu-id="a77ba-114">Como detectar o estado de calibragem ocular</span><span class="sxs-lookup"><span data-stu-id="a77ba-114">How to detect the eye calibration state</span></span>

<span data-ttu-id="a77ba-115">A configuração de acompanhamento ocular no MRTK é configurada por meio da [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface .</span><span class="sxs-lookup"><span data-stu-id="a77ba-115">Eye tracking configuration in MRTK is configured via the [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.</span></span>

<span data-ttu-id="a77ba-116">O [uso de CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fornece a implementação padrão do provedor de gaze registrada no kit de ferramentas em runtime.</span><span class="sxs-lookup"><span data-stu-id="a77ba-116">Using [CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) provides the default gaze provider implementation registered in the toolkit at runtime.</span></span> <span data-ttu-id="a77ba-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` retornará `bool?` um que será nulo se nenhuma informação do rastreador ocular ainda estiver disponível.</span><span class="sxs-lookup"><span data-stu-id="a77ba-117">`IMixedRealityEyeGazeProvider.IsEyeGazeValid` returns a `bool?` which is null if no information from the eye tracker is available yet.</span></span>
<span data-ttu-id="a77ba-118">Depois que os dados foram recebidos, eles retornarão true ou false para indicar que a calibragem de acompanhamento ocular do usuário é válida ou inválida.</span><span class="sxs-lookup"><span data-stu-id="a77ba-118">Once data has been received, it will either return true or false to indicate that the user's eye tracking calibration is valid or invalid.</span></span>

### <a name="sample-eye-calibration-notification---step-by-step"></a><span data-ttu-id="a77ba-119">Notificação de calibragem ocular de exemplo – passo a passo</span><span class="sxs-lookup"><span data-stu-id="a77ba-119">Sample eye calibration notification - step-by-step</span></span>

1. <span data-ttu-id="a77ba-120">Abra o pacote de exemplo de acompanhamento ocular do MRTK (Ativos/MRTK/Exemplos/Demonstrações/EyeTracking)</span><span class="sxs-lookup"><span data-stu-id="a77ba-120">Open the MRTK eye tracking example package (Assets/MRTK/Examples/Demos/EyeTracking)</span></span>

2. <span data-ttu-id="a77ba-121">Carregar _a cena EyeTrackingDemo-00-RootScene.unity_</span><span class="sxs-lookup"><span data-stu-id="a77ba-121">Load _EyeTrackingDemo-00-RootScene.unity_ scene</span></span>

3. <span data-ttu-id="a77ba-122">Confira _EyeCalibrationChecker:_</span><span class="sxs-lookup"><span data-stu-id="a77ba-122">Check out _EyeCalibrationChecker_:</span></span>
   - <span data-ttu-id="a77ba-123">Nesta cena, já temos um exemplo para detectar se o usuário atual está calibrado no objeto de jogo *_EyeCalibrationChecker_*.</span><span class="sxs-lookup"><span data-stu-id="a77ba-123">In this scene, we have already a sample for detecting whether the current user is calibrated under the *_EyeCalibrationChecker_ game object*.</span></span>
<span data-ttu-id="a77ba-124">Ele simplesmente é pai de algumas malhas de texto e tem alguns gatilhos adicionais para mesclar a notificação dentro e fora. Isso inclui aumentar lentamente seu tamanho e opacidade na ativação.</span><span class="sxs-lookup"><span data-stu-id="a77ba-124">It simply parents a few text meshes and has some additional triggers for blending the notification in and out. This includes slowly increasing its size and opacity on activation.</span></span>
<span data-ttu-id="a77ba-125">Depois que a notificação for descartada, ela diminuirá lentamente seu tamanho e esmaecerá.</span><span class="sxs-lookup"><span data-stu-id="a77ba-125">Once the notification is dismissed, it will slowly decrease its size and fade out.</span></span>

   - <span data-ttu-id="a77ba-126">Anexado ao objeto *_de jogo EyeCalibrationChecker_* está o script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) que expõe dois Eventos do Unity:</span><span class="sxs-lookup"><span data-stu-id="a77ba-126">Attached to the *_EyeCalibrationChecker_ game object* is the [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) script which exposes two Unity Events:</span></span>
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - <span data-ttu-id="a77ba-127">Esses eventos serão disparados somente se o status de calibragem mudar.</span><span class="sxs-lookup"><span data-stu-id="a77ba-127">These events will only trigger if the calibration status changes.</span></span> <span data-ttu-id="a77ba-128">Portanto, se um usuário optar por descartar a notificação, a notificação não será novamente até</span><span class="sxs-lookup"><span data-stu-id="a77ba-128">Hence, if a user chooses to dismiss the notification, the notification will not show up again until</span></span>
      - <span data-ttu-id="a77ba-129">O aplicativo é reiniciado</span><span class="sxs-lookup"><span data-stu-id="a77ba-129">The app gets restarted</span></span>
      - <span data-ttu-id="a77ba-130">Um usuário válido foi detectado e, em seguida, um novo usuário descalibrado colocou o dispositivo</span><span class="sxs-lookup"><span data-stu-id="a77ba-130">A valid user has been detected and then a new uncalibrated user has put the device on</span></span>

   - <span data-ttu-id="a77ba-131">Para testar se as animações e eventos são disparados corretamente, o script EyeCalibrationChecker possui um `bool editorTestUserIsCalibrated` sinalizador.</span><span class="sxs-lookup"><span data-stu-id="a77ba-131">For testing whether the animations and events are triggered correctly, the EyeCalibrationChecker script possesses a `bool editorTestUserIsCalibrated` flag.</span></span> <span data-ttu-id="a77ba-132">Por exemplo, ao executar no Editor do Unity, é possível testar:</span><span class="sxs-lookup"><span data-stu-id="a77ba-132">For example, when running in the Unity Editor, one can test:</span></span>
      1. <span data-ttu-id="a77ba-133">Se a notificação é automaticamente pop-up depois que o status de calibragem muda de true para false</span><span class="sxs-lookup"><span data-stu-id="a77ba-133">Whether the notification automatically pops up once the calibration status changes from true to false</span></span>
      1. <span data-ttu-id="a77ba-134">Se ela descarta automaticamente a notificação novamente depois que o status muda de false para true.</span><span class="sxs-lookup"><span data-stu-id="a77ba-134">Whether it automatically dismisses the notification again once the status changes from false to true.</span></span>

```c#
    private bool? prevCalibrationStatus = null;
    ...

   void Update()
   {
      // Get the latest calibration state from the EyeGazeProvider
      bool? calibrationStatus = CoreServices.InputSystem?.EyeGazeProvider?.IsEyeCalibrationValid;

      ...

      if (calibrationStatus != null)
      {
         if (prevCalibrationStatus != calibrationStatus)
         {
            if (calibrationStatus == false)
            {
               OnNoEyeCalibrationDetected.Invoke();
            }
         else
         {
            OnEyeCalibrationDetected.Invoke();
         }

         prevCalibrationStatus = calibrationStatus;
      }
   }
```

## <a name="see-also"></a><span data-ttu-id="a77ba-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="a77ba-135">See also</span></span>

- [<span data-ttu-id="a77ba-136">Visão geral do acompanhamento ocular do MRTK</span><span class="sxs-lookup"><span data-stu-id="a77ba-136">MRTK Eye Tracking Overview</span></span>](eye-tracking-main.md)
- [<span data-ttu-id="a77ba-137">Configuração do Acompanhamento Ocular do MRTK</span><span class="sxs-lookup"><span data-stu-id="a77ba-137">MRTK Eye Tracking setup</span></span>](eye-tracking-basic-setup.md)
- [<span data-ttu-id="a77ba-138">Acompanhamento ocular do MRTK por meio de código</span><span class="sxs-lookup"><span data-stu-id="a77ba-138">MRTK Eye Tracking via Code</span></span>](eye-tracking-eye-gaze-provider.md)
- [<span data-ttu-id="a77ba-139">HoloLens documentação de acompanhamento ocular do HoloLens 2</span><span class="sxs-lookup"><span data-stu-id="a77ba-139">HoloLens 2 Eye Tracking Documentation</span></span>](/windows/mixed-reality/eye-tracking)
