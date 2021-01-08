---
title: Perguntas frequentes sobre o uso do Windows Mixed Reality
description: Encontre recursos para perguntas comuns ao trabalhar com aplicativos e hardware do Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
appliesto:
- Windows 10
ms.openlocfilehash: 31a27afa9c96ee8beb8b38f74534fc6f58c01f1d
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98007046"
---
# <a name="using-windows-mixed-reality-faq"></a>Perguntas frequentes sobre o uso do Windows Mixed Reality

Se precisar de ajuda com o uso de um headset de imersão de realidade mista do Windows, confira estes tópicos para obter informações gerais e solução de problemas.

Ainda precisa de ajuda? Para solução de problemas avançada, confira este artigo.

## <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Vejo uma mensagem que diz "controle perdido" ou "não temos um limite para este espaço".

Selecione **iniciar > portal de realidade misturada** na sua área de trabalho. Selecione **menu** e, em seguida, selecione **Executar instalação** para criar um novo limite. O Windows Mixed Reality dá suporte a vários locais e identificará o espaço em que você está na inicialização, desde que a sala não tenha sido alterada.  

## <a name="i-cant-hear-any-sound-or-the-sound-is-coming-from-my-computer-instead-of-my-headset"></a>Não consigo ouvir nenhum som ou o som é proveniente do meu computador em vez do meu Headset

Se o headset de imersão não incluir fones de ouvido internos, você precisará conectar fones de ouvido à tomada de áudio no headset. (A tomada muitas vezes está localizada logo atrás do visor ou das lentes do headset; Verifique com seu fabricante de headset se você tiver problemas para encontrá-lo.) 

Alguns headsets de áudio têm botões físicos para controlar o volume. Se o áudio não estiver funcionando, verifique se o volume está desativado ou mudo.

O Windows Mixed Reality foi projetado para reproduzir som por meio de um headset de imersão quando você estiver utilizando-o e tiver fones de ouvido conectados a ele. Quando você tirar o fone de ouvido ou virar o visor, o áudio mudará para o dispositivo de reprodução padrão do Windows. Você pode alterar essa configuração em **configurações > realidade misturada > áudio e fala**.

> [!NOTE]
> * O áudio espacial da realidade mista do Windows funciona melhor com fones de ouvido incorporados ou conectados diretamente ao headset de imersão. Alto-falantes de PC ou fones de ouvido conectados ao PC podem não funcionar bem para áudio espacial.
> * A realidade mista do Windows não dá suporte a headsets de áudio Bluetooth.

## <a name="speech-commands-arent-working"></a>Os comandos de fala não estão funcionando

Para usar comandos de fala, as configurações de fala e idioma do seu PC devem ser definidas como uma [região e linguagem de realidade mista do Windows com suporte](other-questions.md#what-languages-are-supported-in-windows-mixed-reality). Para verificar sua região e idioma do Windows, selecione **configurações > hora & idioma > região & idioma**. Para verificar sua linguagem de fala, selecione **configurações > hora & idioma > fala**.

Se o headset não tiver um MIC interno, anexe um par de fones de ouvido com um mic ao seu headset ou PC. Selecione **configurações > realidade misturada > áudio e fala** para alternar automaticamente a entrada do MIC para o headset quando os fones de ouvido estiverem conectados. Certifique-se de que **, quando eu usar meu Headset, mude para o MIC do headset** esteja ligado.

Alguns headsets de áudio têm um botão físico para ativar mudo e mudo do microfone. Se os comandos de fala não estiverem funcionando, verifique se o microfone está mudo.

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>O limite é sempre visível. Como posso fazê-lo desaparecer?

Quando você estiver perto do limite, ele será exibido. Se o seu limite incluir seções que tenham uma forma estreita ou irregular, você poderá acabar ficando perto dela — e fazendo com que ela apareça — com mais frequência do que você gostaria. Para corrigir isso, tente criar o limite novamente, usando uma forma maior e mais regular. Selecione **iniciar > portal de realidade misturada** na área de trabalho e selecione **Executar instalação**. 

Você também pode desativar temporariamente o limite do portal de realidade misturada: selecione o **menu** e, em seguida, use a alternância para desativar o limite. Quando o limite for desativado, você precisará permanecer em um ponto para evitar obstáculos.

## <a name="im-having-trouble-with-my-motion-controllers"></a>Estou tendo problemas com meus controladores de movimento

Se os seus controladores de movimento não estiverem funcionando corretamente, não estão se conectando ou se você não vir uma imagem dos controladores quando estiver desgastando o headset:

* Verifique se os controladores estão ativados. Para ativá-los, pressione e mantenha pressionado o botão do **Windows** por 2 segundos.
* Selecione **iniciar > portal de realidade mista** em seu PC e, em seguida, selecione **menu** para ver os controladores de movimento listados, juntamente com uma mensagem de status:
    * Pronto – os controladores estão todos definidos.
    * Rastreamento perdido – o portal de realidade misturada não pode localizar seus controladores. Mantenha-os na frente do headset e reinicie-os pressionando o botão **Windows** por 4 segundos e, novamente, por 2 segundos.
    * Bateria fraca – Substitua as baterias do controlador.
* Se estiver usando Wi-Fi, tente conectar seu PC a uma rede de Wi-Fi de 5 GHz para reduzir a interferência sem fio. 
* Para fones de ouvido mais recentes que emparelham diretamente com os controladores, selecione o **"..."** no **portal de realidade misturada** e escolha **configurar controladores**. Isso levará você ao aplicativo Headset para emparelhar os controladores com o headset.  
* Para fones de ouvido mais antigos que não têm Bluetooth interno para os controladores emparelharem diretamente:  
    * Selecione Configurações > dispositivos > Bluetooth & outros dispositivos em seu PC e verifique se os controladores estão listados como emparelhados.Se não forem, você precisará emparelhar. 
    * Se você tiver outros dispositivos Bluetooth emparelhados com seu PC, como fones de ouvido ou gamepads, tente remover alguns. Selecione **configurações > dispositivos > Bluetooth & outros dispositivos** em seu computador, selecione os dispositivos e, em seguida, selecione **remover dispositivo**.
    * Remova os fones de ouvido e os alto-falantes Bluetooth em **configurações > dispositivos > Bluetooth & outros dispositivos** e desative os dispositivos. 
    * Se você estiver usando um adaptador Bluetooth USB, verifique se ele está conectado a uma porta USB 2,0 preta. Além disso, verifique se o adaptador está conectado o mais distante possível de qualquer outro transmissor sem fio ou unidades flash USB, incluindo o conector USB para o headset. 
    * Se o seu computador tiver um Bluetooth interno e você estiver tendo problemas de conexão, tente usar um adaptador USB Bluetooth em vez disso. (Para fazer isso, você também precisará desligar sua rádio Bluetooth interna no [Device Manager](https://support.microsoft.com/help/4026149)e emparelhar os outros dispositivos Bluetooth com o novo adaptador.)
* Se o aplicativo Configurações estiver aberto na página Bluetooth & outros dispositivos, feche-o.

## <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Estou tendo discomfort quando uso meu Headset

Para obter informações gerais sobre o conforto na realidade misturada do Windows, consulte [integridade de fone de ouvido de imersão, segurança e conforto do Windows Mixed Reality](wmr-health-safety-comfort.md). Para obter detalhes sobre o fone de ouvido específico, verifique com o fabricante do headset.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Meus elementos visuais estão instável, carregam lentamente ou não parecem bons

Se os visuais de realidade misturada não têm a melhor aparência:

* Verifique se o headset está conectado à placa gráfica correta no seu computador. Alguns PCs têm placas gráficas integradas e discretas. O cartão discreto geralmente oferecerá o melhor desempenho. [Saiba mais sobre hardware de PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Feche os aplicativos não utilizados na área de trabalho.
* Ajuste o ajuste do headset: Mova-o para o sentido inferior e superior, para a esquerda e para a direita, e verifique se ele se encaixa perfeitamente.
* Ajuste as configurações visuais do headset (**configurações > realidade misturada > tela de headset**). Quando a **qualidade visual** for definida como **automática**, escolheremos a melhor experiência de realidade misturada para seu PC. Para obter uma experiência com mais detalhes visuais, defina a **qualidade visual** como **alta**. Se os visuais estiverem ruins, talvez você queira selecionar uma configuração mais baixa.
* Tente ajustar a calibragem do headset. As lentes devem ser ajustadas para corresponder à sua distância de Interpupillary (IPD), a distância entre o Pupils. Se você não souber seu IPD, um optometrist poderá medir para você. Também há sites criados para medir o IPD. Depois de saber seu IPD, use o botão de calibragem do headset para fazer ajustes. Se o headset não tiver um botão de calibragem, selecione **configurações > realidade misturada > tela de headset** e ajuste o controle de calibragem.

## <a name="i-have-questions-about-my-headset-hardware"></a>Tenho dúvidas sobre o meu hardware de headset

Para obter detalhes sobre o headset, verifique com o fabricante. Pode haver um guia de produto na caixa, ou você pode experimentar o site do fabricante.

## <a name="the-floor-in-mixed-reality-seems-to-be-in-the-wrong-spot"></a>O andar em realidade misturada parece estar no local errado

Se a base parecer desativada (por exemplo, você parece que está flutuante), selecione **iniciar > o ajuste de sala** enquanto estiver aproveitando o headset para fazer alterações.

## <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Recebi uma mensagem que disse para conectar e encarregar meu PC. Por quê?

Se você estiver usando um laptop, a realidade mista do Windows funcionará melhor quando o PC for totalmente cobrado e conectado.

## <a name="how-do-i-uninstall-windows-mixed-reality"></a>Como fazer desinstalar o Windows Mixed Reality?

Selecione **iniciar > configurações > realidade misturada** e, em seguida, selecione **desinstalar**. Desconecte o headset do seu PC e feche o portal de realidade misturada antes de desinstalar o.

Quando você estiver pronto para começar a usar o headset novamente, conecte-o e o portal de realidade mista o guiará pela instalação.

> [!NOTE]
> Se você vir uma mensagem dizendo "não foi possível concluir a remoção da realidade mista do Windows", isso significa que alguns arquivos, incluindo informações sobre seu ambiente, ainda podem estar no seu computador. Isso pode causar problemas se você decidir reinstalar o Windows Mixed Reality posteriormente.
> 
> Para saber como remover manualmente qualquer informação restante do Windows Mixed realm do seu PC, consulte **[Este artigo](installation_errors.md)**.

## <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Meu Wi-Fi fica lento quando estou usando a realidade mista do Windows

Se você estiver usando uma conexão Wi-Fi de 2,4 GHz, seus controladores de movimento poderão tornar o seu Wi-Fi mais lento:

<!-- TODO: Use Windows Mixed Reality PC hardware guidelines interlink -->
* Mude para uma conexão de 5 GHz Wi-Fi, se houver uma disponível. [Saiba mais](https://support.microsoft.com/help/4000461)
* Use um adaptador Bluetooth separado para conectar seus controladores de movimento ao seu computador. [Consulte adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

## <a name="what-is-the-experience-options-setting"></a>O que é a configuração de opções de experiência?

A configuração de opções de experiência (**configurações > realidade misturada > exibição de fone de ouvido > opções de experiência**) oferece a capacidade de alterar as configurações de desempenho da realidade mista do Windows. Isso permite que você escolha a melhor experiência possível para sua configuração de hardware em uma variedade de conteúdo. A experiência de 90 Hz está disponível para todos os sistemas, mas talvez você queira testar automaticamente primeiro para ver qual configuração prefere.

Aqui estão as opções:

* Automático ou deixe que o Windows decida: a realidade mista do Windows determinará a melhor experiência para sua configuração de hardware. Para a maioria das pessoas, essa é a melhor opção para começar.
* 60 Hz: define a taxa de atualização para 60 Hz e desativa determinados recursos, como captura de vídeo e visualização no portal de realidade misturada.
* 90 Hz: define a taxa de atualização para 90 Hz se o headset puder ser executado nessa velocidade. Se os problemas de cabo impedirem que o headset seja executado às 90 Hz, você poderá ver um erro na inicialização com esse modo selecionado. 

## <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Vejo uma mensagem que diz "Put on the headset", embora eu tenha meu Headset em

Quando você coloca em seu headset, a realidade mista do Windows precisa de um pouco de tempo para recarregar seu espaço. Isso pode levar alguns segundos. Se essa mensagem não desaparecer, verifique se o adesivo de proteção foi removido do sensor de proximidade, que está dentro do headset, entre as lentes. Se o adesivo tiver sido removido e você ainda tiver problemas, entre em contato com o fabricante do headset. Pressionar **Win + Y** no teclado irá disparar manualmente o headset para ser executado se o sensor de proximidade não estiver disparando automaticamente. 

Ainda precisa de ajuda? Para solução de problemas avançada, confira [Este artigo](troubleshooting-windows-mixed-reality.md).

## <a name="see-also"></a>Veja também

* [Pergunte à comunidade](https://answers.microsoft.com)
* [Entre em contato conosco para obter suporte](https://support.microsoft.com/contactus/)