---
title: Entrada de voz no Unity
description: Saiba como o Unity expõe três maneiras de adicionar entrada de voz, reconhecimento de fala e ditado ao seu aplicativo Windows Mixed Reality.
author: thetuvix
ms.author: alexturn
ms.date: 03/21/2018
ms.topic: article
keywords: Entrada de voz, KeywordRecognizer, GrammarRecognizer, microfone, ditado, voz, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, MRTK, kit de ferramentas de realidade misturada
ms.openlocfilehash: c062289a1a26365528a86761b6b68a9a24041f7c
ms.sourcegitcommit: ac315c1d35f2b9c431e79bc3f1212215301bb867
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105550376"
---
# <a name="voice-input-in-unity"></a>Entrada de voz no Unity

> [!CAUTION]
> Antes de começar, considere usar o plug-in do Unity para o SDK dos serviços de fala cognitiva. O plug-in tem melhores resultados de precisão de fala e acesso fácil à decodificação de fala em texto, bem como a recursos de fala avançados, como diálogo, interação baseada em intenção, tradução, síntese de conversão de texto em fala e reconhecimento de fala em idioma natural. Para começar, confira o [exemplo e a documentação](/azure/cognitive-services/speech-service/quickstart-csharp-unity).

O Unity expõe três maneiras de adicionar [entrada de voz](../../design/voice-input.md) ao aplicativo do Unity, os dois primeiros tipos de PhraseRecognizer:
* O `KeywordRecognizer` fornece ao seu aplicativo uma matriz de comandos de cadeia de caracteres a serem escutados
* O `GrammarRecognizer` fornece ao seu aplicativo um arquivo SRGS que define uma gramática específica a ser escutada
* O `DictationRecognizer` permite que seu aplicativo Ouça qualquer palavra e forneça ao usuário uma anotação ou outra exibição de sua fala

> [!NOTE]
> O reconhecimento de ditado e de frase não pode ser tratado ao mesmo tempo. Se um GrammarRecognizer ou KeywordRecognizer estiver ativo, um DictationRecognizer não poderá estar ativo e vice-versa.

## <a name="enabling-the-capability-for-voice"></a>Habilitando o recurso de voz

A capacidade do **microfone** deve ser declarada para um aplicativo usar entrada de voz.
1. No editor do Unity, navegue até **Editar configurações do projeto > > Player**
2. Selecione a guia **Windows Store**
3. Na seção **configurações de publicação > recursos** , verifique o recurso de **microfone**
4. Conceder permissões ao aplicativo para acesso ao microfone em seu dispositivo de HoloLens
    * Você será solicitado a fazer isso na inicialização do dispositivo, mas se você clicou acidentalmente em "não", poderá alterar as permissões nas configurações do dispositivo

## <a name="phrase-recognition"></a>Reconhecimento de frases

Para permitir que seu aplicativo Ouça frases específicas faladas pelo usuário e, em seguida, execute alguma ação, você precisa:
1. Especificar quais frases escutar usando um `KeywordRecognizer` ou `GrammarRecognizer`
2. Manipular o `OnPhraseRecognized` evento e tomar medidas correspondentes à frase reconhecida

### <a name="keywordrecognizer"></a>KeywordRecognizer

**Namespace:** *UnityEngine. Windows. Speech*<br>
**Tipos:** *KeywordRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

Precisaremos de algumas instruções de uso para salvar alguns pressionamentos de tecla:

```
using UnityEngine.Windows.Speech;
using System.Collections.Generic;
using System.Linq;
```

Em seguida, vamos adicionar alguns campos à sua classe para armazenar o reconhecedor e o dicionário de ação de >de palavra-chave:

```
KeywordRecognizer keywordRecognizer;
Dictionary<string, System.Action> keywords = new Dictionary<string, System.Action>();
```

Agora, adicione uma palavra-chave ao dicionário, por exemplo, em um `Start()` método. Estamos adicionando a palavra-chave "Activate" neste exemplo:

```
//Create keywords for keyword recognizer
keywords.Add("activate", () =>
{
    // action to be performed when this keyword is spoken
});
```

Crie o reconhecedor de palavra-chave e diga a ele o que desejamos reconhecer:

```
keywordRecognizer = new KeywordRecognizer(keywords.Keys.ToArray());
```

Registre-se agora para o `OnPhraseRecognized` evento

```
keywordRecognizer.OnPhraseRecognized += KeywordRecognizer_OnPhraseRecognized;
```

Um manipulador de exemplo é:

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

Por fim, comece a reconhecer!

```
keywordRecognizer.Start();
```

### <a name="grammarrecognizer"></a>GrammarRecognizer

**Namespace:** *UnityEngine. Windows. Speech*<br>
**Tipos**: *GrammarRecognizer*, *PhraseRecognizedEventArgs*, *SpeechError*, *SpeechSystemStatus*

O GrammarRecognizer será usado se você estiver especificando a gramática de reconhecimento usando o SRGS. Isso pode ser útil se seu aplicativo tiver mais do que apenas algumas palavras-chave, se você quiser reconhecer frases mais complexas ou se quiser ativar e desativar facilmente conjuntos de comandos. Consulte: [criar gramáticas usando o XML SRGS](/previous-versions/office/developer/speech-technologies/hh378349(v=office.14)) para informações de formato de arquivo.

Quando você tiver sua gramática SRGS e ele estiver em seu projeto em uma [pasta StreamingAssets](https://docs.unity3d.com/Manual/StreamingAssets.html):

```
<PROJECT_ROOT>/Assets/StreamingAssets/SRGS/myGrammar.xml
```

Crie um `GrammarRecognizer` e passe o caminho para o arquivo SRGS:

```
private GrammarRecognizer grammarRecognizer;
grammarRecognizer = new GrammarRecognizer(Application.streamingDataPath + "/SRGS/myGrammar.xml");
```

Registre-se agora para o `OnPhraseRecognized` evento

```
grammarRecognizer.OnPhraseRecognized += grammarRecognizer_OnPhraseRecognized;
```

Você receberá um retorno de chamada contendo as informações especificadas na gramática SRGS, que você pode manipular adequadamente. A maioria das informações importantes será fornecida na `semanticMeanings` matriz.

```
private void Grammar_OnPhraseRecognized(PhraseRecognizedEventArgs args)
{
    SemanticMeaning[] meanings = args.semanticMeanings;
    // do something
}
```

Por fim, comece a reconhecer!

```
grammarRecognizer.Start();
```

## <a name="dictation"></a>Ditado

**Namespace:** *UnityEngine. Windows. Speech*<br>
**Tipos**: *DictationRecognizer*, *SpeechError*, *SpeechSystemStatus*

Use o `DictationRecognizer` para converter a fala do usuário em texto. O DictationRecognizer expõe a funcionalidade de [ditado](../../design/voice-input.md#dictation) e dá suporte ao registro e à escuta de eventos de hipótese e de expressão concluídas, para que você possa fornecer comentários ao seu usuário enquanto eles falam e depois. `Start()` e `Stop()` métodos respectivamente habilitam e desabilitam o reconhecimento de ditado. Depois de feito com o reconhecedor, ele deve ser descartado usando o `Dispose()` para liberar os recursos que ele usa. Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho extra se eles não forem liberados antes disso.

Há apenas algumas etapas necessárias para começar a usar o ditado:
1. Criar um novo `DictationRecognizer`
2. Manipular eventos de ditado
3. Iniciar o DictationRecognizer

### <a name="enabling-the-capability-for-dictation"></a>Habilitando o recurso de ditado

Os recursos de cliente e **microfone** da **Internet** devem ser declarados para que um aplicativo use o ditado:
1. No editor do Unity, vá para **Editar configurações do projeto > > Player**
2. Selecione na guia **Windows Store**
3. Na seção **configurações de publicação > recursos** , verifique o recurso **internetclient**
    * Opcionalmente, se você ainda não habilitou o microfone, verifique a capacidade do **microfone**
4. Conceda permissões ao aplicativo para acesso ao microfone no seu dispositivo HoloLens se você ainda não
    * Você será solicitado a fazer isso na inicialização do dispositivo, mas se você clicou acidentalmente em "não", poderá alterar as permissões nas configurações do dispositivo

### <a name="dictationrecognizer"></a>DictationRecognizer

Crie um DictationRecognizer da seguinte maneira:

```
dictationRecognizer = new DictationRecognizer();
```

Há quatro eventos de ditado que podem ser assinados e manipulados para implementar o comportamento do ditado.
1. `DictationResult`
2. `DictationComplete`
3. `DictationHypothesis`
4. `DictationError`

**DictationResult**

Esse evento é acionado depois que o usuário pausa, normalmente no final de uma sentença. A cadeia de caracteres totalmente reconhecida é retornada aqui.

Primeiro, assine o `DictationResult` evento:

```
dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;
```

Em seguida, manipule o retorno de chamada DictationResult:

```
private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
{
    // do something
}
```

**DictationHypothesis**

Esse evento é acionado continuamente enquanto o usuário está conversando. Como o reconhecedor Ouve, ele fornece texto do que ele é ouvido até agora.

Primeiro, assine o `DictationHypothesis` evento:

```
dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;
```

Em seguida, manipule o retorno de chamada DictationHypothesis:

```
private void DictationRecognizer_DictationHypothesis(string text)
{
    // do something
}
```

**DictationComplete**

Esse evento é acionado quando o reconhecedor é interrompido, independentemente de Stop () ser chamado, um tempo limite de ocorrência ou algum outro erro.

Primeiro, assine o `DictationComplete` evento:

```
dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;
```

Em seguida, manipule o retorno de chamada DictationComplete:

```
private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
{
   // do something
}
```

**DictationError**

Esse evento é acionado quando ocorre um erro.

Primeiro, assine o `DictationError` evento:

```
dictationRecognizer.DictationError += DictationRecognizer_DictationError;
```

Em seguida, manipule o retorno de chamada DictationError:

```
private void DictationRecognizer_DictationError(string error, int hresult)
{
    // do something
}
```

Depois de assinar e tratar os eventos de ditado sobre os quais você se preocupa, inicie o reconhecedor de ditado para começar a receber eventos.

```
dictationRecognizer.Start();
```

Se você não quiser mais manter o DictationRecognizer, precisará cancelar a assinatura dos eventos e descartar o DictationRecognizer.

```
dictationRecognizer.DictationResult -= DictationRecognizer_DictationResult;
dictationRecognizer.DictationComplete -= DictationRecognizer_DictationComplete ;
dictationRecognizer.DictationHypothesis -= DictationRecognizer_DictationHypothesis ;
dictationRecognizer.DictationError -= DictationRecognizer_DictationError ;
dictationRecognizer.Dispose();
```

**Dicas**
* `Start()` e `Stop()` métodos respectivamente habilitam e desabilitam o reconhecimento de ditado.
* Depois de feito com o reconhecedor, ele deve ser descartado usando o `Dispose()` para liberar os recursos que ele usa. Ele liberará esses recursos automaticamente durante a coleta de lixo com um custo de desempenho extra se eles não forem liberados antes disso.
* Os tempos limite ocorrem após um determinado período de tempo. Você pode verificar esses tempos limite no `DictationComplete` evento. Há dois tempos limite a serem cientes:
   1. Se o reconhecedor for iniciado e não ouvir áudio pelos primeiros cinco segundos, ele atingirá o tempo limite.
   2. Se o reconhecedor tiver dado um resultado, mas, em seguida, ouve silêncio por 20 segundos, ele atingirá o tempo limite.

## <a name="using-both-phrase-recognition-and-dictation"></a>Usando o reconhecimento de frase e o ditado

Se você quiser usar o reconhecimento de frase e o ditado em seu aplicativo, será necessário desligar completamente um antes para poder iniciar o outro. Se você tiver vários KeywordRecognizers em execução, poderá desligá-los de uma só vez com:

```
PhraseRecognitionSystem.Shutdown();
```

Você pode chamar `Restart()` para restaurar todos os reconhecedores ao estado anterior depois que o DictationRecognizer for interrompido:

```
PhraseRecognitionSystem.Restart();
```

Você também pode apenas iniciar um KeywordRecognizer, que reiniciará o PhraseRecognitionSystem também.

## <a name="voice-input-in-mixed-reality-toolkit"></a>Entrada de voz no kit de ferramentas de realidade misturada

Você pode encontrar exemplos de MRTK para entrada de voz nas seguintes cenas de demonstração:
* [Ditado](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Dictation)
* [Fala](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/mrtk_development/Assets/MRTK/Examples/Demos/Input/Scenes/Speech)

## <a name="next-development-checkpoint"></a>Próximo ponto de verificação de desenvolvimento

Se você estiver seguindo a jornada do ponto de verificação de desenvolvimento do Unity que apresentamos, a próxima tarefa está explorando os recursos e as APIs da plataforma de realidade misturada:

> [!div class="nextstepaction"]
> [Experiências compartilhadas](shared-experiences-in-unity.md)

Você sempre pode voltar para os [pontos de verificação de desenvolvimento do Unity](unity-development-overview.md#2-core-building-blocks) a qualquer momento.