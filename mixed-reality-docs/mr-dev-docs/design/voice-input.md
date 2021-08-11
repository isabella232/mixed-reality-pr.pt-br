---
title: Entrada de voz
description: a entrada de voz é uma entrada principal para HoloLens e Windows Mixed Reality headsets de imersão. a voz pode ser usada para comandos, ditado, Cortana e muito mais.
author: hak0n
ms.author: hakons
ms.date: 10/03/2019
ms.topic: article
keywords: ggv, voz, cortana, fala, entrada, headset de realidade misturada, headset de realidade mista do windows, headset da realidade virtual, HoloLens, MRTK, realidade misturada Toolkit, olhar
ms.openlocfilehash: f7ae7ddd40fff3da660cc747d01d258b9fb0eb31f3b024ec77efd2b560e037d7
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115223676"
---
# <a name="voice-input"></a>Entrada de voz

![Entrada de voz](images/UX_Hero_VoiceCommand.jpg)

A voz é uma das principais formas de entrada no HoloLens. Ele permite que você comando diretamente um holograma sem precisar usar [gestos de mão](gaze-and-commit.md#composite-gestures). A entrada de voz pode ser uma maneira natural de comunicar sua intenção. A voz é especialmente boa na passagem de interfaces complexas, pois permite que os usuários recortem os menus aninhados com um único comando.

a entrada de voz é alimentada pelo [mesmo mecanismo](/windows/uwp/design/input/speech-recognition) que dá suporte à fala em todos os _aplicativos de Windows Universal_. no HoloLens, o reconhecimento de fala sempre funcionará na Windows idioma de exibição configurada em seu dispositivo Configurações. 

<br>

## <a name="voice-and-gaze&quot;></a>Voz e olhar

Quando você estiver usando comandos de voz, o olhar de cabeça ou de olho é o mecanismo de direcionamento típico, seja com um cursor para &quot;selecionar&quot; ou para canalizar o comando para um aplicativo que você está vendo. Talvez nem seja necessário mostrar qualquer cursor olhar _(&quot;vê-lo, digamos")_. Alguns comandos de voz não exigem um destino, como "ir para iniciar" ou "Ei Cortana".

<br>

<iframe width="940" height="530" src="https://www.youtube.com/embed/eHMkOpNUtR8" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>


## <a name="device-support"></a>Suporte a dispositivos

<table>
    <colgroup>
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    <col width="25%" />
    </colgroup>
    <tr>
        <td><strong>Recurso</strong></td>
        <td><a href="/hololens/hololens1-hardware"><strong>HoloLens (1ª geração)</strong></a></td>
        <td><a href="/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Entrada de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (com microfone)</td>
    </tr>
</table>

## <a name="the-select-command"></a>O comando "Select"

**HoloLens (1ª geração)**

Mesmo sem adicionar especificamente suporte de voz ao seu aplicativo, os usuários podem ativar os hologramas simplesmente dizendo o comando de voz do sistema "Select". isso se comporta da mesma forma que um [toque de ar](gaze-and-commit.md#composite-gestures) em HoloLens, pressionando o botão selecionar no [HoloLens clicador](/hololens/hololens1-clicker)ou pressionando o gatilho em um [controlador de movimento de Windows Mixed Reality](motion-controllers.md). Você ouvirá um som e verá uma dica de ferramenta com "Select" aparecer como confirmação. "Select" é habilitado por um algoritmo de detecção de palavra-chave de baixa energia, o que significa que você pode dizer a ele a qualquer momento com impacto mínimo na vida útil da bateria. Você pode até mesmo dizer "selecionar" com suas mãos no seu lado.

<br>

---

:::row:::
    :::column:::
        **HoloLens 2**<br><br>
        para usar o comando de voz "select" no HoloLens 2, primeiro você precisa abrir o cursor olhar para usar como um ponteiro. O comando para trazê-lo é fácil de lembrar, apenas digamos, "Select".<br><br>
        Para sair do modo, use suas mãos novamente por Air tocando, abordando um botão com seus dedos ou usando o gesto do sistema.<br>
        <br> 
        *Imagem: Diga "selecionar" para usar o comando de voz para seleção*
    :::column-end:::
        :::column:::
       ![Um usuário pode dizer "selecionar" para usar o comando de voz para uma seleção.](images/kma-voice-select-00170.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hey-cortana"></a>Ei Cortana

você pode dizer "ei Cortana" para abrir Cortana a qualquer momento. Você não precisa esperar que ela pareça continuar perguntando sua pergunta ou dando a ela uma instrução. por exemplo, tente dizer "ei Cortana, qual é o clima?" como uma única frase. para obter mais informações sobre Cortana e o que você pode fazer, pergunte a ela! diga "ei Cortana, o que eu posso dizer?" e ela receberá uma lista de comandos de trabalho e sugeridos. se você já estiver no aplicativo Cortana, selecione o **?** na barra lateral para extrair esse mesmo menu.

**comandos específicos do HoloLens**
* "O que posso falar?"
* "Ir para o início"-em vez de [cair](system-gesture.md#bloom) para chegar ao [menu iniciar](../discover/navigating-the-windows-mixed-reality-home.md#start-menu)
* "Iniciar <app> "
* "Mover <app> aqui"
* "Tirar uma foto"
* "Iniciar gravação"
* "Parar gravação"
* "Mostrar lado raio"
* "Ocultar mão raio"
* "Aumentar o brilho"
* "Diminuir o brilho"
* "Aumentar o volume"
* "Diminuir o volume"
* "Mudo" ou "desativar mudo"
* "Desligar o dispositivo"
* "Reiniciar o dispositivo"
* "Ir para o estado de suspensão"
* "Qual é o tempo?"
* "A quantidade de bateria que resta?"

<br>

---

:::row:::
    :::column:::
        ## <a name="see-it-say-itbr"></a>"Vê-lo, digamos"<br>
        HoloLens tem um modelo "vê-lo, digamos" para entrada de voz, em que os rótulos nos botões informam aos usuários quais comandos de voz eles também podem dizer. por exemplo, ao examinar uma janela de aplicativo em HoloLens (1ª gen), um usuário pode dizer o comando "ajustar" para ajustar a posição do aplicativo no mundo.<br>
        <br>
        *Imagem: um usuário pode dizer o comando "ajustar", que vê na barra de aplicativos para ajustar a posição do aplicativo*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
        ![Ao examinar uma janela de aplicativo ou um holograma, um usuário pode dizer o comando "ajustar" que vê na barra de aplicativos para ajustar a posição do aplicativo no mundo](images/microphone-600px.png)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        Quando os aplicativos seguem essa regra, os usuários podem entender facilmente o que dizer para controlar o sistema. enquanto nuvens em um botão no HoloLens (1ª gen), você verá uma dica de ferramenta de "pesquisa de voz" que aparecerá após um segundo se o botão estiver habilitado para voz e exibirá o comando para falar para "pressionar". para revelar as dicas de ferramentas de voz no HoloLens 2, mostre o cursor de voz dizendo "select" ou "o que eu posso dizer" (consulte a imagem). <br>
        <br>
        *Imagem: "vê-lo, digamos", os comandos aparecem abaixo dos botões*
    :::column-end:::
        :::column:::
       ![Vê-lo, digamos que os comandos de ti apareçam abaixo dos botões](images/voice-seeitsayit-600px.png)<br><br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="voice-commands-for-fast-hologram-manipulation"></a>Comandos de voz para manipulação rápida de holograma

Há muitos comandos de voz que você pode dizer ao nuvensr em um holograma para realizar tarefas de manipulação rapidamente. Esses comandos de voz funcionam em janelas de aplicativos e em objetos 3D que você colocou no mundo.

**Comandos de manipulação de holograma**
* Entre em frente
* Maior | Aprimorou
* Menor

no HoloLens 2, você também pode criar interações mais naturais em combinação com olhar, que implicitamente fornece informações contextuais sobre o que você está referindo. Por exemplo, você pode examinar um holograma e dizer "colocar _isso_" e, em seguida, examinar onde deseja colocá-lo e dizer " _aqui_".
Ou você pode examinar uma parte Holographic em um computador complexo e dizer: "Dê-me mais informações sobre _isso_".

## <a name="discovering-voice-commands"></a>Descobrindo comandos de voz

Alguns comandos, como os comandos para manipulação rápida acima, podem ser ocultados. Para saber mais sobre os comandos que você pode usar, olhar em um objeto e, por exemplo, "o que eu posso dizer?". Uma lista de comandos possíveis é exibida. Você também pode usar o cursor olhar de cabeçalho para examinar e revelar as dicas de ferramenta de voz para cada botão na frente de você. 

Se você quiser uma lista completa, basta dizer "Mostrar todos os comandos" a qualquer momento. 

## <a name="dictation"></a>Ditado

Em vez de digitar com [toques de ar](gaze-and-commit.md#composite-gestures), o ditado de voz pode ser mais eficiente para inserir texto em um aplicativo. Isso pode acelerar muito a entrada com menos esforço para o usuário.

![O ditado de voz começa selecionando o botão de microfone](images/micbuttonfordictation.png)<br>
*O ditado de voz começa selecionando o botão de microfone no teclado*

Sempre que o teclado holográfico está ativo, você pode alternar para o modo de ditado em vez de digitar. Selecione o microfone no lado da caixa de entrada de texto para começar.

## <a name="adding-voice-commands-to-your-app"></a>Adicionando comandos de voz ao seu aplicativo

Considere a adição de comandos de voz em qualquer experiência que você criar. A voz é uma maneira poderosa de controlar o sistema e os aplicativos. Como os usuários falam com diferentes tipos de dialetos e acentos, a escolha adequada das palavras-chave de fala garantirá que os comandos dos usuários sejam interpretados de forma não ambígua.

### <a name="best-practices"></a>Práticas recomendadas

A seguir, algumas práticas que auxiliarão em um reconhecimento de fala perfeito.
* **Use comandos concisos** - quando possível, escolha palavras com duas ou mais sílabas. Palavras com uma sílaba tendem a empregar sons de vogais diferentes quando faladas por pessoas com sotaques diferentes. Exemplo: "Reproduzir vídeo" é melhor do que "Reproduzir o vídeo selecionado no momento"
* **Usar vocabulário simples –** exemplo: "Mostrar observação" é melhor do que "Mostrar placar"
* **Certifique-se de** que os comandos não sejam destrutivas – certifique-se de que as ações de comando de fala não sejam destrutivas e possam ser facilmente desfeitas no caso de outra pessoa falando perto do usuário disparar acidentalmente um comando.
* **Evitar comandos de som semelhantes** – evite registrar vários comandos de fala que soem semelhantes. Exemplo: "Mostrar mais" e "Mostrar loja" podem ter som semelhante.
*  Desarmá-lo quando ele não usar – quando seu aplicativo não estiver em um estado no qual um comando de fala específico é válido, considere o registro para que outros comandos não sejam confundidos com esse.
* **Teste com sotaques diferentes** - teste seu aplicativo com usuários que tenham sotaques diferentes.
* **Mantenha a consistência nos comandos de voz** - se "Voltar" vai para a página anterior, mantenha esse comportamento em seus aplicativos.
* **Evite usar comandos do sistema** – os seguintes comandos de voz são reservados para o sistema, portanto, evite usá-los em seus aplicativos:
   * "Ei, Cortana!"
   * "Selecionar"
   * "Ir para iniciar"

### <a name="advantages-of-voice-input"></a>Vantagens da entrada de voz

A entrada de voz é uma maneira natural de comunicarmos nossas intenções. A voz é especialmente boa em **transmissões de** interface porque pode ajudar os usuários a percorrer várias etapas de uma interface. Um usuário pode dizer "voltar" ao olhar para uma página da Web, em vez de ter que ir para cima e atingir o botão Voltar no aplicativo. Essa pequena economia de tempo tem um efeito **emocional poderoso** na percepção do usuário sobre a experiência e oferece uma pequena quantidade de aprendizado. O uso da voz também é um método de entrada conveniente quando nossos braços estão ocupados ou quando estamos **executando várias tarefas ao mesmo tempo**. Em dispositivos em que a digitação em um teclado é difícil, o ditado **de** voz pode ser uma maneira alternativa eficiente de inserir texto. Por fim, em alguns  casos em que o intervalo de precisão para o olhar e o gesto são limitados, a voz pode ajudar a desambiguar a intenção do usuário. 

**Como o uso da voz pode beneficiar o usuário?**
* Reduz o tempo - deve tornar o objetivo final mais eficiente.
* Minimiza o esforço - deve tornar as tarefas mais fluídas e simples.
* Reduz a carga cognitiva - é intuitivo e fácil de lembrar e aprender.
* É socialmente aceitável – ele deve se ajustar às normas sociais de comportamento.
* É rotineiro - a voz pode facilmente se tornar um comportamento habitual.

### <a name="challenges-for-voice-input"></a>Desafios para entrada de voz

Embora a entrada de voz seja ótima para muitos aplicativos diferentes, ela também enfrenta vários desafios. Entender as vantagens e os desafios da entrada de voz permite que os desenvolvedores de aplicativos façam escolhas mais inteligentes sobre como e quando usar a entrada de voz e criar uma ótima experiência para seus usuários.

**Entrada de voz para controle de entrada contínua** Controle fino é um deles. Por exemplo, um usuário pode querer alterar seu volume em seu aplicativo de música. Ela pode dizer "inintente", mas não está claro o quanto o sistema deve fazer o volume. O usuário poderia dizer: "Torná-lo um pouco mais complicado", mas "um pouco" é difícil de quantificar. Mover ou dimensionar hologramas com voz é muito difícil. 

**Confiabilidade da detecção de entrada de voz** Embora os sistemas de entrada de voz se tornem melhores e melhores, às vezes eles podem ouvir e interpretar incorretamente um comando de voz.
A chave é resolver o desafio em seu aplicativo. Forneça comentários aos usuários quando o sistema estiver escutando e o que o sistema entendeu esclarece possíveis problemas no entendimento da fala dos usuários.  

**Entrada de voz em espaços compartilhados** A voz pode não ser socialmente aceitável em espaços que você compartilha com outras pessoas.
Veja alguns exemplos:
* O usuário talvez não queira interromper outras pessoas (por exemplo, em uma biblioteca silenciosa ou em um escritório compartilhado)
* Os usuários podem se sentir mal ao serem vistos falando sozinhos em público,
* Um usuário pode se sentir constrangido ao ditar uma mensagem pessoal ou confidencial (incluindo senhas) enquanto outros estão escutando

**Entrada de voz de palavras exclusivas ou desconhecidas** As dificuldades para a entrada de voz também vêm quando os usuários estão ditando palavras que podem ser desconhecidas para o sistema, como apelidos, determinadas palavras gírias ou abreviações. 

**Learning de voz** Embora a meta final seja, naturalmente, conversar com seu sistema, muitas vezes os aplicativos ainda dependem de comandos de voz pré-definidos específicos.
Um desafio associado a um conjunto significativo de comandos de voz é como ensinar a eles sem sobrecarregar o usuário e como ajudar o usuário a mantê-los. 

<br>

---

### <a name="voice-feedback-states"></a>Estados de retorno de voz

Quando a voz é aplicada corretamente, o usuário sabe **o que pode dizer e obtém um retorno claro**, e o sistema **o ouve corretamente**. Esses dois sinais fazem o usuário se sentir seguro para usar a Voz como uma entrada primária. A seguir, um diagrama mostrando o que acontece com o cursor quando a entrada de voz é reconhecida e como ele comunica isso ao usuário.


:::row:::
    :::column:::
       ![1. Estado regular do cursor](images/voicefeedbackstates-regular.jpg)<br>
       **1. Estado regular do cursor**<br>
    :::column-end:::
    :::column:::
       ![2. Comunica comentários de voz e desaparece](images/voicefeedbackstates-voice.jpg)<br>
        **2. Comunica comentários de voz e desaparece**<br>
    :::column-end:::
    :::column:::
       ![*3. Estado regular do cursor](images/voicefeedbackstates-regular.jpg)<br>
       **3. Retorna ao estado regular do cursor**<br>
    :::column-end:::
:::row-end:::

<br>

---

<br>

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>As principais coisas que os usuários devem saber sobre "fala" na realidade misturada

* Diga **"Selecionar"** ao direcionar um botão (você pode usá-lo em qualquer lugar para selecionar um botão).
* Você pode dizer o **nome do rótulo de um botão da barra de aplicativos** em alguns aplicativos para realizar uma ação. Por exemplo, ao olhar para um aplicativo, um usuário pode dizer o comando "Remover" para remover o aplicativo do mundo (isso economiza tempo ao precisar selecioná-lo com sua mão).
* Você pode começar a Cortana escutando **"Olá, Cortana".** Você pode fazer perguntas ("Ei, Cortana! Qual é a altura da Torre Eiffel?"), pedir para ela abrir um aplicativo ("Ei, Cortana! Abra o Netflix") ou pedir para ela abrir o Menu Iniciar ("Ei, Cortana! Abra o menu Iniciar") e muito mais.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Perguntas e preocupações comuns dos usuários em relação à voz

* O que posso dizer?
* Como saberei que o sistema me ouviu corretamente?
   * O sistema não entende corretamente meus comandos de voz.
   * Ele não reage quando dou um comando de voz.
* Ele reage de maneira errada quando dou um comando de voz.
* Como direcionar minha voz a um aplicativo específico ou a um comando de aplicativo?
* Posso usar a voz para comandar as coisas no quadro holográfico do HoloLens?

## <a name="communication"></a>Comunicação

Para aplicativos que querem aproveitar as opções de processamento de entrada de áudio personalizadas fornecidas [](/windows/win32/api/audiosessiontypes/ne-audiosessiontypes-audio_stream_category) pelo HoloLens, é importante entender as várias categorias de fluxo de áudio que seu aplicativo pode consumir. Windows 10 dá suporte a várias categorias de fluxo diferentes e o HoloLens usa três delas para habilitar o processamento personalizado para otimizar a qualidade de áudio do microfone adaptada para fala, comunicação e outros, que podem ser usados para cenários de captura de áudio de ambiente ambiente (ou seja, "gravação").
* A AudioCategory_Communications de fluxo é personalizada para cenários de narração e qualidade de chamada e fornece ao cliente um fluxo de áudio mono de 24 bits de 16 kHz da voz do usuário
* A AudioCategory_Speech de fluxo é personalizada para o mecanismo de fala HoloLens (Windows) e fornece a ela um fluxo mono de 16 kHz de 24 bits da voz do usuário. Essa categoria pode ser usada por mecanismos de fala de terceiros, se necessário.
* A AudioCategory_Other de fluxo é personalizada para gravação de áudio de ambiente ambiente e fornece ao cliente um fluxo de áudio estéreo de 48 kHz de 24 bits.

Todo esse processamento de áudio é acelerado por hardware, o que significa que os recursos descarregam muito menos energia do que se o mesmo processamento fosse feito no HoloLens CPU. Evite executar outro processamento de entrada de áudio na CPU para maximizar a vida útil da bateria do sistema e aproveitar o processamento de entrada de áudio descarregado e integrado.

## <a name="languages"></a>Idiomas

HoloLens 2 dá [suporte a vários idiomas.](/hololens/hololens2-language-support) Tenha em mente que os comandos de fala sempre serão executados na linguagem de exibição do sistema, mesmo que vários teclados sejam instalados ou se os aplicativos tentarem criar um reconhecedor de fala em um idioma diferente.

## <a name="troubleshooting"></a>Solução de problemas

Se você estiver tendo problemas ao usar "select" e "Hey Cortana", tente mudar para um espaço mais silencioso, se desligando da origem do ruído ou falando mais alto. Neste momento, todo o reconhecimento de fala HoloLens é ajustado e otimizado especificamente para falantes nativos Estados Unidos inglês.

Para o Windows Mixed Reality Developer Edition versão 2017, a lógica de gerenciamento de ponto de extremidade de áudio funcionará bem (para sempre) depois de fazer logout e voltar para a área de trabalho do pc após a conexão inicial do HMD. Antes desse primeiro evento de saída/logon depois de passar pelo WMR OOBE, o usuário poderia experimentar vários problemas de funcionalidade de áudio que variam de nenhum áudio a nenhuma alternação de áudio, dependendo de como o sistema foi definido antes de conectar o HMD pela primeira vez.

<br>

---

## <a name="voice-input-in-mrtk-mixed-reality-toolkit-for-unity"></a>Entrada de voz no MRTK (Mixed Reality Toolkit) para Unity
Com **[o MRTK,](https://github.com/Microsoft/MixedRealityToolkit-Unity)** você pode atribuir facilmente o comando de voz em qualquer objeto. Use o Perfil de Entrada de Fala **do** MRTK para definir suas palavras-chave. Ao atribuir o script **SpeechInputHandler,** você pode fazer com que qualquer objeto responda às palavras-chave definidas no Perfil de Entrada de Fala. SpeechInputHandler também fornece o rótulo de confirmação de fala para melhorar a confiança do usuário.

* [MRTK – Comando de voz](/windows/mixed-reality/mrtk-unity/features/input/speech)

---

## <a name="see-also"></a>Confira também

* [Focar e confirmar](gaze-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz no DirectX](../develop/native/voice-input-in-directx.md)
* [Entrada de voz no Unity](../develop/unity/voice-input-in-unity.md)