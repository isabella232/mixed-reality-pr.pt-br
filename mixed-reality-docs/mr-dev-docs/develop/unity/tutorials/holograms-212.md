---
title: Entrada do HoloLens (1ª geração) 212 – Serviço de Voz
description: Siga este passo a passo de codificação usando o Unity, Visual Studio e HoloLens para saber os detalhes dos conceitos de voz.
author: keveleigh
ms.author: kurtie
ms.date: 10/22/2019
ms.topic: article
keywords: holotoolkit, mixedrealitytoolkit, mixedrealitytoolkit-unity, academy, tutorial, voz, HoloLens, Mixed Reality Academy, unity, headset de realidade misturada, headset do windows mixed reality, headset de realidade virtual, Windows 10
ms.openlocfilehash: 75a1d32ae72a07b68fc65c40035109c468adb1080070240827eeb253eb4a03f4
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115207362"
---
# <a name="hololens-1st-gen-input-212-voice"></a>HoloLens (1ª geração) Entrada 212: Voz

>[!IMPORTANT]
>Os tutoriais do Mixed Reality Academy foram projetados com HoloLens (1ª geração), Unity 2017 e Headsets Imersivos de Realidade Misturada em mente.  Dessa forma, achamos que é importante continuar disponibilizando esses tutoriais para os desenvolvedores que ainda buscam obter diretrizes para o desenvolvimento visando esses dispositivos. Esses tutoriais não **_serão_** atualizados com os mais recentes toolsets ou interações que estão sendo usados para HoloLens 2 e podem não ser compatíveis com versões mais recentes do Unity.  Eles serão mantidos para continuar funcionando nos dispositivos compatíveis. [Uma nova série de tutoriais](mrlearning-base.md) foi postada para o HoloLens 2.

[A entrada de](../../../design/voice-input.md) voz nos dá outra maneira de interagir com nossos hologramas. Os comandos de voz funcionam de maneira muito natural e fácil. Projete seus comandos de voz para que eles sejam:

* Natural
* Fácil de lembrar
* Contexto apropriado
* Suficientemente distinto de outras opções dentro do mesmo contexto

>[!VIDEO https://www.youtube.com/embed/BYpYsVFYjdw]

No [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md), utilizamos KeywordRecognizer para criar dois comandos de voz simples. Na Entrada 212 do MR, nos aprofundaremos e aprenderemos a:

* Criar comandos de voz otimizados para o HoloLens de fala.
* Faça com que o usuário saiba quais comandos de voz estão disponíveis.
* Confirme que ouvimos o comando de voz do usuário.
* Entenda o que o usuário está dizendo, usando um Reconhecedor de Ditado.
* Use um Reconhecimento de Gramática para escutar comandos com base em um arquivo SRGS ou Especificação de Gramática de Reconhecimento de Fala.

Neste curso, vamos revisitar o Explorador de Modelos, que foi criado na Entrada [210](holograms-210.md) do MR e na [Entrada do MR 211.](holograms-211.md)

>[!IMPORTANT]
>Os vídeos inseridos em cada um dos capítulos abaixo foram gravados usando uma versão mais antiga do Unity e o Toolkit. Embora as instruções passo a passo sejam precisas e atuais, você pode ver scripts e visuais nos vídeos correspondentes que estão des date. Os vídeos permanecem incluídos para a posteridade e porque os conceitos abordados ainda se aplicam.


## <a name="device-support"></a>Suporte a dispositivos

<table>
<tr>
<th>Curso</th><th style="width:150px"> <a href="/hololens/hololens1-hardware">HoloLens</a></th><th style="width:150px"> <a href="../../../discover/immersive-headset-hardware-details.md">Headsets imersivos</a></th>
</tr><tr>
<td>Entrada do MR 212: Voz</td><td style="text-align: center;"> ✔️</td><td style="text-align: center;"> ✔️</td>
</tr>
</table>

## <a name="before-you-start"></a>Antes de começar

### <a name="prerequisites"></a>Pré-requisitos

* Um Windows 10 computador configurado com as ferramentas [corretas instaladas.](../../../develop/install-the-tools.md)
* Alguma capacidade básica de programação em C#.
* Você deve ter concluído o [MR Basics 101](../../../develop/unity/tutorials/holograms-101.md).
* Você deve ter concluído a [Entrada 210 do MR.](holograms-210.md)
* Você deve ter concluído a [Entrada 211 do MR.](holograms-211.md)
* Um HoloLens configurado [para desenvolvimento.](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#enabling-developer-mode)

### <a name="project-files"></a>Arquivos de projeto

* Baixe os [arquivos](https://github.com/Microsoft/HolographicAcademy/archive/Holograms-212-Voice.zip) exigidos pelo projeto. Requer o Unity 2017.2 ou posterior.
* Desarmá-los na área de trabalho ou em outro local fácil de alcançar.

>[!NOTE]
>Se você quiser ver o código-fonte antes de baixar, ele [estará disponível no GitHub](https://github.com/Microsoft/HolographicAcademy/tree/Holograms-212-Voice).

### <a name="errata-and-notes"></a>Errata e observações

* "Habilitar Apenas Meu Código" precisa ser desabilitado *(* desmarcado ) no Visual Studio em Ferramentas->Opções >Depuração para atingir pontos de interrupção em seu código.

## <a name="unity-setup"></a>Instalação do Unity

### <a name="instructions"></a>Instruções

1. Inicie o Unity.
2. Selecione **Abrir**.
3. Navegue até **a pasta HolographicAcademy-Hologramas-212-Voice** que você não arquivou anteriormente.
4. Encontre e selecione a pasta / **Iniciando o Explorador de Modelos.**
5. Clique no **botão Selecionar** Pasta.
6. No painel **Project,** expanda a **pasta Cenas.**
7. Clique duas vezes **em ModelExplorer** scene para carregá-la no Unity.

### <a name="building"></a>Construção

1. No Unity, selecione **Arquivo > Build Configurações**.
2. Se **Scenes/ModelExplorer** não estiver listado em **Cenas no Build**, clique em Adicionar Cenas **Abertas** para adicionar a cena.
3. Se você estiver desenvolvendo especificamente para HoloLens, de definido **Dispositivo de destino** como **HoloLens**. Caso contrário, deixe-o **em Qualquer dispositivo**.
4. Verifique **se o Tipo** de Build está definido como **D3D** e se **o SDK** está definido como Mais recente instalado **(que** deve ser o SDK 16299 ou mais recente).
5. Clique em **Compilar**.
6. Crie uma **nova pasta** chamada "Aplicativo".
7. Clique com um único clique **na pasta** Aplicativo.
8. Pressione **Selecionar Pasta** e o Unity começará a criar o projeto para Visual Studio.

Quando o Unity for feito, uma Explorador de Arquivos será exibida.

1. Abra a **pasta Aplicativo.**
2. Abra a **Solução de Visual Studio ModelExplorer**.

Se estiver implantando no HoloLens:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de Depurar para **Versão** e do ARM para **x86.**
2. Clique na seta para baixo ao lado do botão Computador Local e selecione **Computador Remoto.**
3. Insira **seu HoloLens IP do dispositivo** e descriptografe o Modo de Autenticação como Universal **(Protocolo Não Criptografado).** Clique em **Selecionar**. Se você não sabe o endereço IP do dispositivo, procure Configurações > Rede & **Internet > Opções Avançadas**.
4. Na barra de menus superior, clique em **Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**. Se esta for a primeira vez que você implanta em seu dispositivo, você precisará [emparelhá-lo com Visual Studio](../../../develop/platform-capabilities-and-apis/using-visual-studio.md#pairing-your-device).
5. Quando o aplicativo for implantado, descarte o **Fitbox** com um **gesto de seleção**.

Se estiver implantando em um headset imersivo:

1. Usando a barra de ferramentas superior no Visual Studio, altere o destino de Depurar para Versão **e** de ARM para **x64**.
2. Certifique-se de que o destino de implantação está definido como **Computador Local.**
3. Na barra de menus superior, clique em **Depurar -> Iniciar Sem depuração** ou pressione **Ctrl + F5**.
4. Quando o aplicativo for implantado, descarte o **Fitbox** e esvaia o gatilho em um controlador de movimento.

>[!NOTE]
>Você pode observar alguns erros vermelhos no painel Visual Studio Erros. É seguro ignorá-los. Alternar para o painel Saída para exibir o progresso real do build. Erros no painel Saída exigirão que você faça uma correção (geralmente eles são causados por um erro em um script).

## <a name="chapter-1---awareness"></a>Capítulo 1 – Reconhecimento

>[!VIDEO https://www.youtube.com/embed/fDwijJWuEc0]

### <a name="objectives"></a>Objetivos

* Aprenda o **design do comando Dos e Don'ts** of voice.
* Use **KeywordRecognizer para** adicionar comandos de voz baseados em olhar.
* Tornar os usuários cientes dos comandos de voz usando comentários do **cursor**.

### <a name="voice-command-design"></a>Design de comando de voz

Neste capítulo, você aprenderá a criar comandos de voz. Ao criar comandos de voz:

#### <a name="do"></a>DO

* Crie comandos concisos. Você não deseja usar "Reproduzir o vídeo selecionado *no momento",* porque esse comando não é conciso e seria facilmente esquecido pelo usuário. Em vez disso, você deve usar: *"reproduzir vídeo"*, porque ele é conciso e tem várias sílabas.
* Use um vocabulário simples. Sempre tente usar palavras e frases comuns que sejam fáceis para o usuário descobrir e se lembrar. Por exemplo, se o seu aplicativo tiver um objeto note que pudesse ser exibido ou oculto da exibição, você não usará o comando *"show letreiro"*, porque "letreiro" é um termo raramente usado. Em vez disso, você usaria o comando: *"mostrar nota"*, para revelar a nota em seu aplicativo.
* Ser consistente. Os comandos de voz devem ser mantidos consistentes em seu aplicativo. Imagine que você tem duas cenas em seu aplicativo e ambas as cenas contêm um botão para fechar o aplicativo. Se a primeira cena usou o comando *"Exit"* para disparar o botão, mas a segunda cena usou o comando *"Close app"*, o usuário vai ficar muito confuso. Se a mesma funcionalidade persistir em vários bastidores, o mesmo comando de voz deverá ser usado para dispará-lo.

#### <a name="dont"></a>Não

* Use comandos de sílaba única. Por exemplo, se você estivesse criando um comando de voz para reproduzir um vídeo, evite usar o comando simples *"Play"*, pois ele é apenas uma única sílaba e pode ser facilmente perdido pelo sistema. Em vez disso, você deve usar: *"reproduzir vídeo"*, porque ele é conciso e tem várias sílabas.
* Use comandos do sistema. O comando *"Select"* é reservado pelo sistema para disparar um evento TAP para o objeto atualmente focalizado. Não use novamente o comando *"Select"* em uma palavra-chave ou frase, pois ele pode não funcionar conforme o esperado. Por exemplo, se o comando de voz para selecionar um cubo em seu aplicativo era *"Selecionar Cubo"*, mas o usuário estava olhando para uma esfera quando estivessem o comando, então a esfera seria selecionada em vez disso. De forma semelhante, os comandos da barra de aplicativos estão habilitados para voz Não use os seguintes comandos de fala em sua exibição do CoreWindow:
    1. Voltar
    2. Ferramenta Scroll
    3. Ferramenta de zoom
    4. Ferramenta de arrastar
    5. Ajustar
    6. Remover
* Use sons semelhantes. Tente evitar o uso de comandos de voz que Rhyme. Se você tivesse um aplicativo de compras com suporte para *"mostrar armazenamento"* e *"mostrar mais"* como comandos de voz, convém desabilitar um dos comandos enquanto o outro estava em uso. Por exemplo, você pode usar o botão *"mostrar armazenamento"* para abrir o repositório e, em seguida, desabilitar esse comando quando o repositório foi exibido para que o comando *"mostrar mais"* pudesse ser usado para navegação.

### <a name="instructions"></a>Instruções

* No painel **hierarquia** do Unity, use a ferramenta de pesquisa para localizar o objeto **holoComm_screen_mesh** .
* Clique duas vezes no objeto **holoComm_screen_mesh** para exibi-lo na **cena**. Essa é a inspeção do Astronaut, que responderá aos nossos comandos de voz.
* No painel **Inspetor** , localize o componente **fonte de entrada de fala (script)** .
* Expanda a seção **palavras-chave** para ver o comando de voz com suporte: **abrir Communicator**.
* Clique no engrenagem no lado direito e selecione **Editar script**.
* Explore o **SpeechInputSource. cs** para entender como ele usa o **KeywordRecognizer** para adicionar comandos de voz.

### <a name="build-and-deploy"></a>Compilar e implantar

* no Unity, use o **arquivo > Build Configurações** para recompilar o aplicativo.
* Abra a pasta do **aplicativo** .
* abra a **solução de Visual Studio ModelExplorer**.

(se você já criou/implantou esse projeto no Visual Studio durante a instalação, poderá abrir essa instância do VS e clicar em ' recarregar tudo ' quando solicitado).

* em Visual Studio, clique em **depurar-> iniciar sem depuração** ou pressione **Ctrl + F5**.
* depois que o aplicativo for implantado no HoloLens, descartar a caixa ajustar usando o gesto de [toque do ar](../../../design/gaze-and-commit.md#composite-gestures) .
* Olhar na inspeção do Astronaut.
* Quando o relógio tiver foco, verifique se o cursor é alterado para um microfone. Isso fornece comentários que o aplicativo está ouvindo por comandos de voz.
* Verifique se uma dica de ferramenta aparece na inspeção. isso ajuda os usuários a descobrir o comando *"abrir Communicator"* .
* enquanto nuvens no relógio, diga *"abrir Communicator"* para abrir o painel do Communicator.

## <a name="chapter-2---acknowledgement"></a>Capítulo 2-confirmação

>[!VIDEO https://www.youtube.com/embed/87ViteoPpyU]

### <a name="objectives"></a>Objetivos

* Registre uma mensagem usando a entrada do microfone.
* Envie comentários para o usuário que o aplicativo está ouvindo em sua voz.

>[!NOTE]
>A capacidade do **microfone** deve ser declarada para um aplicativo gravar do microfone. Isso é feito para você já no Sr Input 212, mas tenha isso em mente para seus próprios projetos.
>
>1. no Editor do Unity, vá para as configurações do player navegando para "editar > Project Configurações > player"
>2. clique na guia "Plataforma Universal do Windows"
>3. na seção "publicando Configurações > recursos", verifique a capacidade do **microfone**

### <a name="instructions"></a>Instruções

* No painel **hierarquia** do Unity, verifique se o objeto **holoComm_screen_mesh** está selecionado.
* No painel **Inspetor** , localize o componente **Astronaut Watch (script)** .
* clique no cubo azul pequeno, que é definido como o valor da propriedade **Communicator pré-fabricado** .
* no painel de **Project** , o **Communicator** pré-fabricado agora deve ter foco.
* clique no **Communicator** pré-fabricado no painel de **Project** para exibir seus componentes no **inspetor**.
* Examine o componente do **Gerenciador de microfone (script)** , isso nos permitirá registrar a voz do usuário.
* observe que o objeto **Communicator** tem um componente de **manipulador de entrada de fala (Script)** para responder ao comando **enviar mensagem** .
* examine o componente **Communicator (Script)** e clique duas vezes no Script para abri-lo no Visual Studio.

Communicator. cs é responsável por definir os estados de botão apropriados no dispositivo do Communicator. Isso permitirá que os usuários registrem uma mensagem, a reproduzam e enviem a mensagem para o Astronaut. Ele também iniciará e interromperá um formulário de onda animado para confirmar ao usuário que sua voz foi ouvido.

* em **Communicator. cs**, exclua as seguintes linhas (81 e 82) do método **Start** . Isso habilitará o botão ' registro ' no Communicator.

```cs
// TODO: 2.a Delete the following two lines:
RecordButton.SetActive(false);
MessageUIRenderer.gameObject.SetActive(false);
```

### <a name="build-and-deploy"></a>Compilar e implantar

* em Visual Studio, recompile seu aplicativo e implante-o no dispositivo.
* olhar na inspeção do astronaut e diga *"abrir Communicator"* para mostrar o Communicator.
* Pressione o botão **gravar** (microfone) para começar a gravar uma mensagem verbal para o Astronaut.
* Comece a falar e verifique se a animação ondulada é reproduzida no Communicator, que fornece comentários para o usuário de que a voz é ouvida.
* Pressione o botão **parar** (quadrado à esquerda) e verifique se a animação de onda interrompe a execução.
* Pressione o botão **reproduzir** (triângulo à direita) para reproduzir a mensagem gravada e ouvi-la no dispositivo.
* Pressione o botão **parar** (quadrado direito) para parar a reprodução da mensagem gravada.
* Diga *"Enviar mensagem"* para fechar o Communicator e receber uma resposta "mensagem recebida" do Astronaut.

## <a name="chapter-3---understanding-and-the-dictation-recognizer"></a>Capítulo 3-noções básicas e o reconhecedor de ditador

>[!VIDEO https://www.youtube.com/embed/TIMddr-HqEU]

### <a name="objectives"></a>Objetivos

* Use o reconhecedor de ditado para converter a fala do usuário em texto.
* Mostre os resultados hipotéticos e finais do reconhecedor de ditado no Communicator.

Neste capítulo, usaremos o reconhecedor de ditado para criar uma mensagem para o Astronaut. Ao usar o reconhecedor de ditado, tenha em mente que:

* Você deve estar conectado a WiFi para que o reconhecedor de ditado funcione.
* Os tempos limite ocorrem após um determinado período de tempo. Há dois tempos limite a serem cientes:
  * Se o reconhecedor for iniciado e não ouvir nenhum áudio pelos primeiros cinco segundos, ele atingirá o tempo limite.
  * Se o reconhecedor tiver dado um resultado, mas, em seguida, ouvir silêncio por vinte segundos, ele atingirá o tempo limite.
* Somente um tipo de reconhecedor (palavra-chave ou ditado) pode ser executado de cada vez.

>[!NOTE]
>A capacidade do **microfone** deve ser declarada para um aplicativo gravar do microfone. Isso é feito para você já no Sr Input 212, mas tenha isso em mente para seus próprios projetos.
>
>1. no Editor do Unity, vá para as configurações do player navegando para "editar > Project Configurações > player"
>2. clique na guia "Plataforma Universal do Windows"
>3. na seção "publicando Configurações > recursos", verifique a capacidade do **microfone**

### <a name="instructions"></a>Instruções

Vamos editar **MicrophoneManager.cs** para usar o Reconhecedor de Ditado. Isso é o que adicionaremos:

1. Quando o **botão Registrar** for pressionado, iniciaremos **o DictationRecognizer.**
2. Mostre a **hipótese do** que o DictationRecognizer entendeu.
3. Bloqueie **os resultados** do que o DictationRecognizer entendeu.
4. Verifique se há tempos de vida do DictationRecognizer.
5. Quando o **botão Parar** for pressionado ou a sessão de microfone for pressionada, pare **o DictationRecognizer.**
6. Reinicie **o KeywordRecognizer**, que escutará o **comando Enviar Mensagem.**

Vamos começar. Conclua todos os exercícios de codificação para 3.a em **MicrophoneManager.cs** ou copie e copie e copie o código concluído encontrado abaixo:

```cs
// Copyright (c) Microsoft Corporation. All rights reserved.
// Licensed under the MIT License. See LICENSE in the project root for license information.

using System.Collections;
using System.Text;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.Windows.Speech;

namespace Academy
{
    public class MicrophoneManager : MonoBehaviour
    {
        [Tooltip("A text area for the recognizer to display the recognized strings.")]
        [SerializeField]
        private Text dictationDisplay;

        private DictationRecognizer dictationRecognizer;

        // Use this string to cache the text currently displayed in the text box.
        private StringBuilder textSoFar;

        // Using an empty string specifies the default microphone.
        private static string deviceName = string.Empty;
        private int samplingRate;
        private const int messageLength = 10;

        // Use this to reset the UI once the Microphone is done recording after it was started.
        private bool hasRecordingStarted;

        void Awake()
        {
            /* TODO: DEVELOPER CODING EXERCISE 3.a */

            // 3.a: Create a new DictationRecognizer and assign it to dictationRecognizer variable.
            dictationRecognizer = new DictationRecognizer();

            // 3.a: Register for dictationRecognizer.DictationHypothesis and implement DictationHypothesis below
            // This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
            dictationRecognizer.DictationHypothesis += DictationRecognizer_DictationHypothesis;

            // 3.a: Register for dictationRecognizer.DictationResult and implement DictationResult below
            // This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
            dictationRecognizer.DictationResult += DictationRecognizer_DictationResult;

            // 3.a: Register for dictationRecognizer.DictationComplete and implement DictationComplete below
            // This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
            dictationRecognizer.DictationComplete += DictationRecognizer_DictationComplete;

            // 3.a: Register for dictationRecognizer.DictationError and implement DictationError below
            // This event is fired when an error occurs.
            dictationRecognizer.DictationError += DictationRecognizer_DictationError;

            // Query the maximum frequency of the default microphone. Use 'unused' to ignore the minimum frequency.
            int unused;
            Microphone.GetDeviceCaps(deviceName, out unused, out samplingRate);

            // Use this string to cache the text currently displayed in the text box.
            textSoFar = new StringBuilder();

            // Use this to reset the UI once the Microphone is done recording after it was started.
            hasRecordingStarted = false;
        }

        void Update()
        {
            // 3.a: Add condition to check if dictationRecognizer.Status is Running
            if (hasRecordingStarted && !Microphone.IsRecording(deviceName) && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                // Reset the flag now that we're cleaning up the UI.
                hasRecordingStarted = false;

                // This acts like pressing the Stop button and sends the message to the Communicator.
                // If the microphone stops as a result of timing out, make sure to manually stop the dictation recognizer.
                // Look at the StopRecording function.
                SendMessage("RecordStop");
            }
        }

        /// <summary>
        /// Turns on the dictation recognizer and begins recording audio from the default microphone.
        /// </summary>
        /// <returns>The audio clip recorded from the microphone.</returns>
        public AudioClip StartRecording()
        {
            // 3.a Shutdown the PhraseRecognitionSystem. This controls the KeywordRecognizers
            PhraseRecognitionSystem.Shutdown();

            // 3.a: Start dictationRecognizer
            dictationRecognizer.Start();

            // 3.a Uncomment this line
            dictationDisplay.text = "Dictation is starting. It may take time to display your text the first time, but begin speaking now...";

            // Set the flag that we've started recording.
            hasRecordingStarted = true;

            // Start recording from the microphone for 10 seconds.
            return Microphone.Start(deviceName, false, messageLength, samplingRate);
        }

        /// <summary>
        /// Ends the recording session.
        /// </summary>
        public void StopRecording()
        {
            // 3.a: Check if dictationRecognizer.Status is Running and stop it if so
            if (dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                dictationRecognizer.Stop();
            }

            Microphone.End(deviceName);
        }

        /// <summary>
        /// This event is fired while the user is talking. As the recognizer listens, it provides text of what it's heard so far.
        /// </summary>
        /// <param name="text">The currently hypothesized recognition.</param>
        private void DictationRecognizer_DictationHypothesis(string text)
        {
            // 3.a: Set DictationDisplay text to be textSoFar and new hypothesized text
            // We don't want to append to textSoFar yet, because the hypothesis may have changed on the next event
            dictationDisplay.text = textSoFar.ToString() + " " + text + "...";
        }

        /// <summary>
        /// This event is fired after the user pauses, typically at the end of a sentence. The full recognized string is returned here.
        /// </summary>
        /// <param name="text">The text that was heard by the recognizer.</param>
        /// <param name="confidence">A representation of how confident (rejected, low, medium, high) the recognizer is of this recognition.</param>
        private void DictationRecognizer_DictationResult(string text, ConfidenceLevel confidence)
        {
            // 3.a: Append textSoFar with latest text
            textSoFar.Append(text + ". ");

            // 3.a: Set DictationDisplay text to be textSoFar
            dictationDisplay.text = textSoFar.ToString();
        }

        /// <summary>
        /// This event is fired when the recognizer stops, whether from Stop() being called, a timeout occurring, or some other error.
        /// Typically, this will simply return "Complete". In this case, we check to see if the recognizer timed out.
        /// </summary>
        /// <param name="cause">An enumerated reason for the session completing.</param>
        private void DictationRecognizer_DictationComplete(DictationCompletionCause cause)
        {
            // If Timeout occurs, the user has been silent for too long.
            // With dictation, the default timeout after a recognition is 20 seconds.
            // The default timeout with initial silence is 5 seconds.
            if (cause == DictationCompletionCause.TimeoutExceeded)
            {
                Microphone.End(deviceName);

                dictationDisplay.text = "Dictation has timed out. Please press the record button again.";
                SendMessage("ResetAfterTimeout");
            }
        }

        /// <summary>
        /// This event is fired when an error occurs.
        /// </summary>
        /// <param name="error">The string representation of the error reason.</param>
        /// <param name="hresult">The int representation of the hresult.</param>
        private void DictationRecognizer_DictationError(string error, int hresult)
        {
            // 3.a: Set DictationDisplay text to be the error string
            dictationDisplay.text = error + "\nHRESULT: " + hresult;
        }

        /// <summary>
        /// The dictation recognizer may not turn off immediately, so this call blocks on
        /// the recognizer reporting that it has actually stopped.
        /// </summary>
        public IEnumerator WaitForDictationToStop()
        {
            while (dictationRecognizer != null && dictationRecognizer.Status == SpeechSystemStatus.Running)
            {
                yield return null;
            }
        }
    }
}
```

### <a name="build-and-deploy"></a>Compilar e implantar

* Recomar Visual Studio e implantar em seu dispositivo.
* Descarte a caixa de ajuste com um gesto de toque de ar.
* Observe o relógio do astronautas e diga *"Abrir Communicator".*
* Selecione o **botão** Gravar (microfone) para registrar sua mensagem.
* Comece a falar. O **Reconhecedor de Ditado interpretará** sua fala e mostrará o texto hipótesedo no comunicador.
* Tente dizer *"Enviar Mensagem"* enquanto você está gravando uma mensagem. Observe que o **Reconhecedor de Palavra-chave** não responde porque o **Reconhecedor de** Ditado ainda está ativo.
* Pare de falar por alguns segundos. Observe como o Reconhecedor de Ditado conclui sua hipótese e mostra o resultado final.
* Comece a falar e, em seguida, pause por 20 segundos. Isso fará com que **o Reconhecedor de** Ditado seja o tempo-final.
* Observe que o **Reconhecedor de** Palavras-chave é reabilitar após o tempo acima. O comunicador agora responderá aos comandos de voz.
* Diga *"Enviar Mensagem"* para enviar a mensagem ao astronautas.

## <a name="chapter-4---grammar-recognizer"></a>Capítulo 4 – Reconhecedor de Gramática

>[!VIDEO https://www.youtube.com/embed/J2dYJNSvv18]

### <a name="objectives"></a>Objetivos

* Use o Reconhecimento de Gramática para reconhecer a fala do usuário de acordo com um arquivo SRGS ou Especificação de Gramática de Reconhecimento de Fala.

>[!NOTE]
>A **funcionalidade** microfone deve ser declarada para que um aplicativo seja registrado do microfone. Isso é feito para você já na Entrada 212 do MR, mas tenha isso em mente para seus próprios projetos.
>
>1. No Editor do Unity, acesse as configurações do player navegando até "Editar > Project Configurações > Player"
>2. Clique na guia "Plataforma Windows Universal"
>3. Na seção "Funcionalidades Configurações > publicação", verifique a **funcionalidade microfone**

### <a name="instructions"></a>Instruções

1. No painel **Hierarquia,** pesquise **por Jetpack_Center** e selecione-o.
2. Procure o script **Tagalong Action** no **painel Inspetor.**
3. Clique no pequeno círculo à direita do campo **Objeto para Marcar Ao Longo.**
4. Na janela que aparece, pesquise **SRGSToolbox** e selecione-a na lista.
5. Dê uma olhada no **arquivoSRGSColor.xml** na pasta **StreamingAssets.**
    1. A especificação de design SRGS pode ser encontrada no site do W3C [aqui](https://www.w3.org/TR/speech-grammar/).

Em nosso arquivo SRGS, temos três tipos de regras:

* Uma regra que permite que você diga uma cor de uma lista de doze cores.
* Três regras que escutam uma combinação da regra de cores e uma das três formas.
* A regra raiz, colorChooser, que escuta qualquer combinação das três regras de "cor + forma". As formas podem ser ditos em qualquer ordem e em qualquer quantidade, de apenas uma a todas as três. Essa é a única regra que é escutada, pois ela é especificada como a regra raiz na parte superior do arquivo na &lt; marcação de gramática &gt; inicial.

### <a name="build-and-deploy"></a>Compilar e implantar

* Recomposicionar o aplicativo no Unity e, em seguida, criar e implantar do Visual Studio para experimentar o aplicativo no HoloLens.
* Descarte a caixa de ajuste com um gesto de toque de ar.
* Acarpeia o jetpack do astronautas e execute um gesto de toque no ar.
* Comece a falar. O **Reconhecedor de Gramática** interpretará sua fala e alterará as cores das formas com base no reconhecimento. Um comando de exemplo é "círculo azul, quadrado amarelo".
* Execute outro gesto de toque de ar para descartar a caixa de ferramentas.

## <a name="the-end"></a>Fim

Parabéns! Agora você concluiu a **Entrada do MR 212: Voz.**

* Você conhece os comandos Dos e Don'ts de voz.
* Você viu como as dicas de ferramenta foram empregadas para tornar os usuários cientes dos comandos de voz.
* Você viu vários tipos de comentários usados para confirmar que a voz do usuário foi escutada.
* Você sabe como alternar entre o Reconhecedor de Palavras-Chave e o Reconhecedor de Ditado e como esses dois recursos entendem e interpretam sua voz.
* Você aprendeu a usar um arquivo SRGS e o Reconhecimento De Gramática para reconhecimento de fala em seu aplicativo.