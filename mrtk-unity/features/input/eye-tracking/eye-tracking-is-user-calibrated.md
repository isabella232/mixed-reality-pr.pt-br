---
title: Calibragem de olho
description: Como configurar a calibragem de olho do usuário no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, EyeTracking, calibração,
ms.openlocfilehash: d7ae9885b77798b44b3d63bb7f92283658e05411
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144000"
---
# <a name="eye-calibration"></a>Calibragem de olho

![Captura de tela da notificação de calibragem de olho](../../images/eye-tracking/mrtk_et_calibration_notification_example.jpg)

## <a name="overview"></a>Visão geral

Se o acompanhamento dos olhos for uma parte fundamental da sua experiência com o aplicativo, talvez você queira garantir que a calibragem de olho do usuário seja válida.
O principal motivo para ser inválido é que o usuário optou por ignorar a calibragem de acompanhamento ocular ao colocar no dispositivo.

Esta página aborda o seguinte:

- Descreve como detectar que um usuário está com os olhos calibrados
- Fornece um exemplo de como disparar uma notificação de usuário para instruir o usuário a percorrer a calibragem de olho
  - Ignorar automaticamente a notificação se a calibragem de olho se tornar válida
  - Ignorar manualmente a notificação se o usuário optar por continuar sem a calibragem

### <a name="how-to-detect-the-eye-calibration-state"></a>Como detectar o estado de calibragem de olho

A configuração de acompanhamento de olho no MRTK é configurada por meio da [`IMixedRealityEyeGazeProvider`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityEyeGazeProvider) interface.

O uso de [CoreServices. InputSystem. EyeGazeProvider](eye-tracking-eye-gaze-provider.md) fornece a implementação padrão do provedor olhar registrada no kit de ferramentas em tempo de execução. `IMixedRealityEyeGazeProvider.IsEyeGazeValid` Retorna um `bool?` valor nulo se nenhuma informação do rastreador ocular ainda estiver disponível.
Depois que os dados forem recebidos, eles retornarão true ou false para indicar que a calibragem de controle ocular do usuário é válida ou inválida.

### <a name="sample-eye-calibration-notification---step-by-step"></a>Notificação de calibragem de olho de exemplo – passo a passo

1. Abra o pacote de exemplo de acompanhamento de olho do MRTK (ativos/MRTK/exemplos/demos/EyeTracking)

2. Carregar _EyeTrackingDemo-00-RootScene. Unity_ sceneling

3. Confira _EyeCalibrationChecker_:
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
- [Documentação de acompanhamento ocular do HoloLens 2](/windows/mixed-reality/eye-tracking)