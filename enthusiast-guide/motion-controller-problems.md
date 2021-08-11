---
title: Perguntas frequentes do controlador de movimento
description: os controladores Windows Mixed Reality solução de problemas que vão além da nossa documentação padrão de suporte ao consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, solução de problemas, erros, ajuda, suporte, controladores de movimento
appliesto:
- Windows 10
ms.openlocfilehash: e477ed07e20fb06e270c9a6e13e20defecfc6328896983ed12c4b79ea2197e44
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115219732"
---
# <a name="motion-controller-faqs"></a>Perguntas frequentes do controlador de movimento

## <a name="what-do-the-vibrations-and-lights-mean"></a>O que significam as vibraçãos e luzes

O LED Constellation Ring e haptics indicam o estado do controlador de movimento.

| Estado    | Comportamento associado ao estado | Como chegar/sair do estado |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Ligue**               | Os LEDs acendem e o controlador vibra uma vez. | pressione e mantenha o botão Windows no controlador por dois segundos para ativar o controlador.  |
| **Desligar**              |  Os LEDs desligam e o controlador vibra duas vezes. | pressione e mantenha o botão Windows no controlador por quatro segundos para desligar o controlador.   |
| **Dormindo**               |  Os LEDs desligam e piscam a cada três segundos durante o estado de suspensão. | O controlador entra no estado de suspensão automaticamente quando não está em movimento por 30 segundos. O controlador é ativado quando detecta o movimento, exceto se o dispositivo não estiver emparelhado com o PC host. Pressione o botão para ativá-lo nesse caso. |
| **Emparelhamento**                |  Os LEDs pulsam lentamente enquanto estão no modo de emparelhamento e entram sólidos ao sair do modo de emparelhamento. O controlador vibra uma vez se o emparelhamento tiver sido bem-sucedido ou três vezes se o emparelhamento não for bem-sucedido e o tempo limite for atingido. | Pressione e segure o botão de emparelhamento dentro do caso da bateria por três segundos.     |
| **O controlador conecta/desconecta do PC** |  O controlador vibra uma vez na conexão do PC ou na desconexão. | Ocorre quando o controlador se conecta com êxito ao PC depois que você o liga, ou se o controlador se desconecta do PC durante o uso.|
| **Nível de bateria fraca**      | Haptics são desabilitados quando a bateria está baixa (não há indicação de LED). O ícone de indicador de bateria no identificador do controlador em Headset mostrará 1/4 cheio quando a bateria estiver baixa. | Substitua suas baterias. | 
| **Nível de bateria crítica** |  O controlador vibra três vezes quando você o ativa e, em seguida, desliga automaticamente. O ícone de indicador de bateria ficará vermelho. | Substitua as baterias. Se o problema persistir, [restaure o dispositivo para suas configurações de fábrica](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings)|

## <a name="my-motion-controllers-arent-working-properly"></a>Meus controladores de movimento não estão funcionando corretamente

Se os seus [controladores de movimento](controllers-in-wmr.md) não estiverem funcionando, conectando ou mostrando uma imagem dos controladores quando você estiver desgastando o headset:

1. Verifique se os controladores estão ativados. para ativá-los, pressione e mantenha pressionado o botão de Windows por dois segundos.
2. Certifique-se de que os controladores sejam totalmente cobrados e substitua as baterias, se não estiverem.
3. Desligue os controladores e ligue-os novamente enquanto os mantém na frente de você. pressione e mantenha o botão Windows por quatro segundos para desligar um controlador. Pressione e mantenha-o pressionado novamente por dois segundos para ativá-lo.
4. Verifique se os controladores de movimento estão [emparelhados corretamente](controllers-in-wmr.md#pair-motion-controllers).
5. Verifique os LEDs dos controladores de movimento: controladores acesos brilhantes estão emparelhados e conectados, Dimly os controladores acesos não estão conectados.
6. Acesse **iniciar > portal de realidade misturada** no seu PC e selecione "menu". Você deve ver seus controladores de movimento listados, juntamente com uma mensagem de status:
    * Pronto – os controladores estão todos definidos.
    * Rastreamento perdido – o portal de realidade misturada não pode localizar seus controladores. mantenha-os na frente do headset e reinicie-os pressionando o botão Windows por quatro segundos e, em seguida, novamente por dois segundos.
    * Bateria fraca – Substitua as baterias do controlador.
7. se você estiver usando um adaptador de Bluetooth usb externo, verifique se ele está conectado a uma porta usb 2,0 (geralmente, mas nem sempre preto). Ele também deve ser conectado o máximo possível de qualquer outro transmissor sem fio ou unidades flash USB, incluindo o conector USB para o headset. 
8. vá para **Gerenciador de Dispositivos > Bluetooth** e procure um adaptador para verificar se há apenas um rádio Bluetooth no PC. Se você estiver usando a configuração de computador desktop com rádio interno, verifique se uma antena externa está conectada. Se não houver nenhuma antena externa conectada, isso poderá causar problemas de controle. ou use um dongle de Bluetooth externo (USB), desabilite o recurso de Bluetooth interno e tente emparelhar e se conectar novamente.
9. se a janela configurações de Bluetooth estiver aberta em segundo plano, muitas chamadas extras serão feitas no protocolo Bluetooth. Feche-o.
10. Verifique o nível da bateria virtual no controlador de movimento girando os controladores em realidade misturada para ver o ícone de bateria. Aguarde cerca de 15 segundos antes de ler o nível, pois o nível relatado é maior do que o nível real imediatamente após conectar um controlador. Substitua as baterias se o ícone estiver vermelho.
11. remova Bluetooth fones de ouvido e alto-falantes em **Configurações dispositivos > > Bluetooth & outros dispositivos** e desative os dispositivos. Use a tomada de fone de ouvido ou os palestrantes internos em seu headset de realidade misturada para obter a melhor experiência de áudio.
12. remova outros dispositivos Bluetooth que possam estar emparelhados com seu PC, como fones de ouvido ou gamepads. vá para **Configurações dispositivos > > Bluetooth & outros dispositivos**, selecione os dispositivos e, em seguida, "remover dispositivo".
13. Desconecte o cabo USB em seu headset e conecte-o novamente ao computador para reiniciar Windows Mixed Reality.
14. As luzes do controlador piscam quando estão passando por uma atualização de firmware. Aguarde a conclusão da atualização e os controladores devem aparecer em realidade misturada.
15. Verifique se o PC está conectado a uma rede de 5 GHz Wi-Fi. se o seu laptop estiver conectado a uma rede Wi-Fi de 2,4 GHz, ele geralmente está compartilhando a conexão Bluetooth. isso pode afetar negativamente o desempenho de Wi-Fi ou de Bluetooth, dependendo do design do produto. Altere a banda preferencial para 5 GHz nas configurações do adaptador de rede. se a sua rede não der suporte a 5 GHz, um dongle Bluetooth poderá ser usado em vez do recurso de Bluetooth interno.
16. se suas configurações de Bluetooth tiverem os controladores de movimento já emparelhados, Windows não descobrirá os novos dispositivos até que eles sejam removidos. Se eles tiverem sido adicionados usando um dongle específico, eles só poderão ser removidos com esse dongle.
17. se o seu computador tiver Bluetooth interno e você estiver tendo problemas de conexão, tente usar um adaptador de Bluetooth USB. para fazer isso, desative seu rádio Bluetooth interno no Gerenciador de Dispositivos e, em seguida, emparelhe seus outros dispositivos Bluetooth com o novo adaptador.

## <a name="my-controllers-jitter-get-stuck-or-flicker-and-disappear-in-mixed-reality"></a>Meus controladores tremulam, ficam presos ou cintilam e desaparecem em realidade misturada

* Se o seu computador estiver executando em WiFi de 2,4 GHz, mude para WiFi de 5 GHz. 
* se você estiver usando um adaptador de Bluetooth externo, verifique se ele está conectado a uma porta USB 2,0 (que geralmente é, mas não sempre, preto), longe de outros transmissores sem fio ou unidades flash USB.
* execute o Bluetooth solução de problemas no **Configurações > Update & Security > solucionar problemas**> Bluetooth.

## <a name="my-controller-is-stuck-in-an-infinite-reboot"></a>Meu controlador está preso em uma reinicialização infinita

Esse é um indicador de bateria crítica. Coloque as novas baterias no dispositivo e, se o problema persistir, [redefina o controlador para as configurações de fábrica](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).

## <a name="the-mixed-reality-portal-is-working-but-my-controllers-are-tracking-poorly-flying-away-shaking-etc"></a>O portal de realidade misturada está funcionando, mas meus controladores estão acompanhando mal (pilotando, agitando, etc.)

1. As condições de iluminação podem afetar o controle. Verifique se você não está exposto ao Oriente direto e tenha fontes de luz de ponto mínimas visíveis para seu HMD (por exemplo, cadeias de caracteres de luzes como uma árvore de Natal).
2. esses sintomas são causados por falhas na comunicação entre o controlador e o PC host e indicam uma qualidade de link de Bluetooth ruim. Consulte as [perguntas sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

## <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Os LEDs do controlador de movimento não estão acesos, mas os botões e Thumbstick ainda funcionam no portal de realidade misturada

O cache de calibragem do controlador de movimento pode estar corrompido. Para excluir o cache, execute o seguinte comando em um prompt de comando de administrador:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

essa pasta não está acessível no Windows Explorer e só pode ser modificada em um Prompt de comando de administrador. Depois de excluir a pasta, reinicie o computador e reconecte seus controladores de movimento para restaurar os arquivos de calibragem.

## <a name="my-controller-looks-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Meu controlador parece ser um Naopak/oculus, tem uma orientação estranha ou os botões estão mapeados incorretamente

O site provavelmente não tem suporte ao controlador de movimento completo.

## <a name="my-motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Meus controladores de movimento não aparecem em aplicativos e jogos do SteamVR

Primeiro, certifique-se de que as baterias do controlador sejam cobradas. Os controladores não funcionarão se as baterias estiverem inativas ou curioso

Se você puder ver seus controladores na casa Cliff, mas não em aplicativos e jogos do SteamVR, talvez o driver do modelo do controlador de movimento não esteja instalado corretamente. Para verificar se o driver do modelo do controlador de movimento está instalado corretamente:

1. Ative os dois controladores de movimento. Verifique se os controladores de movimento estão [emparelhados corretamente](controllers-in-wmr.md#pair-motion-controllers).
2. Vá para **Gerenciador de Dispositivos > dispositivos de interface humana** e procure "controlador de movimento".
3. Clique duas vezes em cada dispositivo "controlador de movimento" e vá para a guia "driver". Confirme se a versão do driver listada corresponde a uma dessas [versões](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history).
4. se a versão do driver não corresponder ou se não for possível encontrar um dispositivo chamado "controlador de movimento", execute Windows Update.  Isso baixará e instalará automaticamente o driver. se você estiver em um PC que tenha políticas corporativas ou se Windows Update for, de outra forma, restrita, talvez seja necessário instalar manualmente o driver do modelo do controlador de movimento. Para fazer isso, visite [esta página](mixed-reality-software.md#mixed-reality-motion-controller-model-driver-release-history) e procure a versão do driver correspondente ao seu hardware do controlador. As instruções de instalação estão disponíveis na página de download.

## <a name="the-controller-firmware-update-takes-longer-than-two-minutes"></a>A atualização do firmware do controlador leva mais de dois minutos

marque a [seção perguntas Bluetooths](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). a qualidade de link de Bluetooth ruim geralmente causa esses problemas.

## <a name="i-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Inseri as baterias novas, mas o nível da bateria virtual do controlador não indica o nível completo

O nível de bateria do controlador de movimento está ajustado para baterias AA. Algumas baterias recarregáveis de baixa voltagem podem não ser relatadas como completas, embora elas sejam totalmente cobradas.

## <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Meu touchpad do controlador de movimento Samsung está fora do centro ou tem um ponto de inatividade

Isso provavelmente é um defeito de hardware e você deve voltar para o fabricante do equipamento ou revendedor para uma substituição ou troca.

## <a name="how-can-i-restore-the-controllers-to-factory-settings"></a>Como posso restaurar os controladores para as configurações de fábrica

Restaure-o para as condições de fábrica (você precisará de novas baterias):

1. Desconecte e desligue os controladores.
2. Abra a tampa da bateria.
3. Insira suas novas baterias.
4. Pressione e segure o botão de emparelhamento (a guia na parte inferior sob as baterias).
5. enquanto mantém o botão de emparelhamento, ligue o controlador pressionando e segurando o botão de Windows por cinco segundos (mantenha ambos os botões pressionados).
6. Solte os botões e aguarde até que o controlador ligue. Isso leva até 15 segundos e não há indicadores quando a recuperação do dispositivo está ocorrendo. Se o dispositivo ligar imediatamente na versão do botão, a sequência do botão de recuperação não será registrada e você precisará tentar novamente.
7. se os controladores foram emparelhados com o seu PC, acesse **Configurações > Bluetooth > outros dispositivos** e selecione "controlador de movimento" e "remover dispositivo" para remover as associações de controlador das configurações de Bluetooth.
8. [Emparelhe os controladores](controllers-in-wmr.md#pair-motion-controllers) com o headset ou o PC novamente.
9. Depois de se conectar com o host e o headset, o dispositivo será atualizado para o firmware mais recente disponível.

## <a name="can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset"></a>Posso emparelhar meu controlador Xbox com meu PC para que eu possa usá-lo em Headset

você pode emparelhar um controlador Xbox Bluetooth para usá-lo com o headset seguindo [estas instruções](https://support.xbox.com/help/hardware-network/accessories/connect-and-troubleshoot-xbox-one-bluetooth-issues).

Se você tiver um controlador Xbox com fio, conecte-o ao seu PC.

Alguns jogos e aplicativos usam o controlador Xbox de forma diferente do usado em realidade misturada. Para usar o controlador para um jogo ou aplicativo, selecione "usar como Gamepad" na barra de aplicativos ou, por exemplo, "usar como Gamepad". Para mudar o controlador para a realidade misturada, selecione "usar como Gamepad" novamente ou diga "usar com olhar". 

## <a name="how-do-i-pair-new-controllers-if-windows-mixed-reality-is-already-set-up-on-my-pc"></a>Como fazer emparelhar novos controladores se Windows Mixed Reality já estiver configurado no meu computador

Se você estiver emparelhando seus controladores ao headset, use o aplicativo complementar (o [portal de realidade mista](install-windows-mixed-reality.md#launch-mixed-reality-portal) pode ajudá-lo a encontrar um aplicativo complementar para iniciar ou fornecer uma lista de aplicativos complementares que você pode selecionar).

## <a name="how-can-i-return-my-controllers-to-their-factory-pairing"></a>Como posso retornar meus controladores para o emparelhamento de fábrica

para retornar os controladores de movimento ao emparelhamento de fábrica ou para emparelhar com um Windows Mixed Reality headset com rádio interno Bluetooth, execute o aplicativo de dispositivo do headset e siga as instruções para o emparelhamento do controlador de movimento. Por exemplo, o aplicativo "Acer OJO 500" ou o aplicativo "Samsung HMD Odyssey + Setup" é instalado automaticamente na primeira vez em que o headset está conectado.

## <a name="my-motion-controllers-are-not-pairing-to-my-pc"></a>Meus controladores de movimento não estão emparelhando com meu PC

* Se os controladores não forem ativados, insira baterias novas. Se isso não corrigir, restaure o dispositivo para suas configurações de fábrica ligando o dispositivo enquanto mantém os botões de emparelhamento. Para obter mais informações, consulte as [etapas de recuperação do dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings).
* se os controladores ativarem enquanto você estiver usando um adaptador de Bluetooth externo, verifique se o adaptador está conectado a uma porta USB 2,0 (que geralmente é, mas não sempre, preto), longe de outros transmissores sem fio ou unidades flash USB. se ainda não funcionar, execute o Bluetooth solução de problemas no Configurações > Update & Security > solucionar problemas > Bluetooth.
* Se você estiver usando um adaptador Qualcomm e o PC acabar de falhar, reinicie o computador.
* Tente reiniciar os controladores de movimento que não estão emparelhando, um de cada vez, e reinicie o computador.
* O cache do controlador de movimento pode estar corrompido. Para corrigir esse problema, consulte estas [etapas](motion-controller-problems.md#motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal).
* Se as etapas corrigirem o problema, entre em contato com o fabricante.

## <a name="my-paired-controllers-dont-show-up-in-the-mixed-reality-portal"></a>Meus controladores emparelhados não aparecem no portal da realidade misturada

* mantenha os controladores na frente do headset e reinicie-os pressionando o botão Windows por quatro segundos e, em seguida, novamente por dois segundos.
* Se os controladores forem exibidos como conectados, desemparelhe-os e percorra o [processo de emparelhamento](controllers-in-wmr.md#pair-motion-controllers) novamente.
* Se os LEDs do controlador estiverem alternando um quadrante de luzes acendendo e desativando por vez, eles estarão passando por uma atualização de firmware. Aguarde a conclusão da atualização e os controladores devem aparecer em realidade misturada.
* se um adaptador de Bluetooth externo for usado, verifique se o adaptador está conectado a uma porta USB 2,0 (que é preta), longe de outros transmissores sem fio ou dispositivos USB 3,0.
* Se o PC simplesmente falhar e um adaptador Qualcomm estiver sendo usado, uma redefinição poderá não funcionar. Para corrigir isso, desconecte a energia da parte traseira do computador (ou se estiver em um laptop, mantenha pressionado o botão de energia por 10 segundos) e reinicie o computador.
* execute o Bluetooth solução de problemas no **Configurações > Update & Security > solucionar problemas**> Bluetooth.  

## <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>estou tentando emparelhar meus controladores, mas eles nunca aparecem no menu "adicionar um novo dispositivo" em configurações de Bluetooth

Verifique se você já tem controladores emparelhados. Se você fizer isso, remova-os e tente novamente. Reinicie o PC se o problema persistir. Se isso falhar, consulte mais [informações sobre Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

Observação: se outro conjunto de controladores de movimento estiver emparelhado com seu PC, você precisará desemparelhar esses controladores antes de emparelhar os novos. Se você emparelhar um conjunto de controladores de movimento com seu PC atual e os emparelhar com um segundo PC, precisará desemparelhar e emparelhar novamente com o computador atual antes de usá-los novamente.

## <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>como saber se estou usando a tecnologia de Bluetooth

os controladores de movimento usam a mesma tecnologia de Bluetooth encontrada em muitos dispositivos de consumo e foram projetados para funcionar com o recurso de Bluetooth incluído em qualquer PC recente. seu PC deve ter Bluetooth rádio se ele passou na verificação de compatibilidade da realidade misturada. Para verificar:

* Abra "Gerenciador de Dispositivos".
* expanda a seção Bluetooth e procure um adaptador.

![Captura de tela de um exemplo Gerenciador de Dispositivos. o adaptador é o Bluetooth rádio.](images/devicemanagerbtadapterpic.png)

se o seu computador não tiver Bluetooth, use o USB conectável Bluetooth o adaptador de baixa energia 4,0.

## <a name="wi-fi-slows-down-on-my-notebook-when-motion-controllers-are-turned-on"></a>Wi-Fi fica mais lento no meu notebook quando os controladores de movimento estão ativados

seu notebook pode compartilhar sua antena Wi-Fi com Bluetooth quando conectado a um ponto de acesso de 2,4 GHz. Faça check-in Gerenciador de Dispositivos se você puder alternar a preferência de banda para 5 GHz. se uma rede de 5 GHz não estiver disponível e o desempenho for seriamente afetado, considere o uso de um dongle Bluetooth.

![As configurações de seleção de banda WiFi podem ser encontradas por meio do Gerenciador de dispositivos](images/wifi5ghz.png)

## <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-controllers&quot;></a>meu PC tem Bluetooth tecnologia, mas estou tendo problemas com meus controladores

os controladores de movimento devem funcionar com outros teclados Bluetooth, mouses e controladores de jogos. A experiência irá variar dependendo do modelo de teclado, mouse ou controlador de jogo que você usar. Aqui estão algumas coisas que você pode fazer para melhorar o desempenho:

* se o computador tiver Bluetooth, mas você ainda tiver problemas com os controladores de movimento, considere substituir o rádio de Bluetooth por um adaptador de Bluetooth conectável conectado ao USB. você só pode ter um adaptador de rádio Bluetooth ativo por vez. se você conectar um rádio externo junto com um rádio existente, será necessário desabilitar o Bluetooth rádio existente no Gerenciador de Dispositivos. clique com o botão direito do mouse no adaptador e selecione &quot;desabilitar dispositivo&quot; e desemparelhar/emparelhar todos os seus dispositivos anteriores Bluetooth.
* se você estiver usando um adaptador de Bluetooth usb, conecte-o a uma porta usb 2,0 (as portas 2,0 geralmente são pretas e não são rotuladas &quot;SS"), se disponíveis. A porta deve ser fisicamente separada de:
    - o conector USB do HMD
    - unidades flash
    - discos rígidos
    - receptores usb sem fio como aqueles para teclados/mouses de preferência, conecte o adaptador USB Bluetooth ao lado oposto do computador o máximo possível desses outros conectores.
* feche a janela configurações de Bluetooth se ela estiver aberta. Deixá-lo aberto em segundo plano significa que muitas chamadas extras são feitas para o protocolo Bluetooth segurança.
* Se o headset estiver emparelhado com o computador, use a pilha de driver Windows Bluetooth e não instale nenhuma pilha de driver Bluetooth de terceiros. O software de terceiros pode não funcionar corretamente.
* Desabilite a configuração "Mostrar notificação para se conectar usando Emparelhamento Rápido" em "Bluetooth & outros dispositivos" para reduzir a atividade de verificação de rádio do host.
* Se você estiver usando um cartão Bluetooth interno, certifique-se de estar usando uma Bluetooth externa ou você poderá ter problemas de acompanhamento. Se isso não funcionar, use um dispositivo Bluetooth (USB) externo depois de desabilitar o Bluetooth.
* O dispositivo deve aparecer na categoria "Mouse, Teclado & Caneta" nas Bluetooth configurações. Se estiver em "Outros dispositivos", desempaco logo e emparelhe o dispositivo.
* Remover, desempacocar e desligar Bluetooth fones de ouvido e alto-falantes. Não há suporte para eles com Windows Mixed Reality. Use o fone de ouvido ou alto-falantes integrados em seu headset de Realidade Misturada para a melhor experiência de áudio.

## <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Meu segundo controlador leva muito tempo para se reconectar

Algumas rádios Intel mais antigas experimentam esse problema se os controladores de movimento estão ligado ao mesmo tempo. Evite a energia em controladores ao mesmo tempo.

## <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Meu rádio Qualcomm Bluetooth não pode emparelhar controladores após uma falha no computador

Os drivers de rádio QCA (Qualcomm) Bluetooth antes da 10.0.0.448 podem acabar em um estado ruim após uma Windows falha. Desligar completamente o computador para resolver esse problema.

## <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Estou enfrentando um controle de controlador ruim com a rádio Marvell

Vá para Gerenciador de Dispositivos > Bluetooth > Driver > > Bluetooth > Do adaptador de rádio **avastar** e certifique-se de que você está usando o driver 15.68.9210.47 ou posterior.
