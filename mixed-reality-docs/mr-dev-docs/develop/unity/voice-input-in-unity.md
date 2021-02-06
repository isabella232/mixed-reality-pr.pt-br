---
title: Entrada de voz no Unity
description: Saiba como o Unity expõe três maneiras de adicionar entrada de voz, reconhecimento de fala e ditado ao seu aplicativo Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, microfone, ditado, voz, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: 7268a4df9c7fce03029937c72540ed274574067d
ms.sourcegitcommit: 8c3af63fb49494f75c8ab46236fc3dd8533c1e9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99606111"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="4438c-104">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="4438c-104">Voice input in Unity</span></span>

> [!CAUTION]
> <span data-ttu-id="4438c-105">Antes de começar, considere usar o plug-in do Unity para o SDK dos serviços de fala cognitiva.</span><span class="sxs-lookup"><span data-stu-id="4438c-105">Before starting, consider using the Unity plug-in for the Cognitive Speech Services SDK.</span></span> <span data-ttu-id="4438c-106">O plug-in tem melhores resultados de precisão de fala e acesso fácil à decodificação de fala em texto, bem como a recursos de fala avançados, como diálogo, interação baseada em intenção, tradução, síntese de conversão de texto em fala e reconhecimento de fala em idioma natural.</span><span class="sxs-lookup"><span data-stu-id="4438c-106">The plugin has better Speech Accuracy results and easy access to speech-to-text decode, as well as advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis, and natural language speech recognition.</span></span> <span data-ttu-id="4438c-107">Para começar, confira o [exemplo e a documentação](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span><span class="sxs-lookup"><span data-stu-id="4438c-107">To get started, check out the [sample and documentation](https://docs.microsoft.com/azure/cognitive-services/speech-service/quickstart-csharp-unity).</span></span>

<span data-ttu-id="4438c-108">O Unity expõe três maneiras de adicionar [entrada de voz](../../design/voice-input.md) ao aplicativo do Unity, os dois primeiros tipos de PhraseRecognizer:</span><span class="sxs-lookup"><span data-stu-id="4438c-108">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application, the first two of which are types of PhraseRecognizer:</span></span>
* <span data-ttu-id="4438c-109">O `KeywordRecognizer` fornece ao seu aplicativo uma matriz de comandos de cadeia de caracteres a serem escutados</span><span class="sxs-lookup"><span data-stu-id="4438c-109">The `KeywordRecognizer` supplies your app with an array of string commands to listen for</span></span>
* <span data-ttu-id="4438c-110">O `GrammarRecognizer` fornece ao seu aplicativo um arquivo SRGS que define uma gramática específica a ser escutada</span><span class="sxs-lookup"><span data-stu-id="4438c-110">The `GrammarRecognizer` gives your app an SRGS file defining a specific grammar to listen for</span></span>
* <span data-ttu-id="4438c-111">O `DictationRecognizer` permite que seu aplicativo Ouça qualquer palavra e forneça ao usuário uma anotação ou outra exibição de sua fala</span><span class="sxs-lookup"><span data-stu-id="4438c-111">The `DictationRecognizer` lets your app listen for any word and provide the user with a note or other display of their speech</span></span>

> [!NOTE]
> <span data-ttu-id="4438c-112">O reconhecimento de ditado e de frase não pode ser tratado ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="4438c-112">Dictation and phrase recognition can't be handled at the same time.</span></span> <span data-ttu-id="4438c-113">Se um GrammarRecognizer ou KeywordRecognizer estiver ativo, um DictationRecognizer não poderá estar ativo e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="4438c-113">If a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can't be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="4438c-114">Habilitando o recurso de voz</span><span class="sxs-lookup"><span data-stu-id="4438c-114">Enabling the capability for Voice</span></span>

<span data-ttu-id="4438c-115">A capacidade do **microfone** deve ser declarada para um aplicativo usar entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="4438c-115">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="4438c-116">No editor do Unity, navegue até **Editar configurações do projeto > > Player**</span><span class="sxs-lookup"><span data-stu-id="4438c-116">In the Unity Editor, navigate to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="4438c-117">Selecione a guia **Windows Store**</span><span class="sxs-lookup"><span data-stu-id="4438c-117">Select the **Windows Store** tab</span></span>
3. <span data-ttu-id="4438c-118">Na seção **configurações de publicação > recursos** , verifique o recurso de **microfone**</span><span class="sxs-lookup"><span data-stu-id="4438c-118">In the **Publishing Settings > Capabilities** section, check the **Microphone** capability</span></span>
4. <span data-ttu-id="4438c-119">Conceder permissões ao aplicativo para acesso ao microfone em seu dispositivo de HoloLens</span><span class="sxs-lookup"><span data-stu-id="4438c-119">Grant permissions to the app for microphone access on your HoloLens device</span></span>
    * <span data-ttu-id="4438c-120">Você será solicitado a fazer isso na inicialização do dispositivo, mas se você clicou acidentalmente em "não", poderá alterar as permissões nas configurações do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4438c-120">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="4438c-121">Reconhecimento de frases</span><span class="sxs-lookup"><span data-stu-id="4438c-121">Phrase Recognition</span></span>

<span data-ttu-id="4438c-122">Para permitir que seu aplicativo Ouça frases específicas faladas pelo usuário e, em seguida, execute alguma ação, você precisa:</span><span class="sxs-lookup"><span data-stu-id="4438c-122">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="4438c-123">Especificar quais frases escutar usando um `KeywordRecognizer` ou `GrammarRecognizer`</span><span class="sxs-lookup"><span data-stu-id="4438c-123">Specify which phrases to listen for using a `KeywordRecognizer` or `GrammarRecognizer`</span></span>
2. <span data-ttu-id="4438c-124">Manipular o `OnPhraseRecognized` evento e tomar medidas correspondentes à frase reconhecida</span><span class="sxs-lookup"><span data-stu-id="4438c-124">Handle the `OnPhraseRecognized` event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="4438c-125">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="4438c-125">KeywordRecognizer</span></span>

<span data-ttu-id="4438c-126">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="4438c-126">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="4438c-127">**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="4438c-127">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="4438c-128">Precisaremos de algumas instruções de uso para salvar alguns pressionamentos de tecla:</span><span class="sxs-lookup"><span data-stu-id="4438c-128">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="4438c-129">Em seguida, vamos adicionar alguns campos à sua classe para armazenar o reconhecedor e o dicionário de ação de >de palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="4438c-129">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="4438c-130">Agora, adicione uma palavra-chave ao dicionário, por exemplo, em um `Start()` método.</span><span class="sxs-lookup"><span data-stu-id="4438c-130">Now add a keyword to the dictionary, for example in of a `Start()` method.</span></span> <span data-ttu-id="4438c-131">Estamos adicionando a palavra-chave "Activate" neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="4438c-131">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="4438c-132">Crie o reconhecedor de palavra-chave e diga a ele o que desejamos reconhecer:</span><span class="sxs-lookup"><span data-stu-id="4438c-132">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="4438c-133">Registre-se agora para o `OnPhraseRecognized` evento</span><span class="sxs-lookup"><span data-stu-id="4438c-133">Now register for the `OnPhraseRecognized` event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="4438c-134">Um manipulador de exemplo é:</span><span class="sxs-lookup"><span data-stu-id="4438c-134">An example handler is:</span></span>

```
private void KeywordRecognizer_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    System.Action keywordAction;
    // if the keyword recognized is in our dictionary, call that Action.
    if (keywords.TryGetValue(args.text, out keywordAction))
    {
        keywordAction.Invoke();
    }
}
```

<span data-ttu-id="4438c-135">Por fim, comece a reconhecer!</span><span class="sxs-lookup"><span data-stu-id="4438c-135">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="4438c-136">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="4438c-136">GrammarRecognizer</span></span>

<span data-ttu-id="4438c-137">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="4438c-137">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="4438c-138">**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="4438c-138">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="4438c-139">O GrammarRecognizer será usado se você estiver especificando a gramática de reconhecimento usando o SRGS.</span><span class="sxs-lookup"><span data-stu-id="4438c-139">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="4438c-140">Isso pode ser útil se seu aplicativo tiver mais do que apenas algumas palavras-chave, se você quiser reconhecer frases mais complexas ou se quiser ativar e desativar facilmente conjuntos de comandos.</span><span class="sxs-lookup"><span data-stu-id="4438c-140">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="4438c-141">Consulte: [criar gramáticas usando o XML SRGS](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) para informações de formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="4438c-141">See: [Create Grammars Using SRGS XML](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) for file format information.</span></span>

<span data-ttu-id="4438c-142">Quando você tiver sua gramática SRGS e ele estiver em seu projeto em uma [pasta StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="4438c-142">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="4438c-143">Crie um `GrammarRecognizer` e passe o caminho para o arquivo SRGS:</span><span class="sxs-lookup"><span data-stu-id="4438c-143">Create a `GrammarRecognizer` and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="4438c-144">Registre-se agora para o `OnPhraseRecognized` evento</span><span class="sxs-lookup"><span data-stu-id="4438c-144">Now register for the `OnPhraseRecognized` event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="4438c-145">Você receberá um retorno de chamada contendo as informações especificadas na gramática SRGS, que você pode manipular adequadamente.</span><span class="sxs-lookup"><span data-stu-id="4438c-145">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="4438c-146">A maioria das informações importantes será fornecida na `semanticMeanings` matriz.</span><span class="sxs-lookup"><span data-stu-id="4438c-146">Most of the important information will be provided in the `semanticMeanings` array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="4438c-147">Por fim, comece a reconhecer!</span><span class="sxs-lookup"><span data-stu-id="4438c-147">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="4438c-148">Ditado</span><span class="sxs-lookup"><span data-stu-id="4438c-148">Dictation</span></span>

<span data-ttu-id="4438c-149">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="4438c-149">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="4438c-150">**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="4438c-150">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="4438c-151">Use o `DictationRecognizer` para converter a fala do usuário em texto.</span><span class="sxs-lookup"><span data-stu-id="4438c-151">Use the `DictationRecognizer` to convert the user's speech to text.</span></span> <span data-ttu-id="4438c-152">O DictationRecognizer expõe a funcionalidade de [ditado](../../design/voice-input.md#dictation) e dá suporte ao registro e à escuta de eventos de hipótese e de expressão concluídas, para que você possa fornecer comentários ao seu usuário enquanto eles falam e depois.</span><span class="sxs-lookup"><span data-stu-id="4438c-152">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="4438c-153">`Start()` e `Stop()` métodos respectivamente habilitam e desabilitam o reconhecimento de ditado.</span><span class="sxs-lookup"><span data-stu-id="4438c-153">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="4438c-154">Depois de feito com o reconhecedor, ele deve ser descartado usando o `Dispose()` para liberar os recursos que ele usa.</span><span class="sxs-lookup"><span data-stu-id="4438c-154">Once done with the recognizer, it should be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="4438c-155">Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho extra se eles não forem liberados antes disso.</span><span class="sxs-lookup"><span data-stu-id="4438c-155">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>

<span data-ttu-id="4438c-156">Há apenas algumas etapas necessárias para começar a usar o ditado:</span><span class="sxs-lookup"><span data-stu-id="4438c-156">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="4438c-157">Criar um novo `DictationRecognizer`</span><span class="sxs-lookup"><span data-stu-id="4438c-157">Create a new `DictationRecognizer`</span></span>
2. <span data-ttu-id="4438c-158">Manipular eventos de ditado</span><span class="sxs-lookup"><span data-stu-id="4438c-158">Handle Dictation events</span></span>
3. <span data-ttu-id="4438c-159">Iniciar o DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="4438c-159">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="4438c-160">Habilitando o recurso de ditado</span><span class="sxs-lookup"><span data-stu-id="4438c-160">Enabling the capability for dictation</span></span>

<span data-ttu-id="4438c-161">Os recursos de cliente e **microfone** da **Internet** devem ser declarados para que um aplicativo use o ditado:</span><span class="sxs-lookup"><span data-stu-id="4438c-161">The **Internet Client** and **Microphone** capabilities must be declared for an app to use dictation:</span></span>
1. <span data-ttu-id="4438c-162">No editor do Unity, vá para **Editar configurações do projeto > > Player**</span><span class="sxs-lookup"><span data-stu-id="4438c-162">In the Unity Editor, go to **Edit > Project Settings > Player**</span></span>
2. <span data-ttu-id="4438c-163">Selecione na guia **Windows Store**</span><span class="sxs-lookup"><span data-stu-id="4438c-163">Select on the **Windows Store** tab</span></span>
3. <span data-ttu-id="4438c-164">Na seção **configurações de publicação > recursos** , verifique o recurso **internetclient**</span><span class="sxs-lookup"><span data-stu-id="4438c-164">In the **Publishing Settings > Capabilities** section, check the **InternetClient** capability</span></span>
    * <span data-ttu-id="4438c-165">Opcionalmente, se você ainda não habilitou o microfone, verifique a capacidade do **microfone**</span><span class="sxs-lookup"><span data-stu-id="4438c-165">Optionally, if you didn't already enable the microphone, check the **Microphone** capability</span></span>
4. <span data-ttu-id="4438c-166">Conceda permissões ao aplicativo para acesso ao microfone no seu dispositivo HoloLens se você ainda não</span><span class="sxs-lookup"><span data-stu-id="4438c-166">Grant permissions to the app for microphone access on your HoloLens device if you haven't already</span></span>
    * <span data-ttu-id="4438c-167">Você será solicitado a fazer isso na inicialização do dispositivo, mas se você clicou acidentalmente em "não", poderá alterar as permissões nas configurações do dispositivo</span><span class="sxs-lookup"><span data-stu-id="4438c-167">You'll be asked to do this on device startup, but if you accidentally clicked "no" you can change the permissions in the device settings</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="4438c-168">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="4438c-168">DictationRecognizer</span></span>

<span data-ttu-id="4438c-169">Crie um DictationRecognizer da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="4438c-169">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="4438c-170">Há quatro eventos de ditado que podem ser assinados e manipulados para implementar o comportamento do ditado.</span><span class="sxs-lookup"><span data-stu-id="4438c-170">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

<span data-ttu-id="4438c-171">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="4438c-171">**DictationResult**</span></span>

<span data-ttu-id="4438c-172">Esse evento é acionado depois que o usuário pausa, normalmente no final de uma sentença.</span><span class="sxs-lookup"><span data-stu-id="4438c-172">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="4438c-173">A cadeia de caracteres totalmente reconhecida é retornada aqui.</span><span class="sxs-lookup"><span data-stu-id="4438c-173">The full recognized string is returned here.</span></span>

<span data-ttu-id="4438c-174">Primeiro, assine o `DictationResult` evento:</span><span class="sxs-lookup"><span data-stu-id="4438c-174">First, subscribe to the `DictationResult` event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="4438c-175">Em seguida, manipule o retorno de chamada DictationResult:</span><span class="sxs-lookup"><span data-stu-id="4438c-175">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="4438c-176">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="4438c-176">**DictationHypothesis**</span></span>

<span data-ttu-id="4438c-177">Esse evento é acionado continuamente enquanto o usuário está conversando.</span><span class="sxs-lookup"><span data-stu-id="4438c-177">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="4438c-178">Como o reconhecedor Ouve, ele fornece texto do que ele é ouvido até agora.</span><span class="sxs-lookup"><span data-stu-id="4438c-178">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="4438c-179">Primeiro, assine o `DictationHypothesis` evento:</span><span class="sxs-lookup"><span data-stu-id="4438c-179">First, subscribe to the `DictationHypothesis` event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="4438c-180">Em seguida, manipule o retorno de chamada DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="4438c-180">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="4438c-181">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="4438c-181">**DictationComplete**</span></span>

<span data-ttu-id="4438c-182">Esse evento é acionado quando o reconhecedor é interrompido, independentemente de Stop () ser chamado, um tempo limite de ocorrência ou algum outro erro.</span><span class="sxs-lookup"><span data-stu-id="4438c-182">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="4438c-183">Primeiro, assine o `DictationComplete` evento:</span><span class="sxs-lookup"><span data-stu-id="4438c-183">First, subscribe to the `DictationComplete` event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="4438c-184">Em seguida, manipule o retorno de chamada DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="4438c-184">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="4438c-185">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="4438c-185">**DictationError**</span></span>

<span data-ttu-id="4438c-186">Esse evento é acionado quando ocorre um erro.</span><span class="sxs-lookup"><span data-stu-id="4438c-186">This event is fired when an error occurs.</span></span>

<span data-ttu-id="4438c-187">Primeiro, assine o `DictationError` evento:</span><span class="sxs-lookup"><span data-stu-id="4438c-187">First, subscribe to the `DictationError` event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="4438c-188">Em seguida, manipule o retorno de chamada DictationError:</span><span class="sxs-lookup"><span data-stu-id="4438c-188">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="4438c-189">Depois de assinar e tratar os eventos de ditado sobre os quais você se preocupa, inicie o reconhecedor de ditado para começar a receber eventos.</span><span class="sxs-lookup"><span data-stu-id="4438c-189">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="4438c-190">Se você não quiser mais manter o DictationRecognizer, precisará cancelar a assinatura dos eventos e descartar o DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="4438c-190">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="4438c-191">**Dicas**</span><span class="sxs-lookup"><span data-stu-id="4438c-191">**Tips**</span></span>
* <span data-ttu-id="4438c-192">`Start()` e `Stop()` métodos respectivamente habilitam e desabilitam o reconhecimento de ditado.</span><span class="sxs-lookup"><span data-stu-id="4438c-192">`Start()` and `Stop()` methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="4438c-193">Depois de feito com o reconhecedor, ele deve ser descartado usando o `Dispose()` para liberar os recursos que ele usa.</span><span class="sxs-lookup"><span data-stu-id="4438c-193">Once done with the recognizer, it must be disposed using `Dispose()` to release the resources it uses.</span></span> <span data-ttu-id="4438c-194">Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho extra se eles não forem liberados antes disso.</span><span class="sxs-lookup"><span data-stu-id="4438c-194">It will release these resources automatically during garbage collection at an extra performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="4438c-195">Os tempos limite ocorrem após um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="4438c-195">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="4438c-196">Você pode verificar esses tempos limite no `DictationComplete` evento.</span><span class="sxs-lookup"><span data-stu-id="4438c-196">You can check for these timeouts in the `DictationComplete` event.</span></span> <span data-ttu-id="4438c-197">Há dois tempos limite a serem cientes:</span><span class="sxs-lookup"><span data-stu-id="4438c-197">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="4438c-198">Se o reconhecedor for iniciado e não ouvir áudio pelos primeiros cinco segundos, ele atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4438c-198">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="4438c-199">Se o reconhecedor tiver dado um resultado, mas, em seguida, ouve silêncio por 20 segundos, ele atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="4438c-199">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="4438c-200">Usando o reconhecimento de frase e o ditado</span><span class="sxs-lookup"><span data-stu-id="4438c-200">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="4438c-201">Se você quiser usar o reconhecimento de frase e o ditado em seu aplicativo, será necessário desligar completamente um antes para poder iniciar o outro.</span><span class="sxs-lookup"><span data-stu-id="4438c-201">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="4438c-202">Se você tiver vários KeywordRecognizers em execução, poderá desligá-los de uma só vez com:</span><span class="sxs-lookup"><span data-stu-id="4438c-202">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="4438c-203">Você pode chamar `Restart()` para restaurar todos os reconhecedores ao estado anterior depois que o DictationRecognizer for interrompido:</span><span class="sxs-lookup"><span data-stu-id="4438c-203">You can call `Restart()` to restore all recognizers to their previous state after the DictationRecognizer has stopped:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="4438c-204">Você também pode apenas iniciar um KeywordRecognizer, que reiniciará o PhraseRecognitionSystem também.</span><span class="sxs-lookup"><span data-stu-id="4438c-204">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="4438c-205">Entrada de voz no kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="4438c-205">Voice input in Mixed Reality Toolkit</span></span>

<span data-ttu-id="4438c-206">Você pode encontrar exemplos de MRTK para entrada de voz nas seguintes cenas de demonstração:</span><span class="sxs-lookup"><span data-stu-id="4438c-206">You can find MRTK examples for voice input in the following demo scenes:</span></span>
* [<span data-ttu-id="4438c-207">Comandos</span><span class="sxs-lookup"><span data-stu-id="4438c-207">Dictation</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [<span data-ttu-id="4438c-208">Fala</span><span class="sxs-lookup"><span data-stu-id="4438c-208">Speech</span></span>](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a><span data-ttu-id="4438c-209">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="4438c-209">Next Development Checkpoint</span></span>

<span data-ttu-id="4438c-210">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, a próxima tarefa está explorando os recursos e as APIs da plataforma de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="4438c-210">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="4438c-211">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="4438c-211">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="4438c-212">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="4438c-212">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>