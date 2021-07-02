---
title: Ditado
description: Docummentação sobre como gravar clipes de áudio e obter uma transcrição no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 520a667cc4b41f5e8f4373a7c901eb2458cd2d17
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176475"
---
# <a name="dictation"></a>Ditado

Ditado permite que os usuários gravem clipes de áudio e obtenham uma transcrição. Para usá-lo, certifique-se de que um sistema de ditado esteja registrado no *Perfil do Sistema de Entrada*. **Windows provedor de entrada** de ditado é o sistema de ditado fornecido de forma inoportuna, mas sistemas de ditado alternativos podem ser criados implementando [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .

## <a name="requirements"></a>Requisitos

O sistema de ditado usa [o DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) do Unity, que usa as APIs de fala Windows subjacentes para lidar com ditado. Observe que isso implica que esse recurso está presente apenas em plataformas Windows baseadas em dados.

O uso do sistema de ditado requer as funcionalidades de aplicativo "Cliente da Internet" e "Microfone" na [seção PlayerSettings – Recursos](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).
Confira [Windows Mixed Reality documentação para](/windows/mixed-reality/voice-input-in-unity#dictation) obter mais detalhes sobre a entrada de voz no Unity.

## <a name="configuration"></a>Configuração

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

Depois de configurar um serviço de ditado, você pode usar o script para iniciar e parar as sessões de gravação e obter os resultados da transcrição por meio do [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) UnityEvents.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- **A Hipótese de Ditado é** acionado à medida que o usuário fala com transcrições antecipadas e aproximadas do áudio capturado até o momento.
- **O resultado do ditado** é gerado no final de cada frase (ou seja, quando o usuário pausa) com a transcrição final do áudio capturado até o momento.
- **O ditado Concluído é** gerado no final da sessão de gravação com a transcrição completa e final do áudio.
- **O erro de ditado** é gerado para informar erros no serviço de ditado. A transcrição nesse caso contém uma descrição do erro.

## <a name="example-scene"></a>Cena de exemplo

**A cena de** ditado em `MRTK/Examples/Demos/Input/Scenes/Dictation` mostra o script em `DictationHandler` uso. Se precisar de mais controle, você poderá estender esse script ou criar seu próprio implementando para [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) receber eventos de ditado diretamente.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
