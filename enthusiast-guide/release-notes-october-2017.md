---
title: Notas sobre a versão – outubro de 2017
description: mantenha-se atualizado sobre as notas de versão Windows Mixed Reality para o Windows 10 Fall Creators Update (outubro de 2017).
author: mattzmsft
ms.author: mazeller
ms.date: 03/21/2018
ms.topic: article
keywords: notas de versão, versão, Windows 10, Build, RS3, so
ms.openlocfilehash: 09a33e1bc4a13c75e4c8a0ee250c7b67eb8e68e21220840037085e727acfb1f3
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115190590"
---
# <a name="release-notes---october-2017"></a>Notas sobre a versão – outubro de 2017

Bem-vindo ao Windows Mixed Reality! a versão **[Windows 10 Fall Creators Update](https://blogs.windows.com/windowsexperience/2017/10/17/whats-new-windows-10-fall-creators-update/)** apresenta suporte para novos [headsets de imersão de Windows Mixed Reality](/windows/mixed-reality/discover/immersive-headset-hardware-details) e controladores de [movimento](/windows/mixed-reality/design/motion-controllers). agora você pode explorar novos mundos, participar de jogos de VR e experimentar a diversão de imersão quando estiver conectado a um [PC com capacidade de Windows Mixed Reality](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).

a versão do Windows Mixed Reality headsets e controladores de movimento é a culminação de um grande esforço da equipe e um avanço importante para a [plataforma Windows Mixed Reality](/windows/mixed-reality/discover/mixed-reality), incluindo [Microsoft HoloLens](/windows/mixed-reality/hololens-hardware-details). embora HoloLens não esteja recebendo uma atualização com o Windows 10 Fall Creators Update, o trabalho em HoloLens não foi interrompido. teremos muitos aprendizados e ideias para se aplicarem de nosso trabalho recente em Windows Mixed Reality como um todo. na verdade, Windows Mixed Reality os headsets e os controladores de animação de imersão representam um excelente ponto de entrada para o desenvolvimento para HoloLens também, já que as mesmas APIs, ferramentas e conceitos se aplicam a ambos.

para atualizar para a versão mais recente de cada dispositivo, abra o aplicativo **Configurações** , vá para **atualização & segurança** e, em seguida, selecione o botão **verificar atualizações** . em um Windows 10 PC, você também pode instalar manualmente o Windows 10 Fall Creators Update usando a [ferramenta de criação de mídia do Windows](https://www.microsoft.com/software-download/windows10).

 **versão mais recente do desktop:** Windows 10 área de trabalho de outubro de 2017 (**10.0.16299.15**, Windows 10 Fall Creators Update)<br>
 **versão mais recente para o HoloLens:** [Windows 10 Holographic agosto de 2016](release-notes-august-2016.md) (**10.0.14393.0**, atualização de aniversário de Windows 10)

>[!VIDEO https://www.youtube.com/embed/YBcLy1lkegg]

## <a name="introducing-windows-mixed-reality"></a>Introdução ao Windows Mixed Reality

o Windows 10 Fall Creators Update oficialmente apresenta suporte para Windows Mixed Reality fones de ouvido e controladores de movimento, além de fazer Windows 10 o primeiro sistema operacional espacial do mundo. Aqui estão os destaques:
* **[variedade de headsets](https://blogs.windows.com/windowsexperience/2017/10/03/how-to-pre-order-your-windows-mixed-reality-headset/)** -Windows Mixed Reality está permitindo que os parceiros ofereçam tipos de headset diferentes a partir de $399 USD agrupados com controladores de movimento.
* **[controladores de movimento](/windows/mixed-reality/design/motion-controllers)** -Windows Mixed Reality os controladores de movimento sem fio com seu PC por meio de Bluetooth e recurso seis controle de graus de liberdade, muitos métodos de entrada e IMUs.
* **[Configuração e portabilidade fáceis](./recommended-adapters-for-windows-mixed-reality-capable-pcs.md)** – configure e comece em menos de 10 minutos. Headsets de imersão usam rastreamento interno para acompanhar seu movimento e seus controladores de movimento, com seis graus de liberdade. Não são necessárias câmeras externas ou marcadores de Lighthouse!
* **[o suporte para uma variedade maior de PCs](./windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)** -Windows Mixed Reality permitirá que mais pessoas experimentem o trabalho de hoje, com suporte para selecionar placas gráficas integradas e PCs começando em us $ $499.
* **[Windows Mixed Reality home](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home)** – o primeiro sistema operacional espacial do mundo fornece um ambiente doméstico familiar para várias tarefas com aplicativos 2d, inicialização de jogos e aplicativos de VR e colocação de hologramas decorativos.
* os **[jogos e aplicativos de VR incrível na Microsoft Store](https://www.microsoft.com/store/collections/MR-All-ImmersiveContent/)** -da diversão de imersão como o vídeo Hulu vr e 360 para jogos epic como SUPERHOT VR e o Arizona sol, a Microsoft Store tem uma variedade de conteúdo a ser experimentada no Windows Mixed Reality.
* **[SteamVR acesso antecipado](./using-steamvr-with-windows-mixed-reality.md)** – o Windows 10 Fall Creators Update permite que os títulos de SteamVR sejam reproduzidos com Windows Mixed Reality headsets e controladores, tornando o maior catálogo de títulos VR disponíveis para Windows Mixed Reality usuários.

## <a name="known-issues"></a>Problemas conhecidos

trabalhamos duro para fornecer uma ótima experiência de Windows Mixed Reality, mas ainda estamos acompanhando alguns problemas conhecidos. Se você encontrar outras pessoas, [envie-nos seus comentários](/windows/mixed-reality/give-us-feedback).

### <a name="desktop-app-in-the-windows-mixed-reality-home"></a>aplicativo de Desktop na página inicial do Windows Mixed Reality
* A ferramenta de recorte não funciona no aplicativo de desktop.
* O aplicativo de área de trabalho não mantém a configuração na reinicialização.
* se você estiver usando a visualização do Portal de realidade misturada na sua área de trabalho, ao abrir o aplicativo de desktop no Windows Mixed Reality página inicial, você poderá observar o efeito de espelho infinito. 
* a execução do aplicativo de Desktop pode causar problemas de desempenho em computadores sem Ultra Windows Mixed Reality; Não é recomendável.  
* O aplicativo de desktop pode ser iniciado automaticamente porque uma janela invisível no desktop tem foco. 
* O prompt de controle de conta de usuário da área de trabalho fará com que o headset apareça em preto até que o prompt seja concluído

### <a name="windows-mixed-reality-setup"></a>Windows Mixed Reality configuração
* ao configurar Windows com um headset conectado, o monitor do PC pode ficar em branco. desconecte seu headset para habilitar a saída para o monitor de PC para concluir Windows configuração.
* Ao criar um limite, o rastreamento pode falhar. Nesse caso, tente novamente, pois o sistema aprenderá mais sobre o seu espaço ao longo do tempo.
* se você ativar ou desativar Cortana durante a instalação do Windows Mixed Reality, essa alteração será aplicada às configurações de Cortana da área de trabalho.
* se você não tiver fones de ouvido conectados, poderá perder dicas ao visitar pela primeira vez o Windows Mixed Reality página inicial.
* Bluetooth fones de ouvido podem causar interferências com os controladores de movimento. é recomendável desemparelhar ou desligar Bluetooth controladores durante Windows Mixed Reality sessões.

### <a name="games-and-apps-from-windows-store"></a>jogos e aplicativos da Windows Store
* Alguns jogos graficamente intensivos, como Forza Motorsports 6, podem causar problemas de desempenho em PCs com menos capacidade quando reproduzidos dentro de Windows Mixed Reality.

### <a name="audio"></a>Áudio
* conforme observado acima, Bluetooth periféricos de áudio não funcionam bem com Windows Mixed Reality experiências de voz e som espacial. Eles também podem afetar negativamente a experiência do controlador de movimento. não recomendamos o uso de Bluetooth headsets de áudio com Windows Mixed Reality.
* Você não pode usar o dispositivo de áudio conectado ao (ou parte do) fone de ouvido para reprodução de áudio quando o dispositivo não está sendo gasto. Se você tiver apenas um headset de áudio, talvez queira conectar o headset de áudio ao PC host em vez do headset. nesse caso, você deve desativar "alternar para áudio de headset" em **Configurações**  >  **realidade misturada**  >  **áudio e fala**.
* Alguns aplicativos, incluindo muitos daqueles iniciados por meio de SteamVR, podem perder áudio ou parar quando o dispositivo de áudio muda conforme você inicia ou interrompe o portal de realidade misturada. Reinicie o aplicativo depois de abrir o aplicativo do portal de realidade misturada para corrigir isso.
* se o Cortana estiver habilitado no computador host antes de usar o headset de Windows Mixed Reality, você poderá perder a simulação de som espacial aplicada aos aplicativos que você coloca em casa Windows Mixed Reality página inicial. a solução alternativa é habilitar o "Windows Sonic para Fones de Ouvido" em todos os dispositivos de áudio conectados ao seu PC, até mesmo no dispositivo de áudio conectado ao headset:
   1. Clique com o botão esquerdo do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione na lista de dispositivos de áudio.
   2. clique com o botão direito do mouse no ícone de alto-falante na barra de tarefas da área de trabalho e selecione "Windows Sonic para Fones de Ouvido" no menu "configuração do orador".
   3. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).
>[!NOTE]
> - como os fones de ouvido/alto-falantes conectados ao seu headset não aparecerão a menos que você o esteja usando, você precisa fazer isso na janela do aplicativo de Desktop na Windows Mixed Reality página inicial para aplicar essa configuração ao dispositivo de áudio conectado ao headset (ou integrado ao headset).
> - outra opção é desativar "Let Cortana responder a ei Cortana" em **Configurações**  >  **Cortana** na área de trabalho antes de iniciar o Windows Mixed Reality.

* quando outro dispositivo usb de multimídia (como uma web cam) compartilha o mesmo hub usb (externo ou dentro de seu PC) com o Windows Mixed Reality headset, em casos raros, a tomada de áudio/fone de ouvido do headset pode ter um som de zumbi ou nenhum áudio. Você pode corrigir isso pelo Headset em uma porta USB que não compartilha o mesmo Hub que o outro dispositivo, ou desconectar/desabilitar o outro dispositivo de multimídia USB.
* em casos raros, o hub USB do PC host não pode fornecer energia suficiente para o Windows Mixed Reality headset e você pode notar uma intermitência de ruído dos fones de ouvido conectados ao headset.

### <a name="speech"></a>Fala
* Cortana pode falhar ao reproduzir suas indicações de áudio para ouvir/pensar e respostas de áudio para comandos.
* Cortana na China e nos mercados do japão não mostram corretamente o texto abaixo do círculo Cortana durante o uso.
* Cortana pode ser lenta na primeira vez em que ela é invocada em uma sessão do Portal da realidade misturada. você pode contornar isso garantindo que "Let Cortana responder a ei Cortana" em **Configurações**  >  **Cortana**  >  **fale com Cortana** está habilitado.
* Cortana pode ser executado mais lentamente em computadores que não são Windows Mixed Reality Ultra PCs.
* quando o teclado do sistema é definido como um idioma diferente do idioma da interface do usuário no Windows Mixed Reality, usar o ditado do teclado no Windows Mixed Reality resultará em uma caixa de diálogo de erro sobre o ditado não estar funcionando por não ter Wi-Fi conexão. para corrigir o problema, verifique se o idioma do teclado do sistema corresponde ao idioma da interface do usuário do Windows Mixed Reality.
* A Espanha não está sendo reconhecida corretamente como um mercado em que a fala está habilitada para Windows Mixed Reality.

### <a name="holograms"></a>Hologramas
* se você tiver colocado um grande número de hologramas em sua Windows Mixed Reality página inicial, alguns poderão desaparecer e reaparecerem à medida que você examinar. para evitar isso, remova alguns dos hologramas nessa área da Windows Mixed Reality página inicial.

### <a name="motion-controllers"></a>Controladores de movimento
* Ocasionalmente, se você selecionar uma página da Web no Edge, o conteúdo será ampliado em vez de clicar.
* Às vezes, quando você seleciona um link no Edge, a seleção não funciona.

## <a name="prior-release-notes"></a>Notas de versão anteriores
* [Notas sobre a versão – agosto de 2016](release-notes-august-2016.md)
* [Notas sobre a versão – maio de 2016](release-notes-may-2016.md)
* [Notas sobre a versão – março de 2016](release-notes-march-2016.md)

## <a name="see-also"></a>Confira também
* [Suporte a headsets de imersão (link externo)](./troubleshooting-windows-mixed-reality.md)
* [Problemas conhecidos do HoloLens](/windows/mixed-reality/hololens-known-issues)
* [Instalar as ferramentas](/windows/mixed-reality/develop/install-the-tools)
* [Fornecer comentários](/windows/mixed-reality/give-us-feedback)