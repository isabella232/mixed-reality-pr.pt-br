---
title: Ditado
description: Docummentation sobre como gravar clipes de áudio e obter uma transcrição no MRTK
author: keveleigh
ms.author: kurtie
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 14061197031282dcc9dd20a141101b65ee92ca2376bdc009fa8790076681a970
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219988"
---
# <a name="dictation"></a>Ditado

O ditado permite que os usuários gravem clipes de áudio e obtenham uma transcrição. Para usá-lo, verifique se um sistema de ditado está registrado no *perfil do sistema de entrada*. **Windows provedor de entrada de ditado** é o sistema de ditado fornecido pronta para uso, mas sistemas de ditados alternativos podem ser criados com a implementação [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .

## <a name="requirements"></a>Requisitos

o sistema de ditado usa o [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) do Unity que usa as APIs de fala de Windows subjacentes para manipular o ditado. observe que isso implica que esse recurso está presente apenas em plataformas baseadas em Windows.

O uso do sistema de ditado requer os recursos de aplicativo "cliente de Internet" e "microfone" na [seção PlayerSettings-Capabilities](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).
consulte a [documentação Windows Mixed Reality](/windows/mixed-reality/voice-input-in-unity#dictation) para obter mais detalhes sobre a entrada de voz no Unity.

## <a name="configuration"></a>Configuração

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

Depois de ter um serviço de ditado configurado, você pode usar o [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script para iniciar e parar de gravar sessões e obter os resultados da transcrição por meio de UnityEvents.

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- A **hipótese de ditado** é gerada conforme o usuário fala com as transcrições preliminares do áudio capturado até agora.
- O **resultado do ditado** é gerado no final de cada sentença (ou seja, quando o usuário pausa) com a transcrição final do áudio capturada até o momento.
- O **ditado concluído** é gerado no final da sessão de gravação com a transcrição completa e final do áudio.
- O **erro de ditado** é gerado para informar erros no serviço de ditado. A transcrição, nesse caso, contém uma descrição do erro.

## <a name="example-scene"></a>Cena de exemplo

A cena do **ditado** em `MRTK/Examples/Demos/Input/Scenes/Dictation` mostra o `DictationHandler` script em uso. Se precisar de mais controle, você pode estender esse script ou criar sua própria implementação [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) para receber eventos de ditado diretamente.

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
