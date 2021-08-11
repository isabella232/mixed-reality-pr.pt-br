---
title: Entrada de voz no DirectX
description: Explica como implementar comandos de voz e reconhecimento de frases pequenas e frases em um aplicativo DirectX para Windows Mixed Reality.
author: mikeriches
ms.author: mriches
ms.date: 08/04/2020
ms.topic: article
keywords: passo a passo, comando de voz, frase, reconhecimento, fala, directx, plataforma, cortana, windows mixed reality
ms.openlocfilehash: e30d5c2101bed4b613111b6131a3e94d654c3ff5b1e913f4d8e275ffc1a2776a
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221836"
---
# <a name="voice-input-in-directx"></a>Entrada de voz no DirectX

> [!NOTE]
> Este artigo está relacionado às APIs nativas do WinRT herddas.  Para novos projetos de aplicativo nativo, é recomendável usar a **[API openXR](openxr-getting-started.md)**.

Este artigo explica como implementar comandos de [voz](../../design/voice-input.md) mais reconhecimento de frases pequenas e frases em um aplicativo DirectX para Windows Mixed Reality.

>[!NOTE]
>Os snippets de código neste artigo usam C++/CX em vez de C++17 em conformidade com C++/WinRT, que é usado no modelo de projeto [holográfico C++.](creating-a-holographic-directx-project.md)  Os conceitos são equivalentes para um projeto C++/WinRT, mas você precisa traduzir o código.

## <a name="use-speechrecognizer-for-continuous-speech-recognition"></a>Usar SpeechRecognizer para reconhecimento de fala contínuo

Esta seção descreve como usar o reconhecimento de fala contínuo para habilitar comandos de voz em seu aplicativo. Este passo a passo usa o código do [exemplo HolographicVoiceInput.](https://go.microsoft.com/fwlink/p/?LinkId=844964) Quando o exemplo estiver em execução, fale o nome de um dos comandos de cor registrados para alterar a cor do cubo giratório.

Primeiro, crie uma nova *instância Windows::Media::SpeechRecognition::SpeechRecognizer.*

De *HolographicVoiceInputSampleMain::CreateSpeechConstraintsForCurrentState:*

```
m_speechRecognizer = ref new SpeechRecognizer();
```

Crie uma lista de comandos de fala para o reconhecedor escutar. Aqui, construiremos um conjunto de comandos para alterar a cor de um holograma. Para sua conveniência, também criamos os dados que vamos usar para os comandos posteriormente.

```
m_speechCommandList = ref new Platform::Collections::Vector<String^>();
   m_speechCommandData.clear();
   m_speechCommandList->Append(StringReference(L"white"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"grey"));
   m_speechCommandData.push_back(float4(0.5f, 0.5f, 0.5f, 1.f));
   m_speechCommandList->Append(StringReference(L"green"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"black"));
   m_speechCommandData.push_back(float4(0.1f, 0.1f, 0.1f, 1.f));
   m_speechCommandList->Append(StringReference(L"red"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"yellow"));
   m_speechCommandData.push_back(float4(1.f, 1.f, 0.f, 1.f));
   m_speechCommandList->Append(StringReference(L"aquamarine"));
   m_speechCommandData.push_back(float4(0.f, 1.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"blue"));
   m_speechCommandData.push_back(float4(0.f, 0.f, 1.f, 1.f));
   m_speechCommandList->Append(StringReference(L"purple"));
   m_speechCommandData.push_back(float4(1.f, 0.f, 1.f, 1.f));
```

Você pode usar palavras phoneéticas que podem não estar em um dicionário para especificar comandos.

```
m_speechCommandList->Append(StringReference(L"SpeechRecognizer"));
   m_speechCommandData.push_back(float4(0.5f, 0.1f, 1.f, 1.f));
```

Para carregar a lista de comandos na lista de restrições para o reconhecedor de fala, use um objeto [SpeechRecognitionListConstraint.](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionListConstraint)

```
SpeechRecognitionListConstraint^ spConstraint = ref new SpeechRecognitionListConstraint(m_speechCommandList);
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(spConstraint);
   create_task(m_speechRecognizer->CompileConstraintsAsync()).then([this](SpeechRecognitionCompilationResult^ compilationResult)
   {
       if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
       {
           m_speechRecognizer->ContinuousRecognitionSession->StartAsync();
       }
       else
       {
           // Handle errors here.
       }
   });
```

Assine o [evento ResultGenerated](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) no [SpeechContinuousRecognitionSession do reconhecedor de fala.](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionSession) Esse evento notifica seu aplicativo quando um de seus comandos foi reconhecido.

```
m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated +=
       ref new TypedEventHandler<SpeechContinuousRecognitionSession^, SpeechContinuousRecognitionResultGeneratedEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnResultGenerated, this, _1, _2)
           );
```

O *manipulador de eventos OnResultGenerated* recebe dados de evento em uma instância [speechContinuousRecognitionResultGeneratedEventArgs.](/uwp/api/Windows.Media.SpeechRecognition.SpeechContinuousRecognitionResultGeneratedEventArgs) Se a confiança for maior que o limite definido, seu aplicativo deverá observar que o evento ocorreu. Salve os dados do evento para que você possa usá-los em um loop de atualização posterior.

De *HolographicVoiceInputSampleMain.cpp:*

```
// Change the cube color, if we get a valid result.
   void HolographicVoiceInputSampleMain::OnResultGenerated(SpeechContinuousRecognitionSession ^sender, SpeechContinuousRecognitionResultGeneratedEventArgs ^args)
   {
       if (args->Result->RawConfidence > 0.5f)
       {
           m_lastCommand = args->Result->Text;
       }
   }
```

Em nosso código de exemplo, alteramos a cor do cubo de holograma giratório de acordo com o comando do usuário.

De *HolographicVoiceInputSampleMain::Update:*

```
// Check for new speech input since the last frame.
   if (m_lastCommand != nullptr)
   {
       auto command = m_lastCommand;
       m_lastCommand = nullptr;

       int i = 0;
       for each (auto& iter in m_speechCommandList)
       {
           if (iter == command)
           {
               m_spinningCubeRenderer->SetColor(m_speechCommandData[i]);
               break;
           }

           ++i;
       }
   }
```

## <a name="use-one-shot-recognition"></a>Usar o reconhecimento "one-shot"

Você pode configurar um reconhecedor de fala para escutar frases ou frases que o usuário fala. Nesse caso, aplicamos um *SpeechRecognitionTopicConstraint* que informa ao reconhecedor de fala que tipo de entrada esperar. Aqui está um fluxo de trabalho do aplicativo para este cenário:
1. Seu aplicativo cria o SpeechRecognizer, fornece prompts de interface do usuário e começa a escutar um comando falado.
2. O usuário fala uma frase ou frase.
3. O reconhecimento da fala do usuário ocorre e um resultado é retornado ao aplicativo. Neste ponto, seu aplicativo deve fornecer um prompt de interface do usuário para indicar que o reconhecimento ocorreu.
4. Dependendo do nível de confiança que você deseja responder e do nível de confiança do resultado do reconhecimento de fala, seu aplicativo pode processar o resultado e responder conforme apropriado.

Esta seção descreve como criar um SpeechRecognizer, compilar a restrição e escutar a entrada de fala.

O código a seguir compila a restrição de tópico, que, nesse caso, é otimizada para pesquisa na Web.

```
auto constraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, L"webSearch");
   m_speechRecognizer->Constraints->Clear();
   m_speechRecognizer->Constraints->Append(constraint);
   return create_task(m_speechRecognizer->CompileConstraintsAsync())
       .then([this](task<SpeechRecognitionCompilationResult^> previousTask)
   {
```

Se a compilação for bem-sucedida, podemos continuar com o reconhecimento de fala.

```
try
       {
           SpeechRecognitionCompilationResult^ compilationResult = previousTask.get();

           // Check to make sure that the constraints were in a proper format and the recognizer was able to compile it.
           if (compilationResult->Status == SpeechRecognitionResultStatus::Success)
           {
               // If the compilation succeeded, we can start listening for the user's spoken phrase or sentence.
               create_task(m_speechRecognizer->RecognizeAsync()).then([this](task<SpeechRecognitionResult^>& previousTask)
               {
```

O resultado é retornado ao aplicativo. Se temos confiança suficiente no resultado, podemos processar o comando. Este exemplo de código processa os resultados com pelo menos confiança média.

```
try
                   {
                       auto result = previousTask.get();

                       if (result->Status != SpeechRecognitionResultStatus::Success)
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech recognition was not successful: ") +
                               result->Status.ToString()->Data() +
                               L"\n"
                               );
                       }

                       // In this example, we look for at least medium confidence in the speech result.
                       if ((result->Confidence == SpeechRecognitionConfidence::High) ||
                           (result->Confidence == SpeechRecognitionConfidence::Medium))
                       {
                           // If the user said a color name anywhere in their phrase, it will be recognized in the
                           // Update loop; then, the cube will change color.
                           m_lastCommand = result->Text;

                           PrintWstringToDebugConsole(
                               std::wstring(L"Speech phrase was: ") +
                               m_lastCommand->Data() +
                               L"\n"
                               );
                       }
                       else
                       {
                           PrintWstringToDebugConsole(
                               std::wstring(L"Recognition confidence not high enough: ") +
                               result->Confidence.ToString()->Data() +
                               L"\n"
                               );
                       }
                   }
```

Sempre que você usar o reconhecimento de fala, observe as exceções que podem indicar que o usuário tenha desligado o microfone nas configurações de privacidade do sistema. Isso pode acontecer durante a inicialização ou o reconhecimento.

```
catch (Exception^ exception)
                   {
                       // Note that if you get an "Access is denied" exception, you might need to enable the microphone
                       // privacy setting on the device and/or add the microphone capability to your app manifest.

                       PrintWstringToDebugConsole(
                           std::wstring(L"Speech recognizer error: ") +
                           exception->ToString()->Data() +
                           L"\n"
                           );
                   }
               });

               return true;
           }
           else
           {
               OutputDebugStringW(L"Could not initialize predefined grammar speech engine!\n");

               // Handle errors here.
               return false;
           }
       }
       catch (Exception^ exception)
       {
           // Note that if you get an "Access is denied" exception, you might need to enable the microphone
           // privacy setting on the device and/or add the microphone capability to your app manifest.

           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to initialize predefined grammar speech engine:") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
           return false;
       }
   });
```

> [!NOTE]
> Há vários [SpeechRecognitionScenarios predefinidos](/uwp/api/Windows.Media.SpeechRecognition.SpeechRecognitionScenario) que você pode usar para otimizar o reconhecimento de fala.

* Para otimizar o ditado, use o cenário de ditado.<br/>
   ```
   // Compile the dictation topic constraint, which optimizes for speech dictation.
   auto dictationConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::Dictation, "dictation");
   m_speechRecognizer->Constraints->Append(dictationConstraint);
   ```

* Para pesquisas na Web de fala, use a seguinte restrição de cenário específica da Web.

   ```
   // Add a web search topic constraint to the recognizer.
   auto webSearchConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::WebSearch, "webSearch");
   speechRecognizer->Constraints->Append(webSearchConstraint);
   ```

* Use a restrição de formulário para preencher formulários. Nesse caso, é melhor aplicar sua própria gramática otimizada para preencher o formulário.

   ```
   // Add a form constraint to the recognizer.
   auto formConstraint = ref new SpeechRecognitionTopicConstraint(SpeechRecognitionScenario::FormFilling, "formFilling");
   speechRecognizer->Constraints->Append(formConstraint );
   ```
* Você pode fornecer sua própria gramática no formato SRGS.

## <a name="use-continuous-recognition"></a>Usar o reconhecimento contínuo

Para o cenário de ditado contínuo, consulte o exemplo Windows 10 código de fala [UWP.](https://github.com/Microsoft/Windows-universal-samples/blob/master/Samples/SpeechRecognitionAndSynthesis/cpp/Scenario_ContinuousDictation.xaml.cpp)

## <a name="handle-quality-degradation"></a>Lidar com a degradação da qualidade

Às vezes, as condições ambientais interferem no reconhecimento de fala. Por exemplo, a sala pode ser muito barulhenta ou o usuário pode falar muito alto. Sempre que possível, a API de reconhecimento de fala fornece informações sobre as condições que causaram a degradação da qualidade. Essas informações são pressionadas para seu aplicativo por meio de um evento WinRT. O exemplo a seguir mostra como assinar esse evento.

```
m_speechRecognizer->RecognitionQualityDegrading +=
       ref new TypedEventHandler<SpeechRecognizer^, SpeechRecognitionQualityDegradingEventArgs^>(
           std::bind(&HolographicVoiceInputSampleMain::OnSpeechQualityDegraded, this, _1, _2)
           );
```

Em nosso exemplo de código, escrevemos as informações de condições no console de depuração. Um aplicativo pode querer fornecer comentários ao usuário por meio da interface do usuário, da síntese de fala e de outro método. Ou talvez seja necessário se comportar de maneira diferente quando a fala é interrompida por uma redução temporária na qualidade.

```
void HolographicSpeechPromptSampleMain::OnSpeechQualityDegraded(SpeechRecognizer^ recognizer, SpeechRecognitionQualityDegradingEventArgs^ args)
   {
       switch (args->Problem)
       {
       case SpeechRecognitionAudioProblem::TooFast:
           OutputDebugStringW(L"The user spoke too quickly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooSlow:
           OutputDebugStringW(L"The user spoke too slowly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooQuiet:
           OutputDebugStringW(L"The user spoke too softly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooLoud:
           OutputDebugStringW(L"The user spoke too loudly.\n");
           break;

       case SpeechRecognitionAudioProblem::TooNoisy:
           OutputDebugStringW(L"There is too much noise in the signal.\n");
           break;

       case SpeechRecognitionAudioProblem::NoSignal:
           OutputDebugStringW(L"There is no signal.\n");
           break;

       case SpeechRecognitionAudioProblem::None:
       default:
           OutputDebugStringW(L"An error was reported with no information.\n");
           break;
       }
   }
```

Se você não estiver usando classes ref para criar seu aplicativo DirectX, deverá cancelar a assinatura do evento antes de liberar ou recriar o reconhecedor de fala. O HolographicSpeechPromptSample tem uma rotina para interromper o reconhecimento e cancelar a assinatura de eventos.

```
Concurrency::task<void> HolographicSpeechPromptSampleMain::StopCurrentRecognizerIfExists()
   {
       return create_task([this]()
       {
           if (m_speechRecognizer != nullptr)
           {
               return create_task(m_speechRecognizer->StopRecognitionAsync()).then([this]()
               {
                   m_speechRecognizer->RecognitionQualityDegrading -= m_speechRecognitionQualityDegradedToken;

                   if (m_speechRecognizer->ContinuousRecognitionSession != nullptr)
                   {
                       m_speechRecognizer->ContinuousRecognitionSession->ResultGenerated -= m_speechRecognizerResultEventToken;
                   }
               });
           }
           else
           {
               return create_task([this]() { m_speechRecognizer = nullptr; });
           }
       });
   }
```

## <a name="use-speech-synthesis-to-provide-audible-prompts"></a>Usar a síntese de fala para fornecer prompts audíveis

Os exemplos de fala holográfica usam a síntese de fala para fornecer instruções audíveis ao usuário. Esta seção mostra como criar um exemplo de voz sintetizada e, em seguida, reproduzi-lo por meio das APIs de áudio HRTF.

É recomendável fornecer seus próprios prompts de fala ao solicitar a entrada de frase. Os prompts também podem ajudar a indicar quando comandos de fala podem ser falados para um cenário de reconhecimento contínuo. O exemplo a seguir demonstra como usar um sintetizador de fala para fazer isso. Você também pode usar um clipe de voz pré-gravado, uma interface do usuário visual ou outro indicador do que dizer, por exemplo, em cenários em que o prompt não é dinâmico.

Primeiro, crie o objeto SpeechSynthesizer.

```
auto speechSynthesizer = ref new Windows::Media::SpeechSynthesis::SpeechSynthesizer();
```

Você também precisa de uma cadeia de caracteres que inclua o texto a ser sintetizado.

```
// Phrase recognition works best when requesting a phrase or sentence.
   StringReference voicePrompt = L"At the prompt: Say a phrase, asking me to change the cube to a specific color.";
```

A fala é sintetizada de forma assíncrona por meio de SynthesizeTextToStreamAsync. Aqui, iniciamos uma tarefa assíncrona para sintetizar a fala.

```
create_task(speechSynthesizer->SynthesizeTextToStreamAsync(voicePrompt), task_continuation_context::use_current())
       .then([this, speechSynthesizer](task<Windows::Media::SpeechSynthesis::SpeechSynthesisStream^> synthesisStreamTask)
   {
       try
       {
```

A síntese de fala é enviada como um fluxo de byte. Podemos usar esse fluxo de byte para inicializar uma voz XAudio2. Para nossos exemplos de código holográfico, reproduzimos como um efeito de áudio HRTF.

```
Windows::Media::SpeechSynthesis::SpeechSynthesisStream^ stream = synthesisStreamTask.get();

           auto hr = m_speechSynthesisSound.Initialize(stream, 0);
           if (SUCCEEDED(hr))
           {
               m_speechSynthesisSound.SetEnvironment(HrtfEnvironment::Small);
               m_speechSynthesisSound.Start();

               // Amount of time to pause after the audio prompt is complete, before listening
               // for speech input.
               static const float bufferTime = 0.15f;

               // Wait until the prompt is done before listening.
               m_secondsUntilSoundIsComplete = m_speechSynthesisSound.GetDuration() + bufferTime;
               m_waitingForSpeechPrompt = true;
           }
       }
```

Assim como acontece com o reconhecimento de fala, a síntese de fala lançará uma exceção se algo der errado.

```
catch (Exception^ exception)
       {
           PrintWstringToDebugConsole(
               std::wstring(L"Exception while trying to synthesize speech: ") +
               exception->Message->Data() +
               L"\n"
               );

           // Handle exceptions here.
       }
   });
```

## <a name="see-also"></a>Confira também
* [Design do aplicativo de fala](/windows/uwp/design/input/speech-interactions)
* [Exemplo de SpeechRecognitionAndSynthesis](https://github.com/Microsoft/Windows-universal-samples/tree/master/Samples/SpeechRecognitionAndSynthesis)