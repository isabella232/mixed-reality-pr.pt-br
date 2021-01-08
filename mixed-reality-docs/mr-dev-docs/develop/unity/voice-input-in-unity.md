---
title: Entrada de voz no Unity
description: Saiba como o Unity expõe três maneiras de adicionar entrada de voz, reconhecimento de fala e ditado ao seu aplicativo Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, microfone, ditado, voz, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: d07909bbf05ff882eb0a4b6123c39eae9280e3e8
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98009796"
---
# <a name="voice-input-in-unity"></a><span data-ttu-id="85912-104">Entrada de voz no Unity</span><span class="sxs-lookup"><span data-stu-id="85912-104">Voice input in Unity</span></span>

>[!NOTE]
><span data-ttu-id="85912-105">Em vez das informações abaixo, considere usar o plug-in do Unity para o SDK de serviços de fala cognitiva que tem resultados de precisão de fala muito melhores e fornece acesso fácil a decodificação de fala a texto e recursos de fala avançados, como diálogo, interação baseada em intenção, tradução, síntese de conversão de texto em fala e reconhecimento de fala em idioma natural.</span><span class="sxs-lookup"><span data-stu-id="85912-105">Instead of the below information, consider using the Unity plug-in for the Cognitive Speech Services SDK which has much better Speech Accuracy results and provides easy access to speech-to-text decode and advanced speech features like dialog, intent based interaction, translation, text-to-speech synthesis and natural language speech recognition.</span></span> <span data-ttu-id="85912-106">Encontre o exemplo e documentação aqui: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span><span class="sxs-lookup"><span data-stu-id="85912-106">Find the sample and documentaion here: https://docs.microsoft.com//azure/cognitive-services/speech-service/quickstart-csharp-unity</span></span>   

<span data-ttu-id="85912-107">O Unity expõe três maneiras de adicionar [entrada de voz](../../design/voice-input.md) ao aplicativo Unity.</span><span class="sxs-lookup"><span data-stu-id="85912-107">Unity exposes three ways to add [Voice input](../../design/voice-input.md) to your Unity application.</span></span>

<span data-ttu-id="85912-108">Com o KeywordRecognizer (um dos dois tipos de PhraseRecognizers), seu aplicativo pode receber uma matriz de comandos de cadeia de caracteres a serem escutados.</span><span class="sxs-lookup"><span data-stu-id="85912-108">With the KeywordRecognizer (one of two types of PhraseRecognizers), your app can be given an array of string commands to listen for.</span></span> <span data-ttu-id="85912-109">Com o GrammarRecognizer (o outro tipo de PhraseRecognizer), seu aplicativo pode receber um arquivo SRGS definindo uma gramática específica a ser escutada.</span><span class="sxs-lookup"><span data-stu-id="85912-109">With the GrammarRecognizer (the other type of PhraseRecognizer), your app can be given an SRGS file defining a specific grammar to listen for.</span></span> <span data-ttu-id="85912-110">Com o DictationRecognizer, seu aplicativo pode escutar qualquer palavra e fornecer ao usuário uma nota ou outra exibição de sua fala.</span><span class="sxs-lookup"><span data-stu-id="85912-110">With the DictationRecognizer, your app can listen for any word and provide the user with a note or other display of their speech.</span></span>

>[!NOTE]
><span data-ttu-id="85912-111">Somente o reconhecimento de ditado ou frase pode ser manipulado de uma vez.</span><span class="sxs-lookup"><span data-stu-id="85912-111">Only dictation or phrase recognition can be handled at once.</span></span> <span data-ttu-id="85912-112">Isso significa que se um GrammarRecognizer ou KeywordRecognizer estiver ativo, um DictationRecognizer não poderá estar ativo e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="85912-112">That means if a GrammarRecognizer or KeywordRecognizer is active, a DictationRecognizer can not be active and vice versa.</span></span>

## <a name="enabling-the-capability-for-voice"></a><span data-ttu-id="85912-113">Habilitando o recurso de voz</span><span class="sxs-lookup"><span data-stu-id="85912-113">Enabling the capability for Voice</span></span>

<span data-ttu-id="85912-114">A capacidade do **microfone** deve ser declarada para um aplicativo usar entrada de voz.</span><span class="sxs-lookup"><span data-stu-id="85912-114">The **Microphone** capability must be declared for an app to use Voice input.</span></span>
1. <span data-ttu-id="85912-115">No editor do Unity, vá para as configurações do Player navegando até "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="85912-115">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player"</span></span>
2. <span data-ttu-id="85912-116">Selecione na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="85912-116">Select on the "Windows Store" tab</span></span>
3. <span data-ttu-id="85912-117">Na seção "configurações de publicação > recursos", verifique a capacidade do **microfone**</span><span class="sxs-lookup"><span data-stu-id="85912-117">In the "Publishing Settings > Capabilities" section, check the **Microphone** capability</span></span>

## <a name="phrase-recognition"></a><span data-ttu-id="85912-118">Reconhecimento de frases</span><span class="sxs-lookup"><span data-stu-id="85912-118">Phrase Recognition</span></span>

<span data-ttu-id="85912-119">Para permitir que seu aplicativo Ouça frases específicas faladas pelo usuário e, em seguida, execute alguma ação, você precisa:</span><span class="sxs-lookup"><span data-stu-id="85912-119">To enable your app to listen for specific phrases spoken by the user then take some action, you need to:</span></span>
1. <span data-ttu-id="85912-120">Especificar quais frases escutar usando um KeywordRecognizer ou GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="85912-120">Specify which phrases to listen for using a KeywordRecognizer or GrammarRecognizer</span></span>
2. <span data-ttu-id="85912-121">Manipular o evento OnPhraseRecognized e tomar medidas correspondentes à frase reconhecida</span><span class="sxs-lookup"><span data-stu-id="85912-121">Handle the OnPhraseRecognized event and take action corresponding to the phrase recognized</span></span>

### <a name="keywordrecognizer"></a><span data-ttu-id="85912-122">KeywordRecognizer</span><span class="sxs-lookup"><span data-stu-id="85912-122">KeywordRecognizer</span></span>

<span data-ttu-id="85912-123">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="85912-123">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="85912-124">**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="85912-124">**Types:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="85912-125">Precisaremos de algumas instruções de uso para salvar alguns pressionamentos de tecla:</span><span class="sxs-lookup"><span data-stu-id="85912-125">We'll need a few using statements to save some keystrokes:</span></span>

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

<span data-ttu-id="85912-126">Em seguida, vamos adicionar alguns campos à sua classe para armazenar o reconhecedor e o dicionário de ação de >de palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="85912-126">Then let's add a few fields to your class to store the recognizer and keyword->action dictionary:</span></span>

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

<span data-ttu-id="85912-127">Agora, adicione uma palavra-chave ao dicionário, por exemplo, em um método Start ().</span><span class="sxs-lookup"><span data-stu-id="85912-127">Now add a keyword to the dictionary, for example in of a Start() method.</span></span> <span data-ttu-id="85912-128">Estamos adicionando a palavra-chave "Activate" neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="85912-128">We're adding the "activate" keyword in this example:</span></span>

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

<span data-ttu-id="85912-129">Crie o reconhecedor de palavra-chave e diga a ele o que desejamos reconhecer:</span><span class="sxs-lookup"><span data-stu-id="85912-129">Create the keyword recognizer and tell it what we want to recognize:</span></span>

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

<span data-ttu-id="85912-130">Registre-se agora para o evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="85912-130">Now register for the OnPhraseRecognized event</span></span>

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="85912-131">Um manipulador de exemplo é:</span><span class="sxs-lookup"><span data-stu-id="85912-131">An example handler is:</span></span>

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

<span data-ttu-id="85912-132">Por fim, comece a reconhecer!</span><span class="sxs-lookup"><span data-stu-id="85912-132">Finally, start recognizing!</span></span>

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a><span data-ttu-id="85912-133">GrammarRecognizer</span><span class="sxs-lookup"><span data-stu-id="85912-133">GrammarRecognizer</span></span>

<span data-ttu-id="85912-134">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="85912-134">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="85912-135">**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="85912-135">**Types**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="85912-136">O GrammarRecognizer será usado se você estiver especificando a gramática de reconhecimento usando o SRGS.</span><span class="sxs-lookup"><span data-stu-id="85912-136">The GrammarRecognizer is used if you're specifying your recognition grammar using SRGS.</span></span> <span data-ttu-id="85912-137">Isso pode ser útil se seu aplicativo tiver mais do que apenas algumas palavras-chave, se você quiser reconhecer frases mais complexas ou se quiser ativar e desativar facilmente conjuntos de comandos.</span><span class="sxs-lookup"><span data-stu-id="85912-137">This can be useful if your app has more than just a few keywords, if you want to recognize more complex phrases, or if you want to easily turn on and off sets of commands.</span></span> <span data-ttu-id="85912-138">Consulte: [criar gramáticas usando o XML SRGS](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) para informações de formato de arquivo.</span><span class="sxs-lookup"><span data-stu-id="85912-138">See: [Create Grammars Using SRGS XML](https://msdn.microsoft.com/library/hh378349(v=office.14).aspx) for file format information.</span></span>

<span data-ttu-id="85912-139">Quando você tiver sua gramática SRGS e ele estiver em seu projeto em uma [pasta StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):</span><span class="sxs-lookup"><span data-stu-id="85912-139">Once you have your SRGS grammar, and it is in your project in a [StreamingAssets folder](https://docs.unity3d.com/Manual/StreamingAssets.html):</span></span>

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

<span data-ttu-id="85912-140">Crie um GrammarRecognizer e passe o caminho para o arquivo SRGS:</span><span class="sxs-lookup"><span data-stu-id="85912-140">Create a GrammarRecognizer and pass it the path to your SRGS file:</span></span>

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

<span data-ttu-id="85912-141">Registre-se agora para o evento OnPhraseRecognized</span><span class="sxs-lookup"><span data-stu-id="85912-141">Now register for the OnPhraseRecognized event</span></span>

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

<span data-ttu-id="85912-142">Você receberá um retorno de chamada contendo as informações especificadas na gramática SRGS, que você pode manipular adequadamente.</span><span class="sxs-lookup"><span data-stu-id="85912-142">You'll get a callback containing information specified in your SRGS grammar, which you can handle appropriately.</span></span> <span data-ttu-id="85912-143">A maioria das informações importantes será fornecida na matriz semanticMeanings.</span><span class="sxs-lookup"><span data-stu-id="85912-143">Most of the important information will be provided in the semanticMeanings array.</span></span>

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

<span data-ttu-id="85912-144">Por fim, comece a reconhecer!</span><span class="sxs-lookup"><span data-stu-id="85912-144">Finally, start recognizing!</span></span>

```
grammarRecognizer.Start();
```

## <a name="dictation"></a><span data-ttu-id="85912-145">Ditado</span><span class="sxs-lookup"><span data-stu-id="85912-145">Dictation</span></span>

<span data-ttu-id="85912-146">**Namespace:** *UnityEngine. Windows. Speech*</span><span class="sxs-lookup"><span data-stu-id="85912-146">**Namespace:** *UnityEngine.Windows.Speech*</span></span><br>
<span data-ttu-id="85912-147">**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span><span class="sxs-lookup"><span data-stu-id="85912-147">**Types**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*</span></span>

<span data-ttu-id="85912-148">Use o DictationRecognizer para converter a fala do usuário em texto.</span><span class="sxs-lookup"><span data-stu-id="85912-148">Use the DictationRecognizer to convert the user's speech to text.</span></span> <span data-ttu-id="85912-149">O DictationRecognizer expõe a funcionalidade de [ditado](../../design/voice-input.md#dictation) e dá suporte ao registro e à escuta de eventos de hipótese e de expressão concluídas, para que você possa fornecer comentários ao seu usuário enquanto eles falam e depois.</span><span class="sxs-lookup"><span data-stu-id="85912-149">The DictationRecognizer exposes [dictation](../../design/voice-input.md#dictation) functionality and supports registering and listening for hypothesis and phrase completed events, so you can give feedback to your user both while they speak and afterwards.</span></span> <span data-ttu-id="85912-150">Métodos Start () e Stop () respectivamente habilitam e desabilitam o reconhecimento de ditado.</span><span class="sxs-lookup"><span data-stu-id="85912-150">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span> <span data-ttu-id="85912-151">Depois de feito com o reconhecedor, ele deve ser descartado usando o método Dispose () para liberar os recursos que ele usa.</span><span class="sxs-lookup"><span data-stu-id="85912-151">Once done with the recognizer, it should be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="85912-152">Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho adicional se eles não forem liberados antes disso.</span><span class="sxs-lookup"><span data-stu-id="85912-152">It will release these resources automatically during garbage collection at an additional performance cost if they aren't released before that.</span></span>

<span data-ttu-id="85912-153">Há apenas algumas etapas necessárias para começar a usar o ditado:</span><span class="sxs-lookup"><span data-stu-id="85912-153">There are only a few steps needed to get started with dictation:</span></span>
1. <span data-ttu-id="85912-154">Criar um novo DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="85912-154">Create a new DictationRecognizer</span></span>
2. <span data-ttu-id="85912-155">Manipular eventos de ditado</span><span class="sxs-lookup"><span data-stu-id="85912-155">Handle Dictation events</span></span>
3. <span data-ttu-id="85912-156">Iniciar o DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="85912-156">Start the DictationRecognizer</span></span>

### <a name="enabling-the-capability-for-dictation"></a><span data-ttu-id="85912-157">Habilitando o recurso de ditado</span><span class="sxs-lookup"><span data-stu-id="85912-157">Enabling the capability for dictation</span></span>

<span data-ttu-id="85912-158">O recurso "cliente da Internet", junto com o recurso "microfone" mencionado acima, deve ser declarado para que um aplicativo aproveite o ditado.</span><span class="sxs-lookup"><span data-stu-id="85912-158">The "Internet Client" capability, along with the "Microphone" capability mentioned above, must be declared for an app to leverage dictation.</span></span>
1. <span data-ttu-id="85912-159">No editor do Unity, vá para as configurações do Player navegando para a página "Editar configurações do projeto > > Player"</span><span class="sxs-lookup"><span data-stu-id="85912-159">In the Unity Editor, go to the player settings by navigating to "Edit > Project Settings > Player" page</span></span>
2. <span data-ttu-id="85912-160">Selecione na guia "Windows Store"</span><span class="sxs-lookup"><span data-stu-id="85912-160">Select on the "Windows Store" tab</span></span>
3. <span data-ttu-id="85912-161">Na seção "configurações de publicação > recursos", verifique o recurso **internetclient**</span><span class="sxs-lookup"><span data-stu-id="85912-161">In the "Publishing Settings > Capabilities" section, check the **InternetClient** capability</span></span>

### <a name="dictationrecognizer"></a><span data-ttu-id="85912-162">DictationRecognizer</span><span class="sxs-lookup"><span data-stu-id="85912-162">DictationRecognizer</span></span>

<span data-ttu-id="85912-163">Crie um DictationRecognizer da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="85912-163">Create a DictationRecognizer like so:</span></span>

```
dictationRecognizer = new DictationRecognizer();
```

<span data-ttu-id="85912-164">Há quatro eventos de ditado que podem ser assinados e manipulados para implementar o comportamento do ditado.</span><span class="sxs-lookup"><span data-stu-id="85912-164">There are four dictation events that can be subscribed to and handled to implement dictation behavior.</span></span>
1. <span data-ttu-id="85912-165">DictationResult</span><span class="sxs-lookup"><span data-stu-id="85912-165">DictationResult</span></span>
2. <span data-ttu-id="85912-166">DictationComplete</span><span class="sxs-lookup"><span data-stu-id="85912-166">DictationComplete</span></span>
3. <span data-ttu-id="85912-167">DictationHypothesis</span><span class="sxs-lookup"><span data-stu-id="85912-167">DictationHypothesis</span></span>
4. <span data-ttu-id="85912-168">DictationError</span><span class="sxs-lookup"><span data-stu-id="85912-168">DictationError</span></span>

<span data-ttu-id="85912-169">**DictationResult**</span><span class="sxs-lookup"><span data-stu-id="85912-169">**DictationResult**</span></span>

<span data-ttu-id="85912-170">Esse evento é acionado depois que o usuário pausa, normalmente no final de uma sentença.</span><span class="sxs-lookup"><span data-stu-id="85912-170">This event is fired after the user pauses, typically at the end of a sentence.</span></span> <span data-ttu-id="85912-171">A cadeia de caracteres totalmente reconhecida é retornada aqui.</span><span class="sxs-lookup"><span data-stu-id="85912-171">The full recognized string is returned here.</span></span>

<span data-ttu-id="85912-172">Primeiro, assine o evento DictationResult:</span><span class="sxs-lookup"><span data-stu-id="85912-172">First, subscribe to the DictationResult event:</span></span>

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

<span data-ttu-id="85912-173">Em seguida, manipule o retorno de chamada DictationResult:</span><span class="sxs-lookup"><span data-stu-id="85912-173">Then handle the DictationResult callback:</span></span>

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

<span data-ttu-id="85912-174">**DictationHypothesis**</span><span class="sxs-lookup"><span data-stu-id="85912-174">**DictationHypothesis**</span></span>

<span data-ttu-id="85912-175">Esse evento é acionado continuamente enquanto o usuário está conversando.</span><span class="sxs-lookup"><span data-stu-id="85912-175">This event is fired continuously while the user is talking.</span></span> <span data-ttu-id="85912-176">Como o reconhecedor Ouve, ele fornece texto do que ele é ouvido até agora.</span><span class="sxs-lookup"><span data-stu-id="85912-176">As the recognizer listens, it provides text of what it's heard so far.</span></span>

<span data-ttu-id="85912-177">Primeiro, assine o evento DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="85912-177">First, subscribe to the DictationHypothesis event:</span></span>

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

<span data-ttu-id="85912-178">Em seguida, manipule o retorno de chamada DictationHypothesis:</span><span class="sxs-lookup"><span data-stu-id="85912-178">Then handle the DictationHypothesis callback:</span></span>

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

<span data-ttu-id="85912-179">**DictationComplete**</span><span class="sxs-lookup"><span data-stu-id="85912-179">**DictationComplete**</span></span>

<span data-ttu-id="85912-180">Esse evento é acionado quando o reconhecedor é interrompido, independentemente de Stop () ser chamado, um tempo limite de ocorrência ou algum outro erro.</span><span class="sxs-lookup"><span data-stu-id="85912-180">This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.</span></span>

<span data-ttu-id="85912-181">Primeiro, assine o evento DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="85912-181">First, subscribe to the DictationComplete event:</span></span>

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

<span data-ttu-id="85912-182">Em seguida, manipule o retorno de chamada DictationComplete:</span><span class="sxs-lookup"><span data-stu-id="85912-182">Then handle the DictationComplete callback:</span></span>

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

<span data-ttu-id="85912-183">**DictationError**</span><span class="sxs-lookup"><span data-stu-id="85912-183">**DictationError**</span></span>

<span data-ttu-id="85912-184">Esse evento é acionado quando ocorre um erro.</span><span class="sxs-lookup"><span data-stu-id="85912-184">This event is fired when an error occurs.</span></span>

<span data-ttu-id="85912-185">Primeiro, assine o evento DictationError:</span><span class="sxs-lookup"><span data-stu-id="85912-185">First, subscribe to the DictationError event:</span></span>

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

<span data-ttu-id="85912-186">Em seguida, manipule o retorno de chamada DictationError:</span><span class="sxs-lookup"><span data-stu-id="85912-186">Then handle the DictationError callback:</span></span>

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

<span data-ttu-id="85912-187">Depois de assinar e tratar os eventos de ditado sobre os quais você se preocupa, inicie o reconhecedor de ditado para começar a receber eventos.</span><span class="sxs-lookup"><span data-stu-id="85912-187">Once you've subscribed and handled the dictation events that you care about, start the dictation recognizer to begin receiving events.</span></span>

```
dictationRecognizer.Start();
```

<span data-ttu-id="85912-188">Se você não quiser mais manter o DictationRecognizer, precisará cancelar a assinatura dos eventos e descartar o DictationRecognizer.</span><span class="sxs-lookup"><span data-stu-id="85912-188">If you no longer want to keep the DictationRecognizer around, you need to unsubscribe from the events and Dispose the DictationRecognizer.</span></span>

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

<span data-ttu-id="85912-189">**Dicas**</span><span class="sxs-lookup"><span data-stu-id="85912-189">**Tips**</span></span>
* <span data-ttu-id="85912-190">Métodos Start () e Stop () respectivamente habilitam e desabilitam o reconhecimento de ditado.</span><span class="sxs-lookup"><span data-stu-id="85912-190">Start() and Stop() methods respectively enable and disable dictation recognition.</span></span>
* <span data-ttu-id="85912-191">Depois de feito com o reconhecedor, ele deve ser descartado usando o método Dispose () para liberar os recursos que ele usa.</span><span class="sxs-lookup"><span data-stu-id="85912-191">Once done with the recognizer, it must be disposed using Dispose() method to release the resources it uses.</span></span> <span data-ttu-id="85912-192">Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho adicional se eles não forem liberados antes disso.</span><span class="sxs-lookup"><span data-stu-id="85912-192">It will release these resources automatically during garbage collection at an additional performance cost if they aren't released before that.</span></span>
* <span data-ttu-id="85912-193">Os tempos limite ocorrem após um determinado período de tempo.</span><span class="sxs-lookup"><span data-stu-id="85912-193">Timeouts occur after a set period of time.</span></span> <span data-ttu-id="85912-194">Você pode verificar esses tempos limite no evento DictationComplete.</span><span class="sxs-lookup"><span data-stu-id="85912-194">You can check for these timeouts in the DictationComplete event.</span></span> <span data-ttu-id="85912-195">Há dois tempos limite a serem cientes:</span><span class="sxs-lookup"><span data-stu-id="85912-195">There are two timeouts to be aware of:</span></span>
   1. <span data-ttu-id="85912-196">Se o reconhecedor for iniciado e não ouvir áudio pelos primeiros cinco segundos, ele atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="85912-196">If the recognizer starts and doesn't hear any audio for the first five seconds, it will time out.</span></span>
   2. <span data-ttu-id="85912-197">Se o reconhecedor tiver dado um resultado, mas, em seguida, ouve silêncio por 20 segundos, ele atingirá o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="85912-197">If the recognizer has given a result, but then hears silence for 20 seconds, it will time out.</span></span>

## <a name="using-both-phrase-recognition-and-dictation"></a><span data-ttu-id="85912-198">Usando o reconhecimento de frase e o ditado</span><span class="sxs-lookup"><span data-stu-id="85912-198">Using both Phrase Recognition and Dictation</span></span>

<span data-ttu-id="85912-199">Se você quiser usar o reconhecimento de frase e o ditado em seu aplicativo, será necessário desligar completamente um antes para poder iniciar o outro.</span><span class="sxs-lookup"><span data-stu-id="85912-199">If you want to use both phrase recognition and dictation in your app, you'll need to fully shut one down before you can start the other.</span></span> <span data-ttu-id="85912-200">Se você tiver vários KeywordRecognizers em execução, poderá desligá-los de uma só vez com:</span><span class="sxs-lookup"><span data-stu-id="85912-200">If you have multiple KeywordRecognizers running, you can shut them all down at once with:</span></span>

```
PhraseRecognitionSystem.Shutdown();
```

<span data-ttu-id="85912-201">Para restaurar todos os reconhecedores ao estado anterior, depois que o DictationRecognizer for interrompido, você poderá chamar:</span><span class="sxs-lookup"><span data-stu-id="85912-201">In order to restore all recognizers to their previous state, after the DictationRecognizer has stopped, you can call:</span></span>

```
PhraseRecognitionSystem.Restart();
```

<span data-ttu-id="85912-202">Você também pode apenas iniciar um KeywordRecognizer, que reiniciará o PhraseRecognitionSystem também.</span><span class="sxs-lookup"><span data-stu-id="85912-202">You could also just start a KeywordRecognizer, which will restart the PhraseRecognitionSystem as well.</span></span>

## <a name="using-the-microphone-helper"></a><span data-ttu-id="85912-203">Usando o auxiliar de microfone</span><span class="sxs-lookup"><span data-stu-id="85912-203">Using the microphone helper</span></span>

<span data-ttu-id="85912-204">O kit de ferramentas de realidade misturada no GitHub contém uma classe auxiliar de microfone para indicar aos desenvolvedores se há um microfone utilizável no sistema.</span><span class="sxs-lookup"><span data-stu-id="85912-204">The Mixed Reality Toolkit on GitHub contains a microphone helper class to hint at developers if there's a usable microphone on the system.</span></span> <span data-ttu-id="85912-205">Um uso para é onde você desejaria verificar se há microfone no sistema antes de mostrar qualquer dica de interação de fala no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="85912-205">One use for it's where one would want to check if there's microphone on system before showing any speech interaction hints in the application.</span></span>

<span data-ttu-id="85912-206">O script auxiliar de microfone pode ser encontrado na [pasta de entrada/scripts/utilitários](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span><span class="sxs-lookup"><span data-stu-id="85912-206">The microphone helper script can be found in the [Input/Scripts/Utilities folder](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit/Input/Scripts/Utilities/MicrophoneHelper.cs).</span></span> <span data-ttu-id="85912-207">O repositório GitHub também contém um [pequeno exemplo](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrando como usar o auxiliar.</span><span class="sxs-lookup"><span data-stu-id="85912-207">The GitHub repo also contains a [small sample](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scripts/MicrophoneHelperSample.cs) demonstrating how to use the helper.</span></span>

## <a name="voice-input-in-mixed-reality-toolkit"></a><span data-ttu-id="85912-208">Entrada de voz no kit de ferramentas de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="85912-208">Voice input in Mixed Reality Toolkit</span></span>
<span data-ttu-id="85912-209">Você pode encontrar os exemplos da entrada de voz nesta cena.</span><span class="sxs-lookup"><span data-stu-id="85912-209">You can find the examples of the voice input in this scene.</span></span>

- [<span data-ttu-id="85912-210">HoloToolkit-Examples/Input/cenas/SpeechInputSource. Unity</span><span class="sxs-lookup"><span data-stu-id="85912-210">HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity</span></span>](https://github.com/Microsoft/MixedRealityToolkit-Unity/blob/htk_release/Assets/HoloToolkit-Examples/Input/Scenes/SpeechInputSource.unity)

## <a name="next-development-checkpoint"></a><span data-ttu-id="85912-211">Próximo ponto de verificação de desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="85912-211">Next Development Checkpoint</span></span>

<span data-ttu-id="85912-212">Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, a próxima tarefa está explorando os recursos e as APIs da plataforma de realidade misturada:</span><span class="sxs-lookup"><span data-stu-id="85912-212">If you're following the Unity development checkpoint journey we've laid out, you're next task is exploring the Mixed Reality platform capabilities and APIs:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="85912-213">Experiências compartilhadas</span><span class="sxs-lookup"><span data-stu-id="85912-213">Shared experiences</span></span>](shared-experiences-in-unity.md)

<span data-ttu-id="85912-214">Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="85912-214">You can always go back to the [Unity development checkpoints](unity-development-overview.md#2-core-building-blocks) at any time.</span></span>
