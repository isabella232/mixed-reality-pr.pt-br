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
# <a name="eye-calibration"></a>Calibragem ocular

![Captura de tela da notificação de calibragem ocular](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Visão geral

Se o acompanhamento ocular for uma parte fundamental da sua experiência de aplicativo, talvez seja melhor garantir que a calibragem ocular do usuário seja válida.
O principal motivo para ele ser inválido é que o usuário optou por ignorar a calibragem de acompanhamento ocular ao colocar no dispositivo.

Esta página aborda o seguinte:

- Descreve como detectar que um usuário está calibrado com o olhar
- Fornece um exemplo de como disparar uma notificação de usuário para instruir o usuário a passar pela calibragem ocular
  - Descartar automaticamente a notificação se a calibragem ocular se tornar válida
  - Descartar manualmente a notificação se o usuário optar por continuar sem calibragem

### <a name="how-to-detect-the-eye-calibration-state"></a>Como detectar o estado de calibragem ocular

A configuração de acompanhamento ocular no MRTK é configurada por meio da [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface .

O [uso de CoreServices.InputSystem.EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fornece a implementação padrão do provedor de gaze registrada no kit de ferramentas em runtime. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` retornará `bool?` um que será nulo se nenhuma informação do rastreador ocular ainda estiver disponível.
Depois que os dados foram recebidos, eles retornarão true ou false para indicar que a calibragem de acompanhamento ocular do usuário é válida ou inválida.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Notificação de calibragem ocular de exemplo – passo a passo

1. Abra o pacote de exemplo de acompanhamento ocular do MRTK (Ativos/MRTK/Exemplos/Demonstrações/EyeTracking)

2. Carregar _a cena EyeTrackingDemo-00-RootScene.unity_

3. Confira _EyeCalibrationChecker:_
   - Nesta cena, já temos um exemplo para detectar se o usuário atual está calibrado no objeto de jogo *_EyeCalibrationChecker_*.
Ele simplesmente é pai de algumas malhas de texto e tem alguns gatilhos adicionais para mesclar a notificação dentro e fora. Isso inclui aumentar lentamente seu tamanho e opacidade na ativação.
Depois que a notificação for descartada, ela diminuirá lentamente seu tamanho e esmaecerá.

   - Anexado ao objeto *_de jogo EyeCalibrationChecker_* está o script [EyeCalibrationChecker](xref:Microsoft.MixedReality.Toolkit.Examples.Demos.EyeTracking.EyeCalibrationChecker) que expõe dois Eventos do Unity:
      - `OnEyeCalibrationDetected()`
      - `OnNoEyeCalibrationDetected()`

   - Esses eventos serão disparados somente se o status de calibragem mudar. Portanto, se um usuário optar por descartar a notificação, a notificação não será novamente até
      - O aplicativo é reiniciado
      - Um usuário válido foi detectado e, em seguida, um novo usuário descalibrado colocou o dispositivo

   - Para testar se as animações e eventos são disparados corretamente, o script EyeCalibrationChecker possui um `bool editorTestUserIsCalibrated` sinalizador. Por exemplo, ao executar no Editor do Unity, é possível testar:
      1. Se a notificação é automaticamente pop-up depois que o status de calibragem muda de true para false
      1. Se ela descarta automaticamente a notificação novamente depois que o status muda de false para true.

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

## <a name="see-also"></a>Confira também

- [Visão geral do acompanhamento ocular do MRTK](eye-tracking-main.md)
- [Configuração do Acompanhamento Ocular do MRTK](eye-tracking-basic-setup.md)
- [Acompanhamento ocular do MRTK por meio de código](eye-tracking-eye-gaze-provider.md)
- [HoloLens documentação de acompanhamento ocular do HoloLens 2](/windows/mixed-reality/eye-tracking)
