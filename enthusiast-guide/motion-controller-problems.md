---
title: Perguntas frequentes do controlador de movimento
description: Controladores Windows Mixed Realm insolução de problemas que vão além da nossa documentação padrão de suporte ao consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte, controladores de movimento
appliesto:
- Windows 10
ms.openlocfilehash: 7d3cdae2e098504a755369e3c829c1d4a6142b9d
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93132020"
---
# <a name="motion-controller-faqs"></a>Perguntas frequentes do controlador de movimento

## <a name="what-do-the-vibrations-and-lights-mean"></a>O que significam as vibraçãos e luzes

O LED Constellation Ring e haptics indicam o estado do controlador de movimento.

| Estado    | Comportamento associado ao estado | Como chegar/sair do estado |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Ligue**               | Os LEDs acendem e o controlador vibra uma vez. | Pressione e mantenha o botão do Windows no controlador por dois segundos para ativar o controlador.  |
| **Desligar**              |  Os LEDs desligam e o controlador vibra duas vezes. | Pressione e mantenha o botão do Windows no controlador por quatro segundos para desligar o controlador.   |
| **Hibernando**               |  Os LEDs desligam e piscam a cada três segundos durante o estado de suspensão. | O controlador entra no estado de suspensão automaticamente quando não está em movimento por 30 segundos. O controlador é ativado quando detecta o movimento, exceto se o dispositivo não estiver emparelhado com o PC host. Pressione o botão para ativá-lo nesse caso. |
| **Emparelhamento**                |  Os LEDs pulsam lentamente enquanto estão no modo de emparelhamento e entram sólidos ao sair do modo de emparelhamento. O controlador vibra uma vez se o emparelhamento tiver sido bem-sucedido ou três vezes se o emparelhamento não for bem-sucedido e o tempo limite for atingido. | Pressione e segure o botão de emparelhamento dentro do caso da bateria por três segundos.     |
| **O controlador conecta/desconecta do PC** |  O controlador vibra uma vez na conexão do PC ou na desconexão. | Isso acontece quando o controlador se conecta com êxito ao PC depois que você o liga, ou se o controlador se desconecta do PC durante o uso.|
| **Nível de bateria fraca**      | Haptics são desabilitados quando a bateria está baixa (não há nenhuma indicação de LED). O ícone de indicador de bateria no identificador do controlador em Headset mostrará 1/4 cheio quando a bateria estiver baixa. | Substitua suas baterias. | 
| **Nível de bateria crítica** |  O controlador vibra três vezes quando você o ativa e, em seguida, desliga automaticamente. O ícone de indicador de bateria ficará vermelho. | Substitua as baterias. Se o problema persistir, [restaure o dispositivo para suas configurações de fábrica](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>Meus controladores de movimento não estão funcionando corretamente

Se os seus [controladores de movimento](controllers-in-wmr.md) não estiverem funcionando, não estiver se conectando ou se você não vir uma imagem dos controladores quando estiver desgastando o headset, tente o seguinte:

1. Verifique se os controladores estão ativados. Para ativá-los, pressione e mantenha pressionado o botão Windows por dois segundos.
2. Certifique-se de que os controladores sejam totalmente cobrados e substitua as baterias, se não estiverem.
3. Desligue os controladores e ligue-os novamente enquanto os mantém na frente de você. Pressione e mantenha pressionado o botão do Windows por quatro segundos para desativar um controlador e, em seguida, pressione e mantenha-o pressionado novamente por dois segundos para ativá-lo.
4. Verifique se os controladores de movimento estão [emparelhados corretamente](controllers-in-wmr.md#pair-motion-controllers).
5. Verifique os LEDs dos controladores de movimento: controladores acesos brilhantes estão emparelhados e conectados, Dimly os controladores acesos não estão conectados.
6. Acesse **iniciar > portal de realidade misturada** no seu PC e selecione "menu". Você deve ver seus controladores de movimento listados, juntamente com uma mensagem de status:
    * Pronto – os controladores estão todos definidos.
    * Rastreamento perdido – o portal de realidade misturada não pode localizar seus controladores. Mantenha-os na frente do headset e reinicie-os pressionando o botão Windows por quatro segundos e, em seguida, novamente por dois segundos.
    * Bateria fraca – Substitua as baterias do controlador.
7. Se você estiver usando um adaptador Bluetooth USB externo, verifique se ele está conectado a uma porta USB 2,0 (geralmente, mas nem sempre preto). Ele também deve ser conectado o máximo possível de qualquer outro transmissor sem fio ou unidades flash USB, incluindo o conector USB para o headset. 
8. Para verificar se há apenas um rádio Bluetooth no PC, acesse **Device Manager > Bluetooth** e procure um adaptador. Se você estiver usando a configuração de computador desktop com rádio interno, verifique se uma antena externa está conectada. Se não houver nenhuma antena externa conectada, isso poderá causar problemas de controle. Ou use um dongle Bluetooth externo (USB), desabilite o recurso Bluetooth interno e tente emparelhar e se conectar novamente.
9. Se a janela configurações de Bluetooth estiver aberta em segundo plano, muitas chamadas extras serão feitas no protocolo Bluetooth. Feche-o.
10. Verifique o nível da bateria virtual no controlador de movimento girando os controladores em realidade misturada para ver o ícone de bateria. Aguarde cerca de 15 segundos antes de ler o nível, pois o nível relatado é maior do que o nível real imediatamente após conectar um controlador. Substitua as baterias se o ícone estiver vermelho.
11. Remova os fones de ouvido e os alto-falantes Bluetooth em **configurações > dispositivos > Bluetooth & outros dispositivos** e desligue os dispositivos. Use a tomada de fone de ouvido ou os palestrantes internos em seu headset de realidade misturada para obter a melhor experiência de áudio.
12. Remova outros dispositivos Bluetooth que possam estar emparelhados com seu PC, como fones de ouvido ou gamepads. Acesse **configurações > dispositivos > Bluetooth & outros dispositivos** , selecione os dispositivos e, em seguida, "remover dispositivo".
13. Desconecte o cabo USB em seu headset e conecte-o novamente ao computador para reiniciar a realidade mista do Windows.
14. As luzes do controlador piscam quando estão passando por uma atualização de firmware. Aguarde a conclusão da atualização e os controladores devem aparecer em realidade misturada.
15. Verifique se o computador está conectado a uma rede de 5 GHz Wi-Fi. Se o seu laptop estiver conectado a uma rede WiFi de 2,4 GHz, ele normalmente está compartilhando a conexão Bluetooth. Isso pode afetar negativamente o desempenho de WiFi ou Bluetooth, dependendo do design do produto. Altere a banda preferencial para 5 GHz nas configurações do adaptador de rede. Se sua rede não der suporte a 5 GHz, um dongle Bluetooth poderá ser usado em vez do recurso Bluetooth interno.
16. Se as configurações de Bluetooth já tiverem os controladores de movimento emparelhados, o Windows não descobrirá os novos dispositivos até que eles sejam removidos (se tiverem sido adicionados usando um dongle específico, eles só poderão ser removidos com esse dongle).
17. Se o seu computador tiver um Bluetooth interno e você estiver tendo problemas de conexão, tente usar um adaptador USB Bluetooth. Para fazer isso, desative seu rádio Bluetooth interno em Device Manager e, em seguida, emparelhe os outros dispositivos Bluetooth com o novo adaptador.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Meus controladores tremulam, ficam presos ou cintilam e desaparecem em realidade misturada

* Se o seu PC estiver sendo executado em 2,4 GHz, mude para WiFi de 5 GHz. 
* Se você estiver usando um adaptador Bluetooth externo, verifique se ele está conectado a uma porta USB 2,0 (que é geralmente, mas não sempre, preto), longe de outros transmissores sem fio ou unidades flash USB.
* Execute o solucionador de problemas de Bluetooth em **configurações > atualização & segurança > solucionar problemas > Bluetooth** .

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Meu controlador está preso em uma reinicialização infinita

Esse é um indicador de bateria crítica. Coloque as novas baterias no dispositivo e, se o problema persistir, [redefina o controlador para as configurações de fábrica](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>O portal de realidade misturada está funcionando, mas meus controladores estão acompanhando mal (pilotando, agitando, etc.)

1. As condições de iluminação podem afetar o controle. Certifique-se de que você não está exposto para direcionar a luz solar e que você não tem muitas fontes de luz de ponto visíveis para seu HMD (por exemplo, cadeias de caracteres de luzes como uma árvore de Natal).
2. Esses sintomas geralmente são causados por falhas na comunicação entre o controlador e o PC host e indicam uma qualidade de link Bluetooth ruim. Consulte as [perguntas sobre o Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Os LEDs do controlador de movimento não estão acesos, mas os botões e Thumbstick ainda funcionam no portal de realidade misturada

O cache de calibragem do controlador de movimento pode estar corrompido. Para excluir o cache, execute o seguinte comando em um prompt de comando de administrador:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Essa pasta não está acessível no Windows Explorer e só pode ser modificada a partir de um prompt de comando de administrador. Depois de excluir a pasta, reinicie o computador e reconecte seus controladores de movimento para restaurar os arquivos de calibragem.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Meu controlador parece ser um Naopak/oculus, tem uma orientação estranha ou os botões estão mapeados incorretamente

O site provavelmente não tem suporte ao controlador de movimento completo.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Meus controladores de movimento não aparecem em aplicativos e jogos do SteamVR

Primeiro, certifique-se de que as baterias do controlador sejam cobradas. Os controladores não funcionarão se as baterias estiverem inativas ou curioso

Se você puder ver seus controladores na casa Cliff, mas não em aplicativos e jogos do SteamVR, talvez o driver do modelo do controlador de movimento não esteja instalado corretamente. Para verificar se o driver do modelo do controlador de movimento está instalado corretamente:

1. Ative os dois controladores de movimento. Verifique se os controladores de movimento estão [emparelhados corretamente](controllers-in-wmr.md#pair-motion-controllers).
2. Vá para **Device Manager > Bluetooth** e procure "controlador de movimento".
3. Selecione o dispositivo e vá para **exibir > dispositivos por conexão** .
4. Vá para **configurações do sistema > dispositivos > Bluetooth & outros dispositivos > outros dispositivos** vejam se eles estão visíveis. Haverá dois dispositivos de "dispositivo HID Bluetooth" e, em cada dispositivo HID Bluetooth, devem ser dispositivos chamados "controlador de movimento" (com ícones cinzas) no mesmo nó que o controlador de movimento.
5. Clique duas vezes em cada dispositivo "controlador de movimento" e vá para a guia "driver". Confirme se a versão do driver listada corresponde a uma dessas [versões](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history).
6. Se não tiver, execute Windows Update, que irá baixar e instalar automaticamente o driver. Se você estiver em um PC que tenha políticas corporativas ou se Windows Update for, de outra forma, restrita, talvez seja necessário instalar manualmente o driver do modelo do controlador de movimento. Para fazer isso, visite [esta página](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) e procure a versão do driver correspondente à sua versão do Windows 10. As instruções de instalação estão disponíveis na página de download.

## <a name="the-controller-firmware-update-takes-significantly-longer-than-two-minutes"></a>A atualização do firmware do controlador leva muito mais tempo do que dois minutos

Marque a [seção perguntas sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). A baixa qualidade de link Bluetooth geralmente causa esses problemas.

## <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Acabei de inserir baterias novas, mas o nível de bateria virtual do controlador não indica o nível completo

O nível de bateria do controlador de movimento está ajustado para baterias AA. Algumas baterias recarregáveis de baixa voltagem podem não ser relatadas como completas, embora sejam totalmente cobradas.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Meu touchpad do controlador de movimento Samsung está fora do centro ou tem um ponto de inatividade

Isso provavelmente é um defeito de hardware e você deve voltar para o fabricante do equipamento ou revendedor para uma substituição ou troca.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Como posso restaurar os controladores para as configurações de fábrica

Restaure-o para as condições de fábrica (você precisará de novas baterias):

1. Desconecte e desligue os controladores.
2. Abra a tampa da bateria.
3. Insira suas novas baterias.
4. Pressione e segure o botão de emparelhamento (a guia na parte inferior sob as baterias).
5. Enquanto mantém o botão de emparelhamento, ligue o controlador pressionando e segurando o botão Windows por cinco segundos (Mantenha ambos os botões pressionados).
6. Solte os botões e aguarde até que o controlador ligue. Isso leva até 15 segundos e não há indicadores quando a recuperação do dispositivo está ocorrendo. Se o dispositivo ligar imediatamente na versão do botão, a sequência do botão de recuperação não será registrada e você precisará tentar novamente.
7. Se os controladores foram emparelhados com o seu PC, acesse **configurações > Bluetooth > outros dispositivos** e selecione "controlador de movimento" e "remover dispositivo" para remover associações de controlador de configurações de Bluetooth.
8. [Emparelhe os controladores](controllers-in-wmr.md#pair-motion-controllers) com o headset ou o PC novamente.
9. Depois de se conectar com o host e o headset, o dispositivo será atualizado para o firmware mais recente disponível.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>Posso emparelhar meu controlador Xbox com meu PC para que eu possa usá-lo em Headset

Você pode emparelhar um controlador Xbox do Bluetooth para usá-lo com o headset seguindo [estas instruções](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues).

Se você tiver um controlador Xbox com fio, conecte-o ao seu PC.

Alguns jogos e aplicativos usam o controlador Xbox de forma diferente do usado em realidade misturada. Para usar o controlador para um jogo ou aplicativo, selecione "usar como Gamepad" na barra de aplicativos ou, por exemplo, "usar como Gamepad". Para mudar o controlador para a realidade misturada, selecione "usar como Gamepad" novamente ou diga "usar com olhar". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Como fazer emparelhar novos controladores se o Windows Mixed Reality já estiver configurado no meu PC

Se você estiver emparelhando seus controladores ao headset, use o aplicativo complementar (o [portal de realidade mista](install-windows-mixed-reality.md#launch-mixed-reality-portal) pode ajudá-lo a encontrar um aplicativo complementar para iniciar ou fornecer uma lista de aplicativos complementares que você pode selecionar).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Como posso retornar meus controladores para o emparelhamento de fábrica

Para retornar os controladores de movimento ao emparelhamento de fábrica, ou para emparelhá-los com um headset de realidade mista do Windows com rádio Bluetooth interno, execute o aplicativo de dispositivo do headset (por exemplo, o aplicativo "Acer OJO 500" ou o aplicativo "Samsung HMD Odyssey + Setup", instalado automaticamente na primeira vez em que o headset está conectado) e siga as instruções para o emparelhamento do controlador de movimento.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>Meus controladores de movimento não estão emparelhando com meu PC

* Se os controladores não forem ativados, insira baterias novas. Se isso não corrigir, restaure o dispositivo para suas configurações de fábrica ligando o dispositivo enquanto mantém os botões de emparelhamento. Consulte as [etapas de recuperação do dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) para obter mais detalhes.
* Se os controladores ativarem e você estiver usando um adaptador Bluetooth externo, verifique se o adaptador está conectado a uma porta USB 2,0 (que geralmente é, mas não sempre, preto), longe de outros transmissores sem fio ou unidades flash USB. Se ainda não funcionar, execute o solucionador de problemas de Bluetooth em configurações > atualização & segurança > solucionar problemas > Bluetooth.
* Se você estiver usando um adaptador Qualcomm e o PC acabar de falhar, reinicie o computador.
* Tente reiniciar os controladores de movimento que não estão emparelhando, um de cada vez, e reinicie o computador.
* O cache do controlador de movimento pode estar corrompido. Para corrigir esse problema, consulte estas [etapas](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal).
* Se nenhuma dessas etapas corrigir o problema, você deverá entrar em contato com o fabricante.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Meus controladores emparelhados não aparecem no portal da realidade misturada

* Mantenha os controladores na frente do headset e reinicie-os pressionando o botão Windows por quatro segundos e, em seguida, novamente por dois segundos.
* Se os controladores forem exibidos como conectados, desemparelhe-os e percorra o [processo de emparelhamento](controllers-in-wmr.md#pair-motion-controllers) novamente.
* Se os LEDs do controlador estiverem em ciclo, ativar um quadrante de luzes por vez e desligá-los, eles estarão passando por uma atualização de firmware. Aguarde a conclusão da atualização e os controladores devem aparecer em realidade misturada.
* Se um adaptador Bluetooth externo for usado, verifique se o adaptador está conectado a uma porta USB 2,0 (que geralmente é preta), longe de outros transmissores sem fio ou dispositivos USB 3,0.
* Se o PC simplesmente falhar e um adaptador Qualcomm estiver sendo usado, uma redefinição poderá não funcionar. Para corrigir isso, desconecte a energia da parte traseira do computador (ou se estiver em um laptop, mantenha pressionado o botão de energia por 10 segundos) e reinicie o computador.
* Execute o solucionador de problemas de Bluetooth em **configurações > atualização & segurança > solucionar problemas > Bluetooth** .  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Estou tentando emparelhar meus controladores, mas eles nunca aparecem no menu "adicionar um novo dispositivo" em configurações de Bluetooth

Verifique se você já tem controladores emparelhados. Se você fizer isso, remova-os e tente novamente. Reinicie o PC se o problema persistir. Se isso falhar, consulte mais [informações sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

Observação: se outro conjunto de controladores de movimento estiver emparelhado com seu PC, você precisará desemparelhar esses controladores antes de emparelhar os novos. Se você emparelhar um conjunto de controladores de movimento com seu PC atual e os emparelhar com um segundo PC, precisará desemparelhar e emparelhar novamente com o computador atual antes de usá-los novamente.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Como saber se estou usando a tecnologia Bluetooth

Os controladores de movimento usam a mesma tecnologia Bluetooth encontrada em muitos dispositivos de consumo e foram projetados para funcionar com o recurso de Bluetooth incluído em qualquer PC recente. Seu PC deve ter rádio Bluetooth se ele passou na verificação de compatibilidade da realidade misturada. Para verificar:

* Abra "Device Manager".
* Expanda a seção Bluetooth e procure um adaptador.

![Captura de tela de um exemplo Device Manager. O adaptador é o rádio Bluetooth.](images/devicemanagerbtadapterpic.png)

Se o seu computador não tiver o Bluetooth, use o adaptador de baixa energia micro USB Bluetooth 4,0 de baixo consumo.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi fica mais lento no meu notebook quando os controladores de movimento estão ativados

Seu notebook pode compartilhar sua antena Wi-Fi com Bluetooth quando conectado a um ponto de acesso de 2,4 GHz. Faça check-in Device Manager se você puder alternar a preferência de banda para 5 GHz. Se uma rede de 5 GHz não estiver disponível e o desempenho for seriamente afetado, considere usar um dongle Bluetooth.

![As configurações de seleção de banda WiFi podem ser encontradas por meio do Gerenciador de dispositivos](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers"></a>Meu PC tem tecnologia Bluetooth, mas estou tendo problemas com meus controladores

Os controladores de movimento devem funcionar com outros teclados, mouse e controladores de jogo Bluetooth, mas a experiência variará dependendo do modelo de Keyboard, mouse ou controlador de jogo que você usar. Aqui estão algumas coisas que você pode fazer para melhorar o desempenho:

* Se o seu computador tiver o Bluetooth, mas você ainda tiver problemas com os controladores de movimento, considere substituir o rádio Bluetooth por um adaptador Bluetooth externo conectável conectado ao USB. Você só pode ter um adaptador de rádio Bluetooth ativo por vez. Se você conectar um rádio externo Além de um rádio existente, será necessário desabilitar o rádio Bluetooth existente no Device Manager (clique com o botão direito do mouse no adaptador e selecione "desabilitar dispositivo") e desemparelhar/emparelhar todos os dispositivos Bluetooth anteriores.
* Se você estiver usando um adaptador Bluetooth USB, conecte-o a uma porta USB 2,0 (as portas 2,0 geralmente são pretas e não são rotuladas "SS"), se disponíveis. A porta deve ser fisicamente separada de:
    - o conector USB do HMD
    - unidades flash
    - discos rígidos
    - receptores USB sem fio como aqueles para teclados/mouses de preferência, conecte o adaptador Bluetooth USB ao lado oposto do computador o máximo possível desses outros conectores.
* Feche a janela configurações de Bluetooth se ela estiver aberta. Deixá-lo aberto em segundo plano significa que muitas chamadas extras são feitas no protocolo Bluetooth.
* Se o seu headset estiver emparelhado com seu PC, use a pilha de drivers Bluetooth do Windows e não instale nenhuma pilha de drivers Bluetooth de terceiros. O software de terceiros pode não funcionar corretamente.
* Desabilite a configuração "mostrar notificação para se conectar usando o par Swift" em "Bluetooth & outros dispositivos" para reduzir a atividade de verificação de rádio do host.
* Se você estiver usando uma placa Bluetooth interna, certifique-se de estar usando uma antena de Bluetooth externa ou pode enfrentar problemas de rastreamento. Se isso não funcionar, use um dongle Bluetooth externo (USB) depois de desabilitar o Bluetooth interno.
* O dispositivo deve aparecer na categoria "mouse, teclado & caneta" nas configurações de Bluetooth. Se estiver em "outros dispositivos", desemparelhe e emparelhe o dispositivo.
* Remova, desemparelhe e desligue os fones de ouvido e os alto-falantes Bluetooth. Eles não têm suporte com a realidade mista do Windows. Use a tomada de fone de ouvido ou os palestrantes internos em seu headset de realidade misturada para obter a melhor experiência de áudio.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Meu segundo controlador leva muito tempo para se reconectar

Alguns rádios da Intel mais antigos terão esse problema se os controladores de movimento estiverem ligados ao mesmo tempo. Evite ligar os controladores ao mesmo tempo.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Meu rádio do Qualcomm Bluetooth não pode emparelhar controladores após uma falha de PC

Os drivers de rádio do Qualcomm (QCA) Bluetooth anteriores ao 10.0.0.448 podem terminar em estado inadequado após uma falha do Windows. Desligue o PC completamente para solucionar esse problema.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Estou tendo um controle insatisfatório do controlador com o Marvell Radio

Vá para **Device Manager > bluetooth > adaptador de rádio Bluetooth Marvell AVASTAR > propriedades > driver** e verifique se você está usando o driver 15.68.9210.47 ou posterior.
