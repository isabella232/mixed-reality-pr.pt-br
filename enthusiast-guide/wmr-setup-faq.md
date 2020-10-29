---
title: Perguntas frequentes sobre a instalação do Windows Mixed Reality
description: Obtenha respostas para perguntas comuns de configuração ao trabalhar com a realidade mista do Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
appliesto:
- Windows 10
ms.openlocfilehash: 2e7276e7d734770e29ce41db9a19ef40555fea30
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675461"
---
# <a name="windows-mixed-reality-setup-faq"></a>Perguntas frequentes sobre a instalação do Windows Mixed Reality

Aqui estão algumas informações para ajudar a solucionar problemas que você pode encontrar ao configurar seu headset de imersão de realidade mista do Windows.

## <a name="i-get-a-message-that-says-we-couldnt-download-the-window-mixed-reality-software-or-setup-is-stuck-on-the-hang-tight-while-we-do-some-downloading-page"></a>Recebo uma mensagem que diz "não foi possível baixar o software da realidade misturada do Windows" ou a instalação está presa na página "parar de responder enquanto fazemos alguns downloads".

Experimente o seguinte:
* Vá para **configurações > atualização & segurança > Windows Update** e verifique se Windows Update está ativado. Em seguida, baixe e instale todas as atualizações que estão aguardando para serem instaladas.
* Verifique se o computador está conectado à Internet e tem pelo menos 2 GB de espaço livre de armazenamento.
* Reinicie o computador e tente novamente. Talvez seja necessário repetir várias vezes ou executar a solução de problemas Windows Update para limpar as atualizações pendentes. 

> [!NOTE]
> * Se você estiver em uma rede gerenciada corporativa, verifique com seu administrador. Talvez seja necessário habilitar a realidade mista do Windows. Procurando as instruções do profissional de ti? Consulte **[Este artigo](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality)** .
> * Se sua conexão de rede Wi-Fi estiver definida como medida, altere-a para não medido. **[Saiba mais](https://support.microsoft.com/help/4028458)**

## <a name="i-get-a-message-that-says-something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>Recebo uma mensagem que diz "algo deu errado e não foi possível iniciar a realidade mista do Windows".

Experimente o seguinte:
1. Desconecte o headset do seu computador (ambos os cabos).
2. Reinicie seu computador.
3. Vá para **configurações > atualização & segurança > Windows Update** e verifique se Windows Update está ativado. Em seguida, baixe e instale todas as atualizações que estão aguardando para serem instaladas.
4. Reconecte o headset ao computador e tente a instalação novamente.

Se as etapas acima não funcionarem, tente desinstalar e reinstalar a realidade mista do Windows. Vá para **configurações > realidade misturada > desinstalar** e selecione **desinstalar** . Em seguida, reinicie o seu computador. Para iniciar o processo de instalação novamente, basta conectar seu headset ao seu PC.

## <a name="i-get-a-message-that-says-my-pc-cant-run-windows-mixed-reality"></a>Recebo uma mensagem que diz que meu computador não pode executar a realidade mista do Windows.

Se você receber essa mensagem, seu computador não atenderá aos [requisitos mínimos](https://support.microsoft.com/help/4039260) necessários para executar a realidade mista do Windows. Isso pode ocorrer porque a configuração de hardware do computador não é compatível com a realidade mista do Windows ou porque você precisa [atualizar para a versão mais recente do Windows](https://support.microsoft.com/help/12373).

Observações sobre placas gráficas:

* Se a instalação do Windows Mixed Reality informar que a placa gráfica não atende aos requisitos e você acreditar que ela faz, verifique se o headset está conectado ao cartão correto.
* Consulte o fabricante da placa gráfica para obter a atualização mais recente do driver. A realidade mista do Windows requer um driver de placa gráfica que dá suporte a pelo menos o WDDM 2,2.

## <a name="i-get-a-message-that-says-youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>Recebo uma mensagem que diz: "você está quase lá – este PC não atende aos requisitos mínimos necessários para executar a realidade mista do Windows".

Se você receber essa mensagem, seu computador não atenderá aos requisitos mínimos necessários para a melhor experiência no Windows Mixed Reality. Seu computador pode ser capaz de executar um headset de imersão, mas pode não ser capaz de executar determinados aplicativos ou pode ter problemas com o desempenho.

## <a name="my-xbox-controller-isnt-working"></a>Meu controlador Xbox não está funcionando.

Experimente o seguinte:

* Verifique se o controlador está ligado, totalmente cobrado e conectado ao PC.
* Substitua as baterias do controlador.
* Se você estiver usando um controlador Bluetooth, vá para **configurações > dispositivos > Bluetooth & outros dispositivos** em seu PC e verifique se ele está emparelhado (você deve vê-lo listado na página).

[Saiba mais sobre os controladores do Xbox](https://support.xbox.com/xbox-on-windows/accessories/connect-xbox-one-controller-to-pc)

## <a name="my-motion-controllers-arent-working"></a>Meus controladores de movimento não estão funcionando.
 
Experimente o seguinte:

* Verifique se os controladores estão ligados e totalmente cobrados.
* Substitua as baterias dos controladores.
* Desligue os controladores e ligue-os novamente enquanto os mantém na frente de você. Pressione e mantenha pressionado o botão do Windows por 4 segundos para desativar um controlador e, em seguida, pressione e mantenha-o pressionado novamente por 2 segundos para ativá-lo. 
* Acesse **configurações > dispositivos > Bluetooth & outros dispositivos** em seu PC e verifique se eles estão emparelhados (você deve vê-los listados na página).

[Saiba mais sobre os controladores de animação](controllers-in-wmr.md)

## <a name="i-get-a-message-that-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Recebo uma mensagem que diz "conectar seu headset", mesmo que eu tenha me conectado ao meu Headset

Experimente o seguinte:

* Verifique se o headset está conectado às portas corretas no computador. Ele deve ser conectado à placa gráfica discreta do PC e a uma porta USB 3,0. Veja como identificar as portas corretas:
    * As portas USB 3,0 têm um logotipo especial com uma marca "SS" (indicando "SuperSpeed"). A parte interna da porta é normalmente azul, enquanto as portas USB 2,0 mais antigas geralmente são pretas ou brancas no interior.
    * Se o seu computador tiver duas portas HDMI, use aquela que se conecta à placa gráfica, não a placa-mãe do computador. Nem sempre é óbvio qual é o que, embora as portas discretas geralmente estejam localizadas em um slot de expansão no computador. Se você tentar uma porta e ela não funcionar, tente a outra.
* Acesse o site do fabricante do headset e atualize os drivers e o firmware do headset.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Recebo uma mensagem de erro quando tento criar um limite.

Aqui estão algumas diretrizes para criar um limite:

* Não fique muito perto de uma parede ou de outra obstrução.
* Certifique-se de manter o fone de ouvido na altura de estou e rosto em direção ao seu computador enquanto você rastreia o limite.
* Verifique se o sensor não está bloqueado e se há luz suficiente.
* O espaço que você está rastreando deve ser maior que 3 metros quadrados.
* O espaço não deve ser muito grande ou muito complicado — fique em uma forma geométrica simples sem muita variação e folheio.
* Não entre em seu próprio caminho enquanto estiver rastreando.
* Se você ficar preso em um canto, comece novamente.

**Se eu escolher "conectado e somente à sua posição", que tipo de experiência eu terá?**

"Encaixar e posicionar apenas" significa que você usará o headset sem um limite. Você precisará permanecer em um só lugar, pois não terá nenhum limite para ajudá-lo a evitar obstáculos físicos. Além disso, alguns aplicativos e jogos podem ser projetados para serem usados com um limite, portanto, eles podem não funcionar conforme o esperado.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Como posso obter uma exibição mais clara em meu Headset?

Tente ajustar o ajuste do seu headset. Ajuste sua posição no seu rosto movendo-o para cima e para baixo ou para a esquerda e para a direita, e ajuste as pulseiras para que fique perfeitamente.

Se o headset der suporte a ele, você também poderá ajustar suas configurações de calibragem. Se o headset tiver um botão para ajustar a calibragem, use-o. Se não estiver, vá para **configurações > realidade misturada > qualidade visual** e ajuste a calibragem lá. Para obter mais informações sobre a calibragem para seu dispositivo específico, verifique com o fabricante do headset.

## <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quais idiomas têm suporte no Windows Mixed Reality?

A realidade mista do Windows está disponível nos idiomas a seguir. Se o seu PC estiver definido como um idioma diferente, você ainda poderá usar a realidade mista do Windows, mas a interface aparecerá em inglês (Estados Unidos), e os comandos de fala e o ditado não estarão disponíveis.

* Chinês Simplificado (China)
* Inglês (Austrália)
* Inglês (Canadá)
* Inglês (Grã-Bretanha)
* Inglês (Estados Unidos)
* Francês (Canadá)
* Francês (França)
* Alemão (Alemanha)
* Italiano (Itália)
* Japonês (Japão)
* Espanhol (México)
* Espanhol (Espanha)

Você também pode usar o ditado em uma das linguagens de realidade mista do Windows listadas acima — Basta selecionar **microfone**  no teclado na tela.

A realidade mista do Windows também está disponível nos seguintes idiomas sem comandos de fala ou recursos de ditado:

* Chinês tradicional (Taiwan e Hong Kong)
* Holandês (Países Baixos)
* Coreano (Coreia do Sul)
* Russo (Rússia)

## <a name="when-i-plug-in-my-headset-nothing-happensmixed-reality-portal-doesnt-open"></a>Quando eu conecto meu Headset, nada acontece — o portal de realidade misturada não é aberto.

O portal de realidade misturada, o aplicativo que o conduz pela instalação do Windows Mixed Reality, foi projetado para ser aberto automaticamente quando você conectar um headset compatível. Se ele não abrir, vá para **Iniciar** e digite **portal de realidade misturada** na caixa de **pesquisa**  para abrir o aplicativo a partir daí. Se você não encontrar o portal de realidade misturada, isso pode significar que você precisa [atualizar para a versão mais recente do Windows](https://support.microsoft.com/help/12373) ou que o headset não esteja conectado corretamente ao PC.

## <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer"></a>Não consigo ouvir nenhum som em meu headset ou o som está sendo executado por meio do meu computador.

Se o headset de imersão não incluir fones de ouvido internos, você precisará conectar fones de ouvido à tomada de áudio no headset. (A tomada muitas vezes está localizada logo atrás do visor ou das lentes do headset; Verifique com seu fabricante de headset se você tiver problemas para encontrá-lo.) 

Alguns headsets de áudio têm botões físicos para controlar o volume. Se o áudio não estiver funcionando, verifique se o volume está desativado ou mudo.

O Windows Mixed Reality foi projetado para reproduzir som por meio de um headset de imersão quando você estiver utilizando-o e tiver fones de ouvido conectados a ele. Quando você retirar o fone de ouvido ou virar o visor, o áudio mudará para o dispositivo de reprodução padrão do Windows. Você pode alterar essa configuração em **configurações > realidade misturada > áudio e fala** .

> [!NOTE]
> * O áudio espacial da realidade mista do Windows funciona melhor com fones de ouvido incorporados ou conectados diretamente ao headset de imersão. Alto-falantes de PC ou fones de ouvido conectados ao PC podem não funcionar bem para áudio espacial.
> * A realidade mista do Windows não dá suporte a headsets de áudio Bluetooth.

## <a name="speech-commands-arent-working"></a>Os comandos de fala não estão funcionando.

Para usar comandos de fala, as configurações de fala e idioma do seu PC devem ser definidas como um dos [idiomas](#what-languages-are-supported-in-windows-mixed-reality) com suporte na realidade mista do Windows. Para verificar isso, vá para **configurações > hora & idioma > região & idioma** e **configurações > hora & linguagem > fala** .

Se o headset não tiver um MIC interno, você precisará anexar fones de ouvido com um mic ao headset ou ao seu PC. Para que a entrada do MIC seja alternada automaticamente para o headset quando você o tiver ativado, vá para **configurações > realidade misturada > áudio e fala** e certifique-se de que **, quando eu usar meu Headset, mude para o microfone do headset** esteja ligado.

Alguns headsets de áudio têm um botão físico para ativar mudo e mudo do microfone. Se os comandos de fala não estiverem funcionando, verifique se o microfone está mudo.

## <a name="my-head-mount-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Minha tela de montagem de cabeça não funciona depois de desligar e fazer uma inicialização rápida.

Tente o seguinte:

* Desconecte o cabo de vídeo e o cabo USB da tela de montagem de cabeçalho e, em seguida, conecte-os novamente.

## <a name="my-wi-fi-slows-down-when-i-use-windows-mixed-reality"></a>Meu Wi-Fi fica lento quando uso a realidade mista do Windows

Se você estiver usando uma conexão Wi-Fi de 2,4 GHz, seus controladores de movimento poderão retardar o Wi-Fi. Tente uma das seguintes opções:

* Mude para uma conexão Wi-Fi de 5 GHz, se houver uma disponível. Saiba mais
* Use um adaptador Bluetooth separado para conectar seus controladores de movimento ao seu computador. [Consulte adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

> [!NOTE]
> Os fones de ouvido mais recentes se emparelham diretamente com os controladores por meio de um chip Bluetooth interno e não devem ter esse problema. 

## <a name="see-also"></a>Consulte também
* [Pergunte à comunidade](https://answers.microsoft.com)
* [Entre em contato conosco para obter suporte](https://support.microsoft.com/contactus/)
* [Solução de problemas](troubleshooting-windows-mixed-reality.md)

