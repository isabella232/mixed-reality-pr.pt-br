---
title: Controladores no Windows Mixed Reality
description: Saiba como configurar e usar controladores no Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
appliesto:
- Windows 10
ms.openlocfilehash: f349f4bbc2cadd511515783504562052f1d58ed3
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725387"
---
# <a name="motion-controllers-in-windows-mixed-reality"></a>Controladores de movimentos no Windows Mixed Reality

Os controladores de movimento são acessórios de hardware que permitem que os usuários interajam em realidade misturada. Uma vantagem dos controladores de movimento em gestos é que os controladores têm uma posição precisa no espaço, permitindo uma interação refinada com objetos digitais. Para os headsets de imersão de realidade misturada do Windows, os controladores de movimento são a principal maneira que os usuários executarão ações em seu mundo.

Os controladores de movimento de realidade mista do Windows oferecem controle de movimento preciso e responsivo em seu campo de exibição por meio dos sensores de headset de imersão. Não há necessidade de instalar o hardware nas paredes no seu espaço. Esses controladores de movimento oferecerão a mesma facilidade de instalação e portabilidade que os headsets de imersão de realidade misturada do Windows.

Você também pode usar um controlador Xbox, um mouse e um teclado ou contornar [usando apenas sua voz](using-speech-in-wmr.md).

## <a name="motion-controller-setup"></a>Configuração do controlador de movimento

A maioria dos headsets vem emparelhada diretamente com o headset, mas alguns headsets iniciais exigem que os controladores de movimento sejam emparelhados em seu PC com o Bluetooth 4,0. Ao conectar o headset de imersão pela primeira vez, você será percorrido a ativação de seus controladores de movimento durante a instalação. Mas se você precisar repairá-los mais tarde, veja como:

1. Inicie o **portal de realidade misturada** com o headset conectado.  
2. No canto inferior esquerdo, selecione **... > configurar controladores**.
3. Insira duas baterias AA em cada controlador e coloque seu controlador no modo de emparelhamento (consulte as instruções na [seção de controladores de movimento de par](controllers-in-wmr.md#pair-motion-controllers)
4. Siga as instruções fornecidas na tela.

> [!NOTE]
> * Para controladores que emparelham diretamente com seu PC, você precisará colocá-los no modo de emparelhamento ativando-os e, em seguida, pressionando o botão de emparelhamento dentro do compartimento da bateria até que as luzes comecem a piscar.
> * Os controladores de movimento dão suporte apenas a pares em um computador por vez. Se você precisar usá-los com um headset diferente, precisará passar pelo processo de emparelhamento. Consulte [Configurar a realidade mista do Windows](set-up-windows-mixed-reality.md)

[Obter ajuda para se conectar](wmr-setup-faq.md#my-motion-controllers-arent-working)

> [!IMPORTANT]
> **Tem um controlador Xbox?**
> 
> Se você tiver um controlador Xbox do Bluetooth, emparelhe-o com seu PC para usá-lo com o headset.
> 
> Se você tiver um controlador Xbox com fio, conecte-o ao seu PC.
> 
> Alguns jogos e aplicativos usam o controlador Xbox de forma diferente de como são usados na realidade misturada. Para usar o controlador para um jogo ou aplicativo, selecione **usar como gamepad** na barra de aplicativos ou, por exemplo, "usar como Gamepad". Para mudar o controlador para a realidade misturada, selecione **usar como gamepad**, novamente ou, por exemplo, "usar com olhar".  

## <a name="pair-motion-controllers"></a>Emparelhar controladores de movimento

Se você estiver usando um headset que inclui um controlador Bluetooth integrado, como o Samsung Odyssey + ou HP reverbs, seus controladores já devem estar emparelhados. Mas você ainda pode emparelhar seus controladores usando o aplicativo de instalação (ele já deve estar instalado durante a configuração do HMD. Você também pode obtê-lo da Microsoft Store).

### <a name="pair-motion-controllers-to-hmd"></a>Emparelhar controladores de movimento para HMD

Ligue os controladores pressionando o botão Windows por 2 segundos até que os LEDs se acendam.

Remova a tampa da bateria dos controladores e localize o pequeno botão de emparelhamento na borda do controlador. Mantenha esse botão inoperante para emparelhar com seu PC.
    ![Emparelhamento do controlador de movimento](images/connect_controller.png)

Inicie o **portal de realidade misturada** com o headset conectado.  
No canto inferior esquerdo, selecione **... > configurar controladores**.
Siga as instruções na tela.

### <a name="pair-motion-controllers-to-pc"></a>Emparelhar controladores de movimento com o PC

Você pode emparelhar seu controlador a um computador adicionando outro dispositivo Bluetooth.

Ligue os controladores e coloque-os em modo de emparelhamento, conforme descrito acima.

* Navegue até configurações do computador
* Dispositivo/adicionar Bluetooth ou outro dispositivo.

Quando o emparelhamento for concluído, os LEDs serão sólidos e brilhantes.

### <a name="common-issues"></a>Problemas comuns

* Verifique se você tem apenas uma rádio Bluetooth ativa em seu computador. Se você tiver mais de um rádio Bluetooth, precisará desabilitar as outras rádios em Device Manager.
* Coloque seu dongle Bluetooth em uma porta que tenha uma clara linha de visão para seus controladores e longe de conectar dispositivos USB 3,0. O USB 3,0 é conhecido por ter interferência de RF com Bluetooth (leia [Este artigo](https://www.intel.com/content/dam/www/public/us/en/documents/white-papers/usb3-frequency-interference-paper.pdf) da Intel para obter mais detalhes). Portas USB 2,0 podem funcionar melhor para seu dongle Bluetooth.
* Verifique se o dongle Bluetooth não está conectado a uma porta USB ao lado do cabo USB do seu HMD. O cabo do headset também tem sido conhecido por causar interferências com dongles Bluetooth. Conecte o dongle na porta USB frontal no seu PC para obter os melhores resultados.
* Para notebooks, verifique se a Wi-Fi está conectada à banda de 5 GHz para obter a melhor experiência. Selecione o ícone de rede sem fio inferior à bandeja direita e selecione Propriedades para a rede que você está usando. Os notebooks projetados para compartilhar uma antena de 2,4 GHz para conectividade Bluetooth e WiFi verão o congestionamento de dados de velocidades de rede lentas ou desempenho de rastreamento do controlador de movimento insatisfatório.
* Seus controladores de movimento receberão novas atualizações de software da Microsoft regularmente. Os controladores mostrarão um padrão alternado de luzes piscantes quando receberem essas novas atualizações de software. Isso é normal. Aguarde até que a atualização de software seja concluída antes de usar os controladores. Os controladores ficarão vibrantes e uma luz constante substituirá o padrão flash alternado quando terminar.
* Você pode ser instruído a "colocar o headset e usar o Thumbstick para teleport" antes que os controladores concluam o processo de atualização. Os controladores não estarão visíveis ou utilizáveis até que a atualização seja concluída. A maioria das atualizações ocorre dentro de dois minutos, mas as atualizações podem levar até 10 minutos. Aguarde a conclusão da atualização antes de prosseguir para a próxima etapa.

## <a name="using-controllers"></a>Usando controladores

Veja como contornar uma realidade misturada com os controladores de movimento, um gamepad do Xbox ou um mouse e um teclado.

> [!TIP]
> Para alternar a entrada entre realidade misturada e sua área de trabalho, pressione a **tecla do logotipo do Windows + Y** no teclado do seu PC.

![Mapeamento de botão do controlador de movimento](images/get_to_know_controllers.png)

|  Para fazer isso  |  Controladores de movimento  | Gamepad | Mouse + teclado |
| --- | --- | --- | --- |
| Teleport | Pressione o Thumbstick para frente e aponte o controlador para onde você deseja ir. Libere o Thumbstick. | Pressione o Thumbstick esquerdo para frente e, em seguida, procure onde deseja ir. Libere o Thumbstick. | Selecione e mantenha o botão direito e, em seguida, aponte o mouse para onde deseja ir. Solte o botão. |
| Selecionar | Aponte o controlador e, em seguida, receba o gatilho ou use o touchpad. | Olhar no destino e, em seguida, pressione A. | Aponte o mouse e clique com o botão esquerdo. |
| Abra o menu Iniciar | Pressione o botão **Windows** . | Pressione o botão **Xbox** . | Pressione a **tecla do logotipo do Windows**. |
| Deixar um aplicativo de imersão | Pressione o botão **Windows** . Em seguida, selecione **início da realidade misturada** no menu ações rápidas. | Pressione o botão **Xbox** . Em seguida, selecione o botão **página inicial da realidade misturada** no menu ações rápidas. | Pressione a tecla de logotipo * * do Windows. Em seguida, selecione o botão **página inicial da realidade misturada** no menu ações rápidas que aparece. |
| Rotate | Mova o Thumbstick para a esquerda ou para a direita. | Mover o direcional direito para a direita ou para a direita. | Não disponível. |
| Fazer backup | Mover o Thumbstick para trás. | Mover o movimento para a esquerda para trás. | Não disponível. |
| Walk | Envie o Thumbstick diretamente para baixo e, em seguida, pressione-o na direção que você deseja percorrer. | Pressione o dedo para a esquerda diretamente para baixo e, em seguida, aperte-o na direção que você deseja percorrer. | Não disponível. |
| Mover uma janela do aplicativo | Aponte para a barra de aplicativos. Puxe e segure o gatilho para pegar a janela e, em seguida, use o controlador para movê-lo em qualquer direção. Libere o gatilho. | Olhar na barra de aplicativos e, em seguida, pressione e segure um para pegar a janela. Use a tecla esquerda para mover a janela lado a lado ou para cima e para baixo. Use os gatilhos para movê-los para mais perto e longe. Em seguida, libere um. | Aponte o mouse na barra de aplicativos. Clique e mantenha pressionado para capturar a janela e, em seguida, use o mouse para movê-la lado a lado ou para cima e para baixo. Use a roda de rolagem para mover a janela de perto ou para longe. Solte o botão do mouse. |
| Mover um objeto 3D | Aponte para o objeto e, em seguida, puxe e segure o gatilho para captar. Mova-o em qualquer direção com o controlador e, em seguida, libere o gatilho. | Olhar no objeto e, em seguida, pressione e segure um para pegar. Use a tecla esquerda para mover a janela lado a lado ou para cima e para baixo. Use os gatilhos para movê-los para mais perto e longe. Em seguida, libere um. | Aponte o mouse para o objeto. Clique com o botão esquerdo do mouse e mantenha-o pressionado para movê-lo e, em seguida, use o botão de movimentação para cima e para baixo.  Para movê-lo mais perto ou distante, use a roda de rolagem. Solte o botão do mouse. |
| Girar ou redimensionar uma janela do aplicativo | Aponte um controlador na barra de aplicativos e o outro controlador em qualquer lugar na janela. Mantenha os dois gatilhos e, em seguida, mova os controladores juntos ou decrescentes para redimensionar.  Para girar, mova um controlador para você e o outro longe de você. Libere os gatilhos. | Selecione **ajustar** na barra de aplicativos. Olhar em um canto do quadro de ajuste e, em seguida, pressione um para selecioná-lo. Use o pente esquerdo para redimensionar a janela.  | Selecione **ajustar** na barra de aplicativos. Selecione e mantenha um canto do quadro de ajuste e, em seguida, use o mouse para redimensionar a janela. |
| Girar ou redimensionar um objeto 3D | Aponte ambos os controladores no objeto. Mantenha os dois gatilhos e, em seguida, mova os controladores juntos ou decrescentes para redimensionar.  Para girar, mova um controlador para você e o outro longe de você. | Selecione **ajustar** na barra de aplicativos e, em seguida, mova o objeto usando o pente à esquerda. | Selecione **ajustar** na barra de aplicativos e, em seguida, selecione e segure o objeto e use o mouse para movê-lo. |
| Rolar em uma janela do aplicativo | Puxe e segure o gatilho e, em seguida, mova o controlador para cima ou para baixo.  | Use o painel D. | Use a roda de rolagem do mouse. |
| Ampliar ou reduzir na janela do aplicativo | Extraia ambos os gatilhos e, em seguida, mova os controladores mais perto ou distantes. | Puxe o gatilho direito para ampliar e o gatilho esquerdo para reduzir. | Use a roda de rolagem do mouse enquanto mantém pressionada a tecla CTRL no teclado. |
| Abrir um menu | Pressione o botão de **menu** . | Pressione o botão de **menu** . | Clique com o botão direito do mouse. |

## <a name="what-do-the-vibrations-and-lights-mean"></a>O que significam as vibraçãos e luzes

Seu controlador se comunica com o que está fazendo, vibrando e piscando suas luzes de LED.

|  Quando o controlador faz isso  |  Isso significa que isso |
| --- | --- |
| Os LEDs acendem e o controlador vibra uma vez | **Ativando** |  
| Os LEDs desligam e o controlador vibra duas vezes | **Desligando** |
| LEDs piscam a cada 3 segundos | **Hibernando** |
| Os LEDs pulsam lentamente e o controlador vibra uma vez | **Entrando no modo de emparelhamento** |
| O controlador vibra uma vez | **Conectando ou desconectando do seu PC** |
| Os LEDs estão iluminados com brilho | **Controladores acompanhados por Headset** |
| Os LEDs estão Dimly acesos | **Controladores não acompanhados por Headset** |
| O controlador vibra três vezes e, em seguida, desliga | **Nível de bateria crítica** |
| Os anéis externos e internos de LEDs piscam em um padrão alternado | **Atualizar** |

## <a name="updating-motion-controllers-firmware"></a>Atualizando o firmware dos controladores de movimento

* Se um headset de imersão estiver conectado ao seu computador e o novo firmware do controlador estiver disponível, o firmware será enviado por push para seus controladores de movimento automaticamente na próxima vez que forem ativados.
* Atualizações de firmware do controlador são mostradas com um padrão de quadrantes de LED de iluminação em um movimento circular e levam de 1-2 minutos. Às vezes, as atualizações de firmware podem levar mais tempo, até 10 minutos, o que pode indicar pouca conectividade Bluetooth ou interferência de rádio.
* Caso a atualização do firmware seja interrompida (controlador desligado ou a bateria se esgotar), ela será tentada novamente na próxima ativação.
* Após a conclusão da atualização do firmware, os controladores serão reinicializados e reconectados.
* Ambos os controladores devem estar conectados agora. Navegue até o portal de realidade misturada para verificar o status dos controladores.
* Verifique se os controladores funcionam corretamente:
  * Inicie o **portal de realidade misturada** e insira sua página inicial de realidade misturada.
  * Mova seus controladores e verifique o acompanhamento, os botões de teste e verifique se a teleportabilidade funciona. Se não estiverem, confira [a seção solução de problemas do controlador de movimento](motion-controller-problems.md)

## <a name="faq"></a>Perguntas frequentes

### <a name="how-can-i-check-battery-level"></a>Como posso verificar o nível da bateria?

*R: o nível da bateria está no lado inverso do modelo virtual, não há um indicador de nível de bateria física. Depois de ligar o controlador, aguarde alguns segundos para permitir que a leitura seja estabilizada.*

### <a name="can-you-use-these-controllers-without-a-headset-just-for-the-joysticktriggeretc-input"></a>Você pode usar esses controladores sem um headset? Apenas para a entrada joystick/Trigger/etc?

*R: não para aplicativos universais do Windows*

## <a name="filing-motion-controller-feedbackbugs"></a>Arquivando comentários/bugs do controlador de movimento

Envie-nos comentários no Hub de comentários usando a categoria "realidade misturada-> entrada".

## <a name="see-also"></a>Consulte também

- [Controladores HP no Unity](https://docs.microsoft.com/windows/mixed-reality/develop/unity/unity-reverb-g2-controllers)
- [Controladores HP em não reais](https://docs.microsoft.com/windows/mixed-reality/develop/unreal/unreal-reverb-g2-controllers)
- [Pergunte à comunidade](https://answers.microsoft.com)
- [Entre em contato conosco para obter suporte](https://support.microsoft.com/contactus/)
- [Solução de problemas](troubleshooting-windows-mixed-reality.md)

Está tendo problemas com seus controladores de movimento? [Obter ajuda](motion-controller-problems.md)