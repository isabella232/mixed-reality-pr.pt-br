---
title: Perguntas frequentes sobre fala e áudio
description: fala e áudio Windows Mixed Reality solução de problemas que vão além da nossa documentação de suporte de consumidor padrão.
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, solução de problemas, erros, ajuda, suporte, problemas de áudio, problemas de fala
ms.openlocfilehash: d1d30cebb40d54d579e978013b9abc60981fa943d43b95a96f358092631b4d27
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115208976"
---
# <a name="speech-and-audio-faqs"></a>Perguntas frequentes sobre fala e áudio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Não consigo ouvir nenhum som em meu headset ou o som está passando pelo meu computador em vez do meu Headset

* Se o headset de imersão não incluir fones de ouvido internos, conecte os fones de ouvido à tomada de áudio no headset. A tomada muitas vezes está localizada logo atrás ou abaixo do visor ou das lentes do headset. Verifique com seu fabricante de headset se você não conseguir encontrá-lo.
* Alguns headsets de áudio têm botões físicos para controlar o volume. Se o áudio não estiver funcionando, verifique se o volume está desativado ou mudo.
* o áudio será alternado para o dispositivo de reprodução de Windows padrão: 
    * Se você tirar o fone de ouvido
    * Virar o visor para cima
    * Fechar o aplicativo portal da realidade misturada
    * Quando um aplicativo não tiver sido usado por 15 minutos. 
    * você pode alterar essa configuração em **Configurações > realidade mista > áudio e fala.**
* Verifique se o headset de áudio está conectado à tomada de áudio. O headset do Acer em particular pode exigir mais cuidado para garantir que o headset de áudio esteja conectado.
* Verifique se o headset/microfone de áudio está conectado ao headset e não ao PC.
* o painel de controle de som no **Configurações > sistema > som** mostra apenas os pontos de extremidade de áudio habilitados, não os pontos de extremidade desabilitados. O dispositivo de áudio do headset será desabilitado quando você não estiver desgastando o headset. Para vê-lo, clique com o botão direito do mouse no painel de controle de som e escolha "mostrar dispositivos desabilitados". O nome do dispositivo é "áudio Realtek USB 2.0", que pode ser renomeado na página "Propriedades". Você pode fazer isso para as guias de reprodução e gravação.
* Se o seu áudio não estiver funcionando em aplicativos de realidade misturada, por exemplo, com o aplicativo Netflix. isso pode ser causado por um problema conhecido em que o Windows Mixed Reality não é atualizado automaticamente para corresponder à versão do sistema operacional. para corrigir esse problema e obter a melhor experiência de realidade misturada, vá para **Configurações > Update & Security > Windows Update > verificar se há atualizações**.

> [!NOTE]
> * Windows Mixed Reality áudio espacial funciona melhor com fones de ouvido internos ou conectados diretamente ao headset de imersão. Alto-falantes de PC ou fones de ouvido conectados ao PC podem não funcionar bem para áudio espacial.
> * Windows Mixed Reality não dá suporte a fones de ouvido Bluetooth áudio.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Estou enfrentando alterações de volume repentinas, perda de áudio ou repercussão

* Alguns aplicativos, como aqueles iniciados por meio de SteamVR, podem perder áudio ou parar quando o dispositivo de áudio muda à medida que você inicia ou interrompe o portal de realidade misturada. Para corrigir isso, reabra o portal de realidade misturada e reinicie o aplicativo.
* se outro dispositivo usb de multimídia (como uma web cam) compartilhar o mesmo hub usb interno ou externo com o Windows Mixed Reality headset, a tomada de áudio do headset ou os fones de ouvido poderá, ocasionalmente, ter um som de barulho ou nenhum áudio. Conecte seu headset em uma porta USB que usa um Hub diferente ou desconecte/Desabilite seu outro dispositivo de multimídia USB.
* se você notar um excesso de ruídos dos fones de ouvido conectados, o hub USB do PC poderá não conseguir fornecer energia suficiente para o Windows Mixed Reality headset. Se isso ocorrer, envie um bug do [Hub de comentários](/hololens/hololens-feedback) e tente:
    * removendo cabos de extensão
    * usando um HUB USB 3,0 dedicado e com alimentação externa
    * uma porta USB diferente no PC

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>meu fone de ouvido Bluetooth áudio não está funcionando conforme o esperado

a Microsoft não recomenda o uso de Bluetooth headsets de áudio com Windows Mixed Reality. Bluetooth periféricos de áudio não funcionam bem com Windows Mixed Reality experiências de voz e som espacial. Bluetooth headsets de áudio não dão suporte à entrada de microfone e à saída de estéreo ao mesmo tempo, portanto, você não ouvirá o som estéreo ou espacial ao usá-lo para gamechat ou outra entrada de voz. Bluetooth headsets de áudio também podem afetar negativamente sua experiência com o controlador de movimento.

## <a name="sound-isnt-coming-from-expected-directions"></a>O som não está vindo das direções esperadas

a página inicial do Windows Mixed Reality inclui som espacial (áudio que parece ser proveniente dos aplicativos localizados em sua casa). À medida que você muda e avança mais ou longe de cada aplicativo, a direção e o nível do som mudarão para aumentar o sentido de realm. Abaixo estão alguns motivos possíveis para instruções de som inesperadas:

* se você abrir e reproduzir música de um aplicativo de música com capacidade de fundo (como Groove Música) em sua casa e, em seguida, abrir uma experiência de VR de imersão como um jogo, o som do aplicativo de música fading cruzado do som espacial para o estéreo. Pode parecer mais alto porque não há mais nenhuma distância entre você e o som.
* se você tiver Cortana habilitado em seu computador antes de usar o fone de ouvido Windows Mixed Reality, você poderá perder o som espacial aplicado aos aplicativos em sua página inicial do Windows Mixed Reality. para corrigir isso, desative "permitir que Cortana responda ao ei Cortana" em **Configurações > Cortana** na área de trabalho antes de iniciar Windows Mixed Reality ou habilitar "Windows Sonic para Fones de Ouvido":
    1. vá para a janela do aplicativo da área de trabalho em Windows Mixed Reality página inicial.
    2. Clique com o botão esquerdo do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione-o na lista de dispositivos de áudio.
    3. clique com o botão direito do mouse no ícone de alto-falante na barra de tarefas da área de trabalho e selecione "Windows Sonic para Fones de Ouvido" no menu "configuração do orador".
    4. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).

## <a name="speech-commands-are-not-working-as-expected"></a>Os comandos de fala não estão funcionando conforme o esperado

* Para usar comandos de fala, as configurações de fala e idioma em seu computador devem ser definidas como um [idioma com suporte no Windows Mixed Reality](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages). para verificar suas Windows configurações de fala e idioma, selecione **Configurações tempo > & idioma > região & idioma** e **Configurações > tempo & linguagem > fala**.
* Se o headset não tiver um microfone interno, você precisará anexar fones de ouvido com um microfone ao headset ou ao seu PC. para que a entrada de microfone seja alternada automaticamente para o headset quando você o tiver ativado, vá para **Configurações > realidade mista > áudio e fala** e ative "quando eu usar meu headset, mude para microfone headset".
* Alguns headsets de áudio têm um botão físico para ativar mudo e mudo do microfone. Se os comandos de fala não estiverem funcionando, verifique se o microfone está mudo.
* Os headsets de áudio com um microfone que Dangles do cabo earbud não fazem bem para comandos de voz em ambientes com ruídos de ambiente.
* Cortana pode ser lenta na primeira vez em que ela é invocada em uma sessão do Portal da realidade misturada. vá para **Configurações > Cortana > fale com Cortana** e certifique-se de que "permitir que Cortana responda ao ei Cortana" esteja habilitado.
* Em alguns PCs, o lucro de captura de voz padrão para o microfone conectado ao headset pode estar definido como muito baixo. Se você tiver comandos de fala não confiáveis ou ditado, execute a solução de problemas de configuração do microfone:
    1. vá para o aplicativo de Desktop na Windows Mixed Reality página inicial enquanto usa o headset (para afetar o microfone usado para Windows Mixed Reality).
    2. vá para **Configurações > hora & idioma > fala**.
    3. selecione "Introdução" na seção "microfone".
    4. Selecione o ponto de extremidade apropriado no assistente de solução de problemas.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Tenho apenas um headset de áudio e quero usá-lo para área de trabalho e meu Headset

Se você tiver apenas um headset de áudio e não tiver um headset com fones de ouvido internos, conecte o headset de áudio ao PC em vez do headset. Em seguida, desligue "alternar para áudio do headset" nas configurações do portal de realidade misturada.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Quero mudar para Dolby Atmos for Headphones

Windows Mixed Reality ambientes e seus aplicativos usam Windows Sonic para Fones de Ouvido tecnologia de áudio espacial, que é personalizada para experiências de realidade misturada. outras tecnologias espaciais de áudio, como Dolby Atmos for Headphones, podem ser aplicadas a aplicativos de tela inteira, como jogos SteamVR, mas não para os ambientes de Windows Mixed Reality shell e aplicativos (como colocar um navegador da web na parede da casa Cliff ou o céu Loft) que foram projetados usando Windows Sonic para Fones de Ouvido som espacial e acústicos.