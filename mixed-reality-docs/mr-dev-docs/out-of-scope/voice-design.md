---
title: Comando de voz
description: Foco, gestos e voz (GGV) são o principal meio de interação do HoloLens. Este artigo fornece orientação sobre design de voz.
author: shengkait
ms.author: shentan
ms.date: 04/21/2019
ms.topic: article
keywords: Windows Mixed Reality, design, interação, voz
ms.openlocfilehash: 2a988ad50a8b20a256b0d7208187785778447cc08109fbf55d4ae83e820a76ba
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115225354"
---
# <a name="voice-commanding"></a>Comando de voz

Ao usar comandos de voz, o olhar normalmente é usado como o mecanismo de direcionamento, seja como um ponteiro ("selecionar") ou para direcionar o comando para um aplicativo ("veja-o, diga-o"). Obviamente, alguns comandos de voz não exigem um alvo, como "Ir para o início" ou "Ei, Cortana".


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
        <td><a href="https://docs.microsoft.com/hololens/hololens2-hardware"><strong>HoloLens 2</strong></td>
        <td><a href="../discover/immersive-headset-hardware-details.md"><strong>Headsets imersivos</strong></a></td>
    </tr>
     <tr>
        <td>Comando de voz</td>
        <td>✔️</td>
        <td>✔️</td>
        <td>✔️ (com o headset anexado)</td>
    </tr>
</table>



## <a name="how-to-use-voice"></a>Como usar a voz

Considere a adição de comandos de voz em qualquer experiência que você criar. A voz é uma maneira eficiente e conveniente de controlar o sistema e os aplicativos. Como os usuários falam com uma variedade de dialetos e sotaques, a escolha adequada das palavras garantirá que os comandos sejam interpretados de maneira inequívoca.

### <a name="best-practices"></a>Práticas recomendadas

A seguir, algumas práticas que auxiliarão em um reconhecimento de fala perfeito.
* **Use comandos concisos** - quando possível, escolha palavras com duas ou mais sílabas. Palavras com uma sílaba tendem a empregar sons de vogais diferentes quando faladas por pessoas com sotaques diferentes. Exemplo: "Reproduzir vídeo" é melhor do que "Reproduzir o vídeo selecionado no momento"
* **Usar vocabulário simples –** exemplo: "Mostrar observação" é melhor do que "Mostrar placar"
* **Certifique-se de que os comandos não sejam destrutivos** - certifique-se de que as ações que podem ser executadas por um comando de voz não sejam destrutivas e possam ser facilmente desfeitas caso outra pessoa falando nas proximidades do usuário acidentalmente acione um comando.
* **Evite comandos com sons semelhantes** - evite registrar vários comandos de fala muito semelhantes. Exemplo: "Mostrar mais" e "Mostrar loja" podem ser som muito semelhantes.
* **Cancele o registro do aplicativo quando não estiver em uso** - quando seu aplicativo não estiver em um estado em que um determinado comando de fala seja válido, considere cancelar seu registro para evitar a confusão com outros comandos.
* **Teste com sotaques diferentes** - teste seu aplicativo com usuários que tenham sotaques diferentes.
* **Mantenha a consistência nos comandos de voz** - se "Voltar" vai para a página anterior, mantenha esse comportamento em seus aplicativos.
* **Evite usar comandos do sistema** - os comandos de voz a seguir são reservados para o sistema. Eles não devem ser usados pelos aplicativos.
   * "Ei, Cortana!"
   * "Selecionar"

### <a name="select"></a>"Selecionar"

Dizer "selecionar" a qualquer momento ativará tudo o que o cursor estiver apontando. 

>Observação: HoloLens 2, o cursor de olhar precisa primeiro ser invocado dizendo a palavra "select". Diga "selecionar" novamente para ativar. Para ocultar o cursor de olhar, basta usar as mãos para fazer airtap ou tocar em um objeto. 

### <a name="see-it-say-it"></a>Veja e diga

O Windows Mixed Reality utiliza um modelo de voz "veja e diga", no qual os **rótulos dos botões são idênticos aos comandos de voz associados**. Como não há dissonância entre o rótulo e o comando de voz, os usuários tem melhor noção do que dizer para controlar o sistema. Para reforçar isso, ao olhar fixo para um botão, uma **"dica de espera de voz"** é exibida para comunicar quais botões estão habilitados para voz.


![Exemplo 1 - veja e diga](../design/images/voice-seeitsayit1-640px.jpg)

![Exemplo 2 - veja e diga](../design/images/voice-seeitsayit2-640px.jpg)<br>
*Exemplos de "veja e diga"*

### <a name="voices-strengths"></a>Vantagens da voz

A entrada de voz é uma maneira natural de comunicarmos nossas intenções. A voz é especialmente boa em transmissões de **interface** porque pode ajudar os usuários a percorrer várias etapas de uma interface (um usuário pode dizer "voltar" ao olhar para uma página da Web, em vez de precisar ir para cima e clicar no botão Voltar no aplicativo). Essa pequena economia de tempo tem um efeito **emocional** poderoso na percepção da experiência de um usuário e oferece uma pequena quantidade de coisas. O uso da voz também é um método de entrada conveniente quando nossos braços estão ocupados ou quando estamos **executando várias tarefas ao mesmo tempo**. Em dispositivos em que a digitação em um teclado é difícil, o **ditado de** voz pode ser uma maneira eficiente e alternativa de entrada. Por fim, em alguns  casos, quando o intervalo de precisão para o olhar e o gesto são limitados, a voz pode ser o único método confiável de entrada de um usuário.

**Como o uso da voz pode beneficiar o usuário?**
* Reduz o tempo - deve tornar o objetivo final mais eficiente.
* Minimiza o esforço - deve tornar as tarefas mais fluídas e simples.
* Reduz a carga cognitiva - é intuitivo e fácil de lembrar e aprender.
* É socialmente aceitável - deve estar de acordo com as normas sociais em termos de comportamento.
* É rotineiro - a voz pode facilmente se tornar um comportamento habitual.

### <a name="voices-weaknesses"></a>Desvantagens da voz

A voz também tem algumas desvantagens. O controle refinado é uma delas. (por exemplo, um usuário pode dizer "mal-estar", mas não pode dizer quanto. "Um pouco" é difícil de quantificar. Também é difícil mover ou dimensionar objetos usando a voz (ela não oferece granularidade de controle). A voz também pode ser imperfeita. Às vezes, um sistema de voz ouve incorretamente ou não consegue ouvir um comando. Contornar esses erros é um desafio em qualquer interface. Por fim, a voz pode não ser socialmente aceitável em locais públicos. Há algumas coisas que os usuários não podem ou não devem dizer. Essas limitações permitem usar a fala para sua melhor função.

### <a name="voice-feedback-states"></a>Estados de retorno de voz

Quando a voz é aplicada corretamente, o usuário sabe **o que pode dizer e obtém um retorno claro**, e o sistema **o ouve corretamente**. Esses dois sinais fazem o usuário se sentir seguro para usar a Voz como uma entrada primária. A seguir, um diagrama mostrando o que acontece com o cursor quando a entrada de voz é reconhecida e como ele comunica isso ao usuário.

![Estados de retorno de voz para cursor](../design/images/voicefeedbackstates.png)<br>
*Estados de retorno de voz para cursor*

## <a name="top-things-users-should-know-about-speech-in-mixed-reality"></a>As principais coisas que os usuários devem saber sobre "fala" na realidade misturada
* Diga **"Selecionar"** ao focalizar um botão (você pode usar esse comando em qualquer lugar para clicar em um botão).
* Você pode dizer o **nome do rótulo de um botão da barra de aplicativos** em alguns aplicativos para realizar uma ação. Por exemplo, olhando para um aplicativo, um usuário pode dizer o comando "Remover" para remover o aplicativo do mundo (isso economiza tempo, pois você não precisa clicar nele com a mão).
* Você pode iniciar a escuta da Cortana dizendo **"Ei, Cortana".** Você pode fazer perguntas ("Hey Cortana, quão alta é a torre Eia?"), pedir para ela abrir um aplicativo ("Hey Cortana, open Netflix") ou pedir que ela abra o Menu Iniciar ("Hey Cortana, leve-me para casa") e muito mais.

## <a name="common-questions-and-concerns-users-have-about-voice"></a>Perguntas e preocupações comuns dos usuários em relação à voz
* O que posso dizer?
* Como saberei que o sistema me ouviu corretamente?
   * O sistema não entende corretamente meus comandos de voz.
   * Ele não reage quando dou um comando de voz.
* Ele reage de maneira errada quando dou um comando de voz.
* Como direcionar minha voz a um aplicativo específico ou a um comando de aplicativo?
* Posso usar a voz para comandar as coisas no quadro holográfico do HoloLens?

## <a name="see-also"></a>Confira também
* [Gestos](../design/gaze-and-commit.md#composite-gestures)
* [Focar com a cabeça e esperar](../design/gaze-and-dwell.md)