---
title: Provedores de entrada
description: Documentação sobre diferentes tipos de provedores de entrada no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: ad4a643d0fb46cdb15cee3c37edaffb4f51ed44b
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145267"
---
# <a name="input-providers"></a>Provedores de entrada

Os provedores de entrada são registrados no **Perfil de Provedores de Serviços Registrados**, encontrado no componente Kit de Ferramentas de Realidade Misturada:

<img src="../images/input/RegisteredServiceProviders.PNG" width="650px" style="display:block;" alt="Service providers">

Esses são os provedores de entrada disponíveis imediatamente, juntamente com seus controladores correspondentes:

| Provedor de Entrada | Controladores |
| --- | --- |
| [`Input Simulation Service`](xref:Microsoft.MixedReality.Toolkit.Input.InputSimulationService) | Mão simulada |
| [`Mouse Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.MouseDeviceManager) | Mouse  |
| [`OpenVR Device Manager`](xref:Microsoft.MixedReality.Toolkit.OpenVR.Input.OpenVRDeviceManager) | Generic OpenVR, Vive Ltd, Vive Então, Oculus Touch, Oculus Remote, Windows Mixed Reality OpenVR  |
| [`Unity Joystick Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityJoystickManager) | Generic Joystick  |
| [`Unity Touch Device Manager`](xref:Microsoft.MixedReality.Toolkit.Input.UnityInput.UnityTouchDeviceManager) | Controlador de toque do Unity  |
| [`Windows Dictation Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsDictationInputProvider) | *Nenhuma*  |
| [`Windows Mixed Reality Device Manager`](xref:Microsoft.MixedReality.Toolkit.WindowsMixedReality.Input.WindowsMixedRealityDeviceManager) | Mão articulada wmr, controlador WMR, wmr GGV (olhar, gesto e voz) mão |
| [`Windows Speech Input Provider`](xref:Microsoft.MixedReality.Toolkit.Windows.Input.WindowsSpeechInputProvider) | *Nenhuma* |

Os provedores de Ditado e Fala não criam controladores, eles geram seus próprios eventos de entrada especializados diretamente.

Provedores de entrada personalizados podem ser criados implementando a [`IMixedRealityInputDeviceManager`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityInputDeviceManager) interface .

Para obter mais informações, consulte [criando um provedor de dados do sistema de entrada](create-data-provider.md).
