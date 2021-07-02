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
# <a name="dictation"></a><span data-ttu-id="61551-104">Ditado</span><span class="sxs-lookup"><span data-stu-id="61551-104">Dictation</span></span>

<span data-ttu-id="61551-105">Ditado permite que os usuários gravem clipes de áudio e obtenham uma transcrição.</span><span class="sxs-lookup"><span data-stu-id="61551-105">Dictation allows users to record audio clips and obtain a transcription.</span></span> <span data-ttu-id="61551-106">Para usá-lo, certifique-se de que um sistema de ditado esteja registrado no *Perfil do Sistema de Entrada*.</span><span class="sxs-lookup"><span data-stu-id="61551-106">To use it make sure that a dictation system is registered in the *Input System Profile*.</span></span> <span data-ttu-id="61551-107">**Windows provedor de entrada** de ditado é o sistema de ditado fornecido de forma inoportuna, mas sistemas de ditado alternativos podem ser criados implementando [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem) .</span><span class="sxs-lookup"><span data-stu-id="61551-107">**Windows Dictation Input Provider** is the dictation system provided out of the box but alternative dictation systems can be created implementing [`IMixedRealityDictationSystem`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationSystem).</span></span>

## <a name="requirements"></a><span data-ttu-id="61551-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="61551-108">Requirements</span></span>

<span data-ttu-id="61551-109">O sistema de ditado usa [o DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) do Unity, que usa as APIs de fala Windows subjacentes para lidar com ditado.</span><span class="sxs-lookup"><span data-stu-id="61551-109">The dictation system uses Unity's [DictationRecognizer](https://docs.unity3d.com/ScriptReference/Windows.Speech.DictationRecognizer.html) which itself uses the underlying Windows speech APIs for handling dictation.</span></span> <span data-ttu-id="61551-110">Observe que isso implica que esse recurso está presente apenas em plataformas Windows baseadas em dados.</span><span class="sxs-lookup"><span data-stu-id="61551-110">Note that this implies that this feature is only present on Windows-based platforms.</span></span>

<span data-ttu-id="61551-111">O uso do sistema de ditado requer as funcionalidades de aplicativo "Cliente da Internet" e "Microfone" na [seção PlayerSettings – Recursos](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span><span class="sxs-lookup"><span data-stu-id="61551-111">Usage of the Dictation system requires both the "Internet Client" and "Microphone" application capabilities in the [PlayerSettings - Capabilities section](https://docs.unity3d.com/Manual/class-PlayerSettingsWSA.html#Capabilities).</span></span>
<span data-ttu-id="61551-112">Confira [Windows Mixed Reality documentação para](/windows/mixed-reality/voice-input-in-unity#dictation) obter mais detalhes sobre a entrada de voz no Unity.</span><span class="sxs-lookup"><span data-stu-id="61551-112">See [Windows Mixed Reality Documentation](/windows/mixed-reality/voice-input-in-unity#dictation) for more details on voice input in Unity.</span></span>

## <a name="configuration"></a><span data-ttu-id="61551-113">Configuração</span><span class="sxs-lookup"><span data-stu-id="61551-113">Configuration</span></span>

<img src="../images/input/DictationDataProvider.png" width="80%" class="center" alt="Data provider">

<span data-ttu-id="61551-114">Depois de configurar um serviço de ditado, você pode usar o script para iniciar e parar as sessões de gravação e obter os resultados da transcrição por meio do [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) UnityEvents.</span><span class="sxs-lookup"><span data-stu-id="61551-114">Once you have a dictation service set up, you can use the [`DictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.DictationHandler) script to start and stop recording sessions and obtain the transcription results via UnityEvents.</span></span>

<img src="../images/input/DictationHandler.png" width="80%" alt="Dictation Handler" class="center">

- <span data-ttu-id="61551-115">**A Hipótese de Ditado é** acionado à medida que o usuário fala com transcrições antecipadas e aproximadas do áudio capturado até o momento.</span><span class="sxs-lookup"><span data-stu-id="61551-115">**Dictation Hypothesis** is raised as the user speaks with early, rough transcriptions of the audio captured so far.</span></span>
- <span data-ttu-id="61551-116">**O resultado do ditado** é gerado no final de cada frase (ou seja, quando o usuário pausa) com a transcrição final do áudio capturado até o momento.</span><span class="sxs-lookup"><span data-stu-id="61551-116">**Dictation Result** is raised at the end of each sentence (i.e. when the user pauses) with the final transcription of the audio captured so far.</span></span>
- <span data-ttu-id="61551-117">**O ditado Concluído é** gerado no final da sessão de gravação com a transcrição completa e final do áudio.</span><span class="sxs-lookup"><span data-stu-id="61551-117">**Dictation Complete** is raised at the end of the recording session with the full, final transcription of the audio.</span></span>
- <span data-ttu-id="61551-118">**O erro de ditado** é gerado para informar erros no serviço de ditado.</span><span class="sxs-lookup"><span data-stu-id="61551-118">**Dictation Error** is raised to inform of errors in the dictation service.</span></span> <span data-ttu-id="61551-119">A transcrição nesse caso contém uma descrição do erro.</span><span class="sxs-lookup"><span data-stu-id="61551-119">The transcription in this case contains a description of the error.</span></span>

## <a name="example-scene"></a><span data-ttu-id="61551-120">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="61551-120">Example scene</span></span>

<span data-ttu-id="61551-121">**A cena de** ditado em `MRTK/Examples/Demos/Input/Scenes/Dictation` mostra o script em `DictationHandler` uso.</span><span class="sxs-lookup"><span data-stu-id="61551-121">**Dictation** scene in `MRTK/Examples/Demos/Input/Scenes/Dictation` shows the `DictationHandler` script in use.</span></span> <span data-ttu-id="61551-122">Se precisar de mais controle, você poderá estender esse script ou criar seu próprio implementando para [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) receber eventos de ditado diretamente.</span><span class="sxs-lookup"><span data-stu-id="61551-122">If you need more control, you can either extend this script or create your own implementing [`IMixedRealityDictationHandler`](xref:Microsoft.MixedReality.Toolkit.Input.IMixedRealityDictationHandler) to receive dictation events directly.</span></span>

<img src="../images/input/DictationDemo.png" width="80%" alt="Dictation Demo" class="center">
