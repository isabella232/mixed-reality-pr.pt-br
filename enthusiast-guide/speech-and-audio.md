---
title: Perguntas frequentes sobre fala e áudio
description: Solução de problemas da realidade mista do Windows com voz e áudio que vai além da nossa documentação de suporte padrão do consumidor.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, solução de problemas, erros, ajuda, suporte, problemas de áudio, problemas de fala
ms.openlocfilehash: fff5d661dbe61d4c9364c83e3bd0c6ddb8ab5cc6
ms.sourcegitcommit: d3a3b4f13b3728cfdd4d43035c806c0791d3f2fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/20/2021
ms.locfileid: "98581413"
---
# <a name="speech-and-audio-faqs"></a>Perguntas frequentes sobre fala e áudio

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Não consigo ouvir nenhum som em meu headset ou o som está passando pelo meu computador em vez do meu Headset

* Se o headset de imersão não incluir fones de ouvido internos, conecte os fones de ouvido à tomada de áudio no headset. A tomada muitas vezes está localizada logo atrás ou abaixo do visor ou das lentes do headset. Verifique com seu fabricante de headset se você não conseguir encontrá-lo.
* Alguns headsets de áudio têm botões físicos para controlar o volume. Se o áudio não estiver funcionando, verifique se o volume está desativado ou mudo.
* O áudio será alternado para o dispositivo de reprodução padrão do Windows: 
    * Se você tirar o fone de ouvido
    * Virar o visor para cima
    * Fechar o aplicativo portal da realidade misturada
    * Quando um aplicativo não tiver sido usado por 15 minutos. 
    * Você pode alterar essa configuração em **configurações > realidade misturada > áudio e fala.**
* Verifique se o headset de áudio está conectado à tomada de áudio. O headset do Acer em particular pode exigir mais cuidado para garantir que o headset de áudio esteja conectado.
* Verifique se o headset/microfone de áudio está conectado ao headset e não ao PC.
* O painel de controle de som em **configurações > sistema > som** mostra apenas os pontos de extremidade de áudio habilitados, não os pontos de extremidade desabilitados. O dispositivo de áudio do headset será desabilitado quando você não estiver desgastando o headset. Para vê-lo, clique com o botão direito do mouse no painel de controle de som e escolha "mostrar dispositivos desabilitados". O nome do dispositivo é "áudio Realtek USB 2.0", que pode ser renomeado na página "Propriedades". Você pode fazer isso para as guias de reprodução e gravação.
* Se o seu áudio não estiver funcionando em aplicativos de realidade misturada, por exemplo, com o aplicativo Netflix. Isso pode ser causado por um problema conhecido em que a realidade mista do Windows não é atualizada automaticamente para corresponder à versão do sistema operacional. Para corrigir esse problema e obter a melhor experiência de realidade misturada, acesse **configurações > atualização & segurança > Windows Update > verificar se há atualizações**.

> [!NOTE]
> * O áudio espacial da realidade mista do Windows funciona melhor com fones de ouvido incorporados ou conectados diretamente ao headset de imersão. Alto-falantes de PC ou fones de ouvido conectados ao PC podem não funcionar bem para áudio espacial.
> * A realidade mista do Windows não dá suporte a headsets de áudio Bluetooth.

## <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Estou enfrentando alterações de volume repentinas, perda de áudio ou repercussão

* Alguns aplicativos, como aqueles iniciados por meio de SteamVR, podem perder áudio ou parar quando o dispositivo de áudio muda à medida que você inicia ou interrompe o portal de realidade misturada. Para corrigir isso, reabra o portal de realidade misturada e reinicie o aplicativo.
* Se outro dispositivo USB de multimídia (como uma Web Cam) compartilhar o mesmo hub USB interno ou externo com o headset de realidade misturada do Windows, a tomada de áudio do headset ou os fones de ouvido poderão, ocasionalmente, ter um som de zumbi ou nenhum áudio. Conecte seu headset em uma porta USB que usa um Hub diferente ou desconecte/Desabilite seu outro dispositivo de multimídia USB.
* Se você notar um excesso de ruídos dos fones de ouvido conectados, o hub USB do PC poderá não conseguir fornecer energia suficiente ao headset da realidade mista do Windows. Se isso ocorrer, envie um bug do [Hub de comentários](/hololens/hololens-feedback) e tente:
    * removendo cabos de extensão
    * usando um HUB USB 3,0 dedicado e com alimentação externa
    * uma porta USB diferente no PC

## <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Meu headset de áudio Bluetooth não está funcionando conforme o esperado

A Microsoft não recomenda o uso de headsets de áudio Bluetooth com a realidade mista do Windows. Os periféricos de áudio Bluetooth não funcionam bem com experiências de voz e de som espacial do Windows Mixed Reality. Fones de ouvido de áudio Bluetooth não dão suporte à entrada de microfone e à saída de estéreo ao mesmo tempo, portanto, você não ouvirá o som estéreo ou espacial ao usá-lo para gamechat ou outra entrada de voz. Fones de ouvido de áudio Bluetooth também podem afetar negativamente sua experiência com o controlador de movimento.

## <a name="sound-isnt-coming-from-expected-directions"></a>O som não está vindo das direções esperadas

O Windows Mixed Reality Home inclui som espacial (áudio que parece ser proveniente dos aplicativos localizados em sua casa). À medida que você muda e avança mais ou longe de cada aplicativo, a direção e o nível do som mudarão para aumentar o sentido de realm. Abaixo estão alguns motivos possíveis para instruções de som inesperadas:

* Se você abrir e reproduzir música de um aplicativo de música com capacidade de fundo (como o Groove Music) em sua casa e, em seguida, abrir uma experiência de VR de imersão como um jogo, o som do aplicativo de música fading cruzado do som espacial para o estéreo. Pode parecer mais alto porque não há mais nenhuma distância entre você e o som.
* Se você tivesse o Cortana habilitado em seu computador antes de usar o headset de realidade misturada do Windows, poderá perder o som espacial aplicado aos aplicativos em sua página inicial do Windows Mixed Reality. Para corrigir isso, desative "permitir que a Cortana responda à Ei Cortana" em **configurações > Cortana** na sua área de trabalho antes de iniciar a realidade mista do Windows ou habilitar "Windows Sonic para fones de ouvido":
    1. Vá para a janela do aplicativo da área de trabalho na página inicial do Windows Mixed Reality.
    2. Clique com o botão esquerdo do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione-o na lista de dispositivos de áudio.
    3. Clique com o botão direito do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione "Windows Sonic para fones de ouvido" no menu "configuração do orador".
    4. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).

## <a name="speech-commands-are-not-working-as-expected"></a>Os comandos de fala não estão funcionando conforme o esperado

* Para usar comandos de fala, as configurações de fala e idioma em seu computador devem ser definidas como um [idioma com suporte na realidade mista do Windows](https://support.microsoft.com/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Para verificar as configurações de idioma e de fala do Windows, selecione **configurações > hora & idioma > região & idioma** e **configurações > hora & linguagem > fala**.
* Se o headset não tiver um microfone interno, você precisará anexar fones de ouvido com um microfone ao headset ou ao seu PC. Para que a entrada do microfone seja alternada automaticamente para o headset quando você o tiver ativado, vá para **configurações > realidade misturada > áudio e fala** e ative "quando eu usar meu Headset, mude para microfone MIC".
* Alguns headsets de áudio têm um botão físico para ativar mudo e mudo do microfone. Se os comandos de fala não estiverem funcionando, verifique se o microfone está mudo.
* Os headsets de áudio com um microfone que Dangles do cabo earbud não fazem bem para comandos de voz em ambientes com ruídos de ambiente.
* A Cortana pode ser lenta na primeira vez em que ela é invocada em uma sessão do portal da realidade misturada. Vá para **configurações > Cortana > fale com a Cortana** e certifique-se de que "permitir que a Cortana responda ao Ei Cortana" esteja habilitado.
* Em alguns PCs, o lucro de captura de voz padrão para o microfone conectado ao headset pode estar definido como muito baixo. Se você tiver comandos de fala não confiáveis ou ditado, execute a solução de problemas de configuração do microfone:
    1. Vá para o aplicativo de desktop na página inicial do Windows Mixed Realm ao utilizar o headset (para afetar o microfone que você usa para a realidade mista do Windows).
    2. Vá para **configurações > hora & idioma > fala**.
    3. Selecione "introdução" na seção "microfone".
    4. Selecione o ponto de extremidade apropriado no assistente de solução de problemas.

## <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Tenho apenas um headset de áudio e quero usá-lo para área de trabalho e meu Headset

Se você tiver apenas um headset de áudio e não tiver um headset com fones de ouvido internos, conecte o headset de áudio ao PC em vez do headset. Em seguida, desligue "alternar para áudio do headset" nas configurações do portal de realidade misturada.

## <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Quero mudar para o Dolby Atmos para fones de ouvido

Os ambientes de realidade mista do Windows e seus aplicativos usam a tecnologia de áudio espacial do Windows Sonic para fone de ouvido, que é personalizada para experiências de realidade misturada. Outras tecnologias espaciais de áudio, como o Dolby Atmos for fones de ouvido, podem ser aplicadas a aplicativos de tela inteira, como jogos SteamVR, mas não para os ambientes e aplicativos do shell do Windows Mixed Reality (como colocar um navegador da Web na parede da casa Cliff ou o céu loft) que foram projetados usando o Windows Sonic para sons espaciais e acústicos.