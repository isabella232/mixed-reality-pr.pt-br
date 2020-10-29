---
title: Solução de problemas do Windows Mixed Reality
description: Solução de problemas avançada do Windows Mixed realm que vai além da nossa documentação de suporte padrão do consumidor.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte
ms.openlocfilehash: bf972c70f46ad9045005b953e28831df3ee9906e
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675497"
---
# <a name="troubleshooting-windows-mixed-reality-faqs"></a>Solução de problemas do Windows Mixed Reality (FAQs)

## <a name="understanding-common-installation-error-messages"></a>Noções básicas sobre mensagens de erro de instalação comuns

### <a name="your-pc-cant-run-windows-mixed-reality"></a>"Seu PC não pode executar a realidade mista do Windows"

Seu PC não atende aos [requisitos mínimos](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessários para executar a realidade mista do Windows. Isso pode ocorrer porque a configuração de hardware do computador não é compatível com a realidade mista do Windows ou porque você precisa [atualizar para a versão mais recente do Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq). 

Observe que a realidade mista do Windows requer um driver de placa gráfica que dá suporte a pelo menos o WDDM 2,2, portanto, verifique se você tem a atualização de driver mais recente do fabricante. Se a instalação do Windows Mixed Reality informar que a placa gráfica não atende aos requisitos e você acreditar que ela faz, verifique se o headset está conectado ao cartão correto.

### <a name="youre-nearly-therethis-pc-doesnt-meet-the-minimum-requirements-needed-to-run-windows-mixed-reality"></a>"Você está quase lá – este PC não atende aos requisitos mínimos necessários para executar a realidade mista do Windows"

Seu PC não atende aos [requisitos mínimos](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) necessários para a melhor experiência no Windows Mixed Reality. Seu computador pode ser capaz de executar um headset de imersão, mas pode não ser capaz de executar determinados aplicativos ou pode ter problemas com o desempenho.

Observe que a realidade mista do Windows requer um driver de placa gráfica que dá suporte a pelo menos o WDDM 2,2, portanto, verifique se você tem a atualização de driver mais recente do fabricante. Se a instalação do Windows Mixed Reality informar que a placa gráfica não atende aos requisitos e você acreditar que ela faz, verifique se o headset está conectado ao cartão correto.

### <a name="before-we-can-set-up-windows-mixed-reality-your-administrator-will-need-to-enable-it-for-your-organization-learn-more"></a>"Antes que possamos configurar o Windows Mixed Reality, o administrador precisará habilitá-lo para sua organização. Saiba mais "

Você provavelmente está em uma rede gerenciada corporativa e sua organização está usando o Windows Server Update Services (WSUS) ou tem outras políticas que podem bloquear o download. Entre em contato com o departamento de ti ou o administrador do sistema da sua organização para [habilitar a realidade mista do Windows](https://docs.microsoft.com/windows/application-management/manage-windows-mixed-reality#enable).

### <a name="we-couldnt-download-the-mixed-reality-software-or-hang-tight-while-we-do-some-downloading"></a>"Não foi possível baixar o software de realidade misturada" ou "parar de responder enquanto fazemos algum download"

* Às vezes, uma atualização pendente pode bloquear o download de software da realidade mista. Vá para **configurações > atualização & segurança > Windows Update** e verifique se Windows Update está ativado. Em seguida, baixe e instale todas as atualizações que estão aguardando para serem instaladas. Se você receber um erro com Windows Update ao tentar essas etapas, acesse [aqui](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors).
* Verifique se o computador está conectado à Internet e tem pelo menos 2 GB de espaço livre de armazenamento. Verifique seu status de rede em: **configurações > rede & status de > de Internet** . Se você não conseguir se conectar à Internet, acesse [aqui](https://support.microsoft.com/en-us/help/10741/windows-10-fix-network-connection-issues) para obter ajuda.  
* Reinicie o computador e tente novamente. 

Se as soluções anteriores não funcionarem, tente:
* Se sua conexão de rede Wi-Fi estiver definida como [medida](https://support.microsoft.com/en-us/help/17452/windows-metered-internet-connections-faq), altere-a para não medido. Para desativar uma conexão limitada, acesse: **configurações > rede & Internet > Status > alterar propriedades de conexão > definir como conexão limitada** e selecione "desativado".  
* Se você instalou uma atualização recentemente, isso pode causar problemas. Não recomendamos que você remova todas as atualizações instaladas, especialmente atualizações de segurança que mantêm seu computador seguro, mas às vezes remover a atualização mais recente pode ajudar a determinar a origem do problema. Para fazer isso: 
    * Vá para **configurações > atualização & segurança > exibir o histórico de atualizações instalado > desinstalar atualizações**
    * Selecione a última atualização instalada e "Desinstalar".
    * Quando solicitado "tem certeza de que deseja desinstalar esta atualização?" responder "Sim". Se você receber um erro ao tentar essas etapas, acesse [aqui](https://support.microsoft.com/en-us/help/10164/fix-windows-update-errors). 
    * Reinicie o computador e tente novamente. 
    * Se o Windows Mixed Reality for instalado corretamente, reinstale as atualizações mais recentes em **configurações > Windows Update > verificar se há atualizações** e ver se o Windows Mixed Reality continua funcionando. Se não for instalado corretamente, reinstale as atualizações mais recentes e contate o suporte do Windows. 

### <a name="something-went-wrong-and-we-couldnt-start-windows-mixed-reality"></a>"Algo deu errado e não foi possível iniciar a realidade do Windows Mixed"
* Desconecte os dois cabos do headset do PC.
* Reinicie o computador.
* Vá para **configurações > atualização & segurança > Windows Update** e verifique se Windows Update está ativado. Em seguida, baixe e instale todas as atualizações em espera.
* Reconecte o headset ao PC e tente a instalação novamente.

Se as etapas acima não funcionarem, tente desinstalar e reinstalar a realidade mista do Windows:
* Vá para **configurações > realidade misturada > desinstalar** e selecione "Desinstalar". 
* Reinicie o computador. 
* Para iniciar o processo de instalação novamente, basta conectar seu headset ao seu PC.
    

## <a name="troubleshooting-setup-questions"></a>Perguntas sobre solução de problemas de instalação 

### <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>Meu controlador Xbox não está funcionando com a realidade mista do Windows.

* Verifique se o controlador está ligado, totalmente cobrado e conectado ao PC.
* Substitua as baterias do controlador.
* Se você estiver usando um controlador Bluetooth, vá para **configurações > dispositivos > Bluetooth & outros dispositivos** em seu PC e verifique se ele está emparelhado (ele deve estar listado na página).

### <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>Não consigo direcionar a entrada (controladores, gamepad, mouse/teclado) para a realidade mista do Windows.

Quando você coloca em seu headset, a entrada deve ser automaticamente alternada para sua experiência de realidade misturada por meio do sensor de presença do headset. Uma barra azul deve aparecer na área de trabalho:

![Área de trabalho do Windows com entrada sendo direcionada para headset](images/1050px-windowsy.png)

Se a entrada não for alternada automaticamente, você precisará alternar manualmente a entrada para o headset. Você pode fazer isso digitando a **tecla Windows + Y** no teclado (e o mesmo para alternar a entrada de volta para a área de trabalho).

### <a name="when-i-plug-in-my-headset-nothing-happens-the-mixed-reality-portal-doesnt-open"></a>Quando eu conecto meu Headset, nada acontece. O portal de realidade misturada não é aberto.
O portal de realidade misturada, o aplicativo que o conduz pela instalação do Windows Mixed Reality, foi projetado para ser aberto automaticamente quando você conectar um headset compatível. Se ele não abrir, vá para iniciar e digite "portal da realidade mista" na caixa de pesquisa para abrir o aplicativo a partir daí. Se você não encontrar o portal de realidade misturada, isso pode significar que você precisa [atualizar para a versão mais recente do Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq).

### <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Como fazer escolher entre "sentado e em pé" e "todas as experiências"?

Se você escolher "colocado e posicionado", durante a configuração do headset ou posterior, você usará o headset sem um limite. Você pode sentar ou se repousar, mas, caso contrário, precisará permanecer em um lugar, pois você não terá nenhum limite para ajudá-lo a evitar obstáculos físicos. Alguns aplicativos podem ser projetados para funcionar com um limite, portanto, talvez você não possa usá-los ou talvez não tenha a mesma experiência se usá-los sem limites. Consulte "o que é um limite e por que devo criar um?" abaixo para obter mais informações.

Se você escolher "todas as experiências", configurará um limite e poderá usar aplicativos e experiências que funcionam com um limite, bem como aqueles que não exigem um. 

### <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-into-the-windows-mixed-reality-home"></a>Aprender a realidade misturada não foi executada na primeira inicialização, e eu fui direto na página inicial do Windows Mixed Reality.

Você pode executar novamente a experiência de aprendizado seguindo as [etapas de nova execução](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience). 


## <a name="boundary-setup-and-other-questions"></a>Configuração de limite e outras perguntas

### <a name="whats-a-boundary-and-why-should-i-create-one"></a>O que é um limite e por que devo criar um?

Um limite define a área na qual você pode mover-se enquanto estiver aproveitando o headset de imersão de realidade mista do Windows. Como não é possível ver seus arredores enquanto você está usando o headset, é importante criar um limite para ajudá-lo a evitar obstáculos. O limite é semelhante a um esboço branco dentro da realidade misturada e aparece quando você chega perto dele. Quando você vê isso, reduza os movimentos e evite cruzar o limite ou estendê-los para além dele.

A área dentro do limite deve ser gratuita de mobília, acessórios de luz com baixa interrupções, ventiladores de teto, etc., para que você não se aprofunde nem vá para nada. [Saiba mais sobre integridade e segurança no Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

### <a name="how-do-i-create-a-boundary"></a>Como fazer criar um limite?

Quando você configura o headset pela primeira vez, o aplicativo de instalação (portal de realidade mista) o guiará pelas etapas para criar um limite. Mas você pode criar um a qualquer momento. Para fazer isso:
1. Selecione **iniciar > portal de realidade misturada** na sua área de trabalho. 
2. Abra o "menu".
3. Selecione "executar instalação" para criar um novo limite.

Se outra pessoa usar o headset, verifique se ele entendeu o limite e como usá-lo. Se você mover o headset para um novo local, precisará configurar um novo limite que funcione para esse espaço.

### <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Recebo uma mensagem de erro quando tento criar um limite.

* Não fique muito perto de uma parede ou de outra obstrução ao criar um limite.
* Certifique-se de manter o headset na altura de estou e rosto o computador enquanto rastreia o limite.
* Verifique se o sensor não está bloqueado e se há luz suficiente.
* O espaço que você está rastreando deve ser maior do que três metros quadrados.
* O espaço não deve ser muito grande ou muito complicado. Fique à medida de uma forma geométrica simples sem muita variação e folheia.
* Não entre em seu próprio caminho enquanto estiver rastreando.
* Se você ficar preso em um canto, comece novamente.

### <a name="during-start-up-of-mixed-reality-im-stuck-at-the-step-turn-your-head-side-to-side-and-then-at-the-floor"></a>Durante a inicialização da realidade misturada, estou preso na etapa "mude seu lado para o lado e, em seguida, no andar".

Esta etapa permite que o headset reconheça seu espaço e restaure qualquer piso e limite virtuais existentes. Quando você coloca em seu headset, esse processo de verificação pode levar até 10 segundos. Após a conclusão, você estará na casa da realidade misturada ou será solicitado a configurar seu limite novamente.

Se o processo de verificação demorar mais de 10 segundos, pode haver um problema com o sensor de proximidade no headset:
1. Verifique se o adesivo foi removido do sensor de proximidade. O sensor de proximidade está localizado dentro do headset, aproximadamente onde o centro de seu nervosismo seria.
2. Verifique se o sensor de proximidade está alternando a entrada para o headset: com o dedo, cubra e descubra o sensor de proximidade algumas vezes para verificar se a entrada está mudando para o headset. Você deve ver a faixa de **tecla do Windows + Y** na parte superior do seu computador. Você pode alternar manualmente a entrada para o headset a qualquer momento digitando a **tecla Windows + Y** no teclado.

### <a name="i-see-a-message-that-says-my-boundary-cant-be-found-what-should-i-do"></a>Vejo uma mensagem que diz que o meu limite não foi encontrado. O que devo fazer?

A realidade mista do Windows pode ter problemas para identificar o limite existente. Você pode criar um novo limite ou pode usar seu dispositivo no modo "encaixado e posicionado". 

### <a name="i-see-a-message-that-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Vejo uma mensagem que diz "controle perdido" ou "não temos um limite para este espaço".

Você deve criar um novo limite. Para fazer isso:
* Selecione **iniciar > portal de realidade misturada** .
* Selecione "executar instalação".

### <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>O limite é sempre visível. Como posso fazê-lo desaparecer?

O limite aparece quando você está perto dele. Se seu limite incluir seções que tenham uma forma estreita ou irregular, você poderá acabar ficando perto dela e fazendo com que ela apareça, com mais frequência do que você gostaria. Para corrigir isso, tente criar o limite novamente usando uma forma maior e mais regular. Para fazer isso:
* Selecione **iniciar > portal de realidade misturada** .
* Selecione "executar instalação".

### <a name="how-can-i-turn-off-the-boundary-temporarily"></a>Como posso desativar o limite temporariamente?

* Selecione **iniciar > portal de realidade misturada** .
* Abra o "menu". 
* Ativar "limite" para "desativado". Lembre-se de permanecer em um único lugar enquanto o limite está desativado.


## <a name="problems-in-windows-mixed-reality-home"></a>Problemas na página inicial do Windows Mixed Reality

### <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>Meus controladores não estão sendo exibidos na minha página inicial do Windows Mixed Reality.

Verifique se os controladores têm baterias completas e se estão emparelhados corretamente usando o Bluetooth. Tente ligar os controladores e desligar usando o botão Windows. Se você ainda não consegue ver seus controladores, tente em emparelhar e reemparelhar cada controlador no menu configurações em **dispositivos > Bluetooth** .

### <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height-or-it-is-slanted"></a>O andar da minha página inicial do Windows Mixed Reality não parece estar na altura correta ou é inclinado.

Selecione **iniciar > o ajuste de sala** que será iniciado quando você colocar o aplicativo no mundo, para fazer alterações ao usar o headset. Neste aplicativo, você será direcionado para usar o Touch Pad (controlador de movimento) ou o gamepad (painel de direção) para ajustar a altura do piso. Quando o piso estiver correto, use o botão Windows para sair de volta para sua página inicial.

### <a name="my-headset-has-stopped-tracking"></a>Meu Headset parou o acompanhamento.

Verifique se as luzes estão acesas e se não há nada obstruindo as câmeras de rastreamento internas na frente do headset. Se o rastreamento for perdido, pode levar alguns segundos para retomar. Se o rastreamento não for retomado, tente reiniciar o portal do Windows Mixed Reality. Consulte [acompanhamento de solução de problemas](tracking.md) para obter mais detalhes.

### <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop-screen"></a>Não consigo mostrar uma visualização do que estou vendo em meu Headset na tela da área de trabalho.

O portal de realidade misturada tem um botão de **reprodução** na parte inferior da tela que permite mostrar uma visualização do que você está vendo no headset na tela de sua área de trabalho. Mas, por motivos de desempenho, esse recurso só está disponível em PCs em execução no Windows Mixed Reality ultra (90Hz).

## <a name="headset-connectivity-issues"></a>Problemas de conectividade do headset

### <a name="my-computer-does-not-have-an-hdmi-port"></a>Meu computador não tem uma porta HDMI.
Se o seu computador não tiver uma porta HDMI, mas tiver uma porta DisplayPort (DP), Mini DisplayPort (miniDP) ou USB Type-C (USB-C) para gerar vídeo de saída, talvez seja necessário usar um [adaptador com suporte](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

### <a name="can-i-use-usb-or-hdmi-extension-cables-with-windows-mixed-reality-headsets"></a>Posso usar cabos de extensão USB ou HDMI com headsets de realidade mista do Windows?
Os headsets de realidade mista do Windows não dão suporte oficialmente ao uso de cabos de extensão de USB ou HDMI. O uso desses cabos pode afetar significativamente a sua experiência de realidade misturada devido a variações na integridade do sinal resultante e na potência do barramento entre o controlador USB do PC e o headset da realidade misturada. Se a tela do fone de ouvido mostrar resumidamente um ecrã azul e, em seguida, ativar as reinicializações do portal da realidade em preto e misturada ou desenumerar completamente durante o uso ou se o áudio do headset for retirado ou ficar com problemas, ou se os movimentos do headset entre preto e a exibição correta, tente usar o headset sem cabos de extensão.

### <a name="i-am-getting-a-check-your-display-cable-error"></a>Estou recebendo um erro "verificar o cabo de vídeo".

* Se você estiver usando qualquer adaptador para conectar seu headset ao seu PC, verifique se eles dão suporte à realidade mista do Windows. Além disso, tente conectar o adaptador ao PC antes de conectar o HMD ao adaptador.
* Se o seu PC tiver gráficos integrados e discretos, verifique se você está usando a porta HDMI em sua placa gráfica ativa. Em alguns casos, isso pode significar que você precisará conectar a exibição do seu PC a uma porta não HDMI.
* Se o seu PC tiver gráficos integrados e discretos, e os gráficos integrados forem mais antigos e não oferecerem suporte à realidade mista do Windows, tente desabilitar a GPU integrada.
* Conecte um monitor de PC à porta HDMI do seu PC. Verifique se os drivers gráficos estão atualizados. Baixe e instale os de AMD, Nvidia ou Intel diretamente, pois eles provavelmente serão mais recentes do que o que foi publicado para Windows Update.
* Certifique-se de que você conectou o cabo HDMI do headset em uma porta de **saída de HDMI** no seu PC, não em uma porta HDMI.
* O Windows pode não conseguir detectar a conexão do cabo de vídeo. Abra o Device Manager e veja se o headset está listado em "monitores". Caso contrário, selecione **ação > verificar se há alterações de hardware** . 

### <a name="i-see-a-message-that-says-put-on-your-headset-even-though-i-have-my-headset-on"></a>Vejo uma mensagem que diz "Put on the headset", embora eu tenha meu headset ligado.

Quando você coloca em seu headset, a realidade mista do Windows pode precisar de alguns segundos para recarregar seu espaço. Se essa mensagem não desaparecer, verifique se o adesivo de proteção foi removido do sensor de proximidade, que está dentro do fone de ouvido entre as lentes. Se isso não resolver o problema, entre em contato com o fabricante do headset.

### <a name="a-message-says-connect-your-headset-even-though-ive-plugged-in-my-headset"></a>Uma mensagem diz "conectar seu headset" mesmo que eu tenha me conectado ao meu headset.

1. Verifique se os cabos USB e HDMI do headset estão conectados às portas corretas no seu PC. Aqui está como identificar as portas corretas:
    * As portas USB 3,0 têm um logotipo especial com uma marca "SS" (indicando "SuperSpeed"). A parte interna da porta é normalmente azul, enquanto as portas USB 2,0 mais antigas geralmente são pretas ou brancas no interior.
    * Se o seu computador tiver duas portas HDMI, use aquela que se conecta à placa gráfica, não a placa-mãe do computador. Nem sempre é óbvio qual é o que, embora as portas discretas geralmente estejam localizadas em um slot de expansão no computador. Se você tentar uma porta e ela não funcionar, tente a outra.
2. Desconecte e conecte os cabos USB e HDMI do headset para garantir que eles estejam conectados com segurança. Ao conectar-se ao cabo USB, tente não pausar durante a inserção do cabo USB.
3. Abra Device Manager e confirme se o headset está listado em "dispositivos de realidade misturada". Clique duas vezes em seu headset em "dispositivos de realidade misturada" e confirme se o status do dispositivo indica "este dispositivo está funcionando corretamente". Pontos de exclamação amarelos em dispositivos listados em Device Manager indicam erros relatados pelos dispositivos conectados ao seu PC.
    * Se "sensores do Hololens" estiver listado com um ponto de exclamação amarelo em Device Manager, clique duas vezes no dispositivo. Se você vir um **"código 10: os drivers para este dispositivo não estão instalados. Não há drivers compatíveis para este dispositivo "** , siga as [instruções](headset-connectivity.md#the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset) para instalar manualmente o driver headset.
    * Se você usar vários headsets de realidade misturada em seu PC e tiver instalado manualmente o driver de headset da realidade misturada antes, em algumas circunstâncias a atualização manual do driver só poderá ser aplicada ao headset conectado no momento e não a outros headsets. Nesse caso, você verá **"código 31: este dispositivo não está funcionando corretamente porque o Windows não pode carregar os drivers necessários para este dispositivo. (Código 31). A mensagem ALPC solicitada não está mais disponível "** em Device Manager. Em Device Manager, clique com o botão direito do mouse em seu headset em "dispositivos de realidade misturada" e selecione "desinstalar dispositivo". Selecione "OK" para confirmar e, em seguida, desconectar e reconectar o headset.
4. Se você estiver vendo a enumeração parcial do headset (uma série de dispositivos USB enumerar, mas nada em "a realidade misturada headsets" em Device Manager), experimente um hub USB 3,0 com alimentação externa.
5. Acesse o site do fabricante do headset e atualize os drivers e o firmware do headset.
6. Conecte seu headset a outro computador e abra Device Manager. Mesmo que esse PC não seja totalmente compatível com a realidade mista do Windows, você pode verificar se o fone de ouvido é enumerado. Se o headset não enumerar em vários PCs, ele poderá ter um problema de hardware.

**Observação para usuários do Surface:** As versões anteriores dos softwares de atualização de firmware de Hub USB do Surface Dock e do livro de superfície são incompatíveis com headsets de realidade misturada. Se você receber uma mensagem "conectar seu headset" em um PC de superfície, verifique se algum dispositivo está relatando um **erro "código 10: o dispositivo não pode iniciar"** em Device Manager. Nesse caso, [remova o driver conflitante](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Você só precisa fazer isso uma vez.

**Observação para usuários do Windows 10 N:** Se o seu computador estiver executando o Windows 10 N, você verá um **erro "código 28: a classe de instalação não está presente ou inválida"** em Device Manager depois de conectar seu headset de realidade misturada. N-edições do Windows 10 não são suportadas pela realidade mista do Windows. Siga estas [instruções](troubleshooting-windows-mixed-reality.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) para obter mais informações.

### <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Uma mensagem diz "verificar o cabo USB" ou "velocidade de USB insuficiente".

* Verifique se você está usando uma porta USB 3,0 com suporte em seu PC:
    * Certifique-se de que o cabo USB do headset esteja conectado.
    * Execute o aplicativo de [verificação do PC do Windows Mixed Reality](https://aka.ms/pccheckapp) para verificar se o controlador USB 3,0 do computador tem suporte.
    * Experimente cada uma das outras portas USB 3,0 em seu PC. Alguns PCs têm mais de um controlador USB 3,0.
    * Desconecte temporariamente todos os dispositivos USB conectados ao seu PC e conecte-se somente ao headset.
    * Em computadores personalizados, embora uma porta possa ser marcada como uma porta USB 3,0, ela pode estar conectada a um controlador USB 2,0. Com o fone de ouvido conectado, abra Device Manager, localize e clique em qualquer um dos dispositivos enumerados do headset e, em seguida, vá para **exibir > dispositivos por conexão** .
* Experimente o headset em outro PC. Se esse outro PC não for totalmente compatível com a realidade mista do Windows, faça check-in Device Manager para ver se você vê a mensagem "velocidade de USB insuficiente". Se o headset não enumerar corretamente em vários PCs, o headset poderá estar com defeito.

### <a name="the-mixed-reality-portal-did-not-launch-automatically-after-i-plugged-in-my-headset"></a>O portal de realidade misturada não foi iniciado automaticamente depois que eu conectei meu headset.

O headset pode não ter sido detectado corretamente devido a um problema subjacente. Tente iniciar o portal de realidade misturada manualmente e procure as mensagens de erro que aparecem. 

### <a name="my-headset-stopped-working-after-putting-my-pc-to-sleep-in-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Meu Headset parou de funcionar depois de colocar meu PC em suspensão, no modo de hibernação, ou ao reiniciar meu PC com meu Headset anexado.

1. Abra Device Manager e confirme se o headset está listado em "dispositivos de realidade misturada".
2. Clique duas vezes em seu headset em "dispositivos de realidade misturada" e confirme se o status do dispositivo indica "este dispositivo está funcionando corretamente".
3. Se você vir um erro de "código 43" indicando que o dispositivo parou de funcionar ou se você não vir o headset listado em "dispositivos de realidade misturada", desconecte e reconecte o cabo USB do headset. A Microsoft está investigando um problema potencial de interoperabilidade de software/driver que pode resultar nesse erro. Esse problema afeta um pequeno número de computadores e deve ser resolvido em uma atualização futura para o driver de headset de realidade misturada.

### <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Meu Headset faz com que meu computador gere uma verificação de bug (tela azul) quando coloco meu computador em suspensão ou quando ele está no modo de hibernação.

A Microsoft está investigando um problema potencial de interoperabilidade de software/driver que pode resultar em um pequeno número de PCs potencialmente gerando uma verificação de bug "9F" (tela azul) quando o PC é colocado em suspensão ou em modo de hibernação com fone de ouvido anexado. Esse problema deve ser resolvido em uma atualização futura para o driver de headset de realidade misturada.

### <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>O driver Headset não foi instalado automaticamente quando eu conectei o headset.

Em novos computadores ou PCs com uma cópia recém-instalada do Windows 10, o driver de headset pode ser enfileirado por trás de outras atualizações do Windows e pode não ser instalado imediatamente. Se você tiver uma edição "N" do Windows, será necessário alternar para uma edição regular do Windows 10 para usar a realidade mista do Windows. Para instalá-lo manualmente:

1. Acesse **iniciar > Device Manager** e procure "outros dispositivos" em um dispositivo "sensores do hololens" com um ponto de exclamação amarelo: ![ exibição de sensores Device Manager HoloLens](images/hololenssensors.png)
2. Clique com o botão direito do mouse no dispositivo e selecione Propriedades. Se as propriedades do dispositivo ler **os drivers para este dispositivo não estiverem instaladas (código 28)** , feche a janela e continue. Se houver outra mensagem, siga as etapas de solução de problemas no restante desta página.
![Código 28 de sensores do HoloLens no Device Manager](images/code28.png)
3. Clique com o botão direito do mouse no dispositivo novamente e selecione "atualizar drivers..." e, em seguida, "Pesquisar automaticamente software de driver atualizado" após as atualizações do dispositivo, você deve ver o fone de ouvido listado em "dispositivos de realidade misturada" no Device Manager: o ![ dispositivo de realidade mista aparece em Device Manager](images/mixedrealitydevices.png)

Se a instalação manual não funcionar ou se você não encontrar o driver em outros dispositivos, provavelmente precisará desinstalar o driver existente e reinstalá-lo. Para fazer isso:
1. Acesse **iniciar > Device Manager** e procure "dispositivos de realidade misturada" para o headset. O status do dispositivo deve indicar que "o dispositivo está funcionando corretamente".
2. Clique com o botão direito do mouse no dispositivo e selecione "desinstalar dispositivo".
3. No novo pop-up que aparece, marque a caixa de seleção "excluir o software de driver para este dispositivo" e, em seguida, selecione "Desinstalar".
4. Quando isso for concluído, desconecte o headset do seu PC e conecte-o novamente. Windows Update agora vai baixar e instalar um novo driver.

### <a name="troubleshooting-flowchart"></a>Solução de problemas de fluxograma

![Conecte seu headset/Verifique seu cabo USB](images/hmd-connectivity2.jpg)


## <a name="mixed-reality-headset-display-problems"></a>Problemas de exibição de headset de realidade misturada ##

### <a name="my-headset-displays-are-black"></a>Minhas telas de headset são pretas.

* Verifique o desempenho e a estabilidade do seu PC:
    * Use o Gerenciador de tarefas para ver se algum processo está maximizandondo a CPU, a GPU e/ou as unidades de disco do seu PC.
    * Examine os aplicativos e os logs de eventos do sistema no Windows (usando Visualizador de Eventos) para ver se você tem um aplicativo com frequência que está falhando e gerando relatórios de Relatório de Erros do Windows (WER).
    * Verifique Windows Update para certificar-se de que sua versão do Windows está atualizada. Talvez seja necessário selecionar "verificar atualizações" várias vezes.
* Verificar a estabilidade do aplicativo e do jogo:
    * Verifique se o seu PC atende aos requisitos mínimos do sistema para executar qualquer aplicativo/jogo que não esteja executando corretamente.    
    * Verifique se a versão do driver de GPU é recente e verifique se há novos problemas de desempenho e compatibilidade e regressões sobre novos drivers.
    * Se você estiver usando aplicativos e jogos do SteamVR, verifique se o SteamVR e o Windows Mixed Reality for SteamVR Components estão atualizados.
* Verifique a compatibilidade do adaptador HDMI:
    * Verifique se o cabo HDMI está conectado a todo o caminho.
    * Se você estiver usando um adaptador HDMI (por exemplo, um Mini DisplayPort para adaptador HDMI), verifique se ele é compatível com a realidade mista do Windows. O adaptador deve oferecer suporte a HDMI 2,0 e há muitos adaptadores mais antigos que dão suporte apenas a 1080p. Consulte [adaptadores recomendados para a realidade mista do Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
    * A ordem de plugue pode ser importante. Conecte o adaptador HDMI ao seu computador antes de conectar o headset ao adaptador, especialmente se você estiver usando um USB-C para adaptador HDMI. 
    * Tente remover os cabos de extensão se você os estiver usando.
* Verifique a placa gráfica e a compatibilidade do driver:
    * Experimente a porta HDMI do seu PC com um monitor de PC. Alguns PCs podem ter mais de uma porta HDMI, e nem todas podem estar ativas.
    * Se o seu PC tiver uma iGPU (unidade de processamento gráfico) integrada e uma dGPU (unidade de processamento gráfico discreto), verifique se você está conectado à porta HDMI de dGPU.<br> ![Portas HDMI](images/HP_HDMI_Ports_s.png)
    * Verifique a versão do driver de GPU. Verifique se ele é recente, mas também preste atenção a quaisquer novos problemas de desempenho e compatibilidade e regressões em novos drivers.
    * Se você estiver usando realidade mista em um laptop e tiver instalado um driver de gráficos mais recente no site do fabricante da placa de gráficos, tente fazer o downgrade para o driver de placa gráfica mais recente fornecido no site do fabricante do seu PC ou em Windows Update.
    * Se você tiver vários monitores de PC conectados ao seu PC, tente desconectar temporariamente todos, exceto um monitor de PC.
    * Se você tiver definido uma taxa de atualização personalizada para o monitor do seu PC, tente reverter temporariamente para uma taxa de atualização padrão, como 60Hz.
    * Se você alterou recentemente a placa gráfica sem reinstalar o Windows, verifique se o monitor Headset ainda tem o driver correto instalado. Com o fone de ouvido conectado, confirme que "a realidade mista" está listado no nó monitores em Device Manager.
    * Se o seu PC tiver uma placa gráfica Nvidia, verifique se o software de visão 3D da NVIDIA está desabilitado.
    * Em algumas placas gráficas (especialmente placas gráficas mais antigas), a porta HDMI pode não oferecer suporte a HDMI 2,0 ou pode não ser totalmente compatível com a realidade mista do Windows. Experimente a porta DisplayPort da placa gráfica usando um [adaptador de displayport 1,2 ativo para HDMI 2,0](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs)
    * Os PCs HP Omen com o número de produto HP 1RJ99EA # ABU têm portas HDMI incompatíveis com a realidade mista do Windows. Para pesquisar isso, abra o "Assistente de suporte HP" e o número do produto será listado na parte inferior do aplicativo.
    * Se o seu PC tiver uma placa gráfica AMD série R9 e você estiver usando um headset de realidade mista Samsung, você precisará atualizar o firmware do headset para a versão 1.0.8 ou mais recente para usar a porta HDMI da placa gráfica com o headset.
    * Se você estiver usando um livro de superfície 2, verifique se está usando a [superfície USB-C para o adaptador HDMI](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
* Verifique se há um problema de hardware de headset de realidade misturada:
    * Para confirmar ou eliminar problemas de hardware com o headset de realidade misturada, tente conectar o headset de realidade misturada a outro PC. 
    * Verifique a compatibilidade do PC e os problemas de instalação primeiro, pois os sintomas são muito semelhantes.
* Verifique se o cabo USB está conectado a uma porta USB 3,0 ou mais rápida. As portas USB 3,0 têm SS (super velocidade) gravadas ao lado delas. Eles são frequentemente (mas nem sempre) coloridos em azul.        

Se for útil, consulte o gráfico de fluxo de solução de problemas de tela preta do headset abaixo.

![Tela preta/não consegue ver nada](images/hmd-connectivity.jpg)

### <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Minha exibição do headset ocasionalmente fica preta após algum uso.

* Tente desabilitar qualquer recurso de suspensão ou de economia de USB que seu computador possa ter. Por exemplo, [suspensão seletiva de USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend) nas opções de energia do Windows, a configuração "permitir que o computador desligue este dispositivo para economizar energia" em Device Manager e quaisquer configurações de economia de energia USB no firmware do seu PC.
* Desconecte temporariamente quaisquer outros dispositivos USB e periféricos conectados ao seu PC.
* Verifique a versão do driver de GPU. Verifique se ele é recente, mas também preste atenção a quaisquer novos problemas de desempenho e compatibilidade e regressões em novos drivers.

### <a name="one-of-the-displays-on-my-headset-is-black"></a>Um dos monitores no meu Headset é preto.

* Se você estiver usando um adaptador HDMI, verifique se ele oferece suporte a HDMI 2,0.
* Remova todos os cabos de extensão de USB e HDMI que você possa estar usando.
* Verifique se o driver de gráficos está atualizado.
* Experimente o headset de realidade misturada em outro PC.

### <a name="my-headset-displays-turn-blue-for-a-moment-and-then-mixed-reality-portal-reinitializes"></a>Meu Headset exibe azul por um momento e, em seguida, o portal da realidade misturada é reinicializado.

Isso normalmente indica um problema de confiabilidade ocasional do controlador USB em seu PC:
* Tente outra porta USB. Seu computador pode ter vários controladores USB 3,0.
* Remova todos os cabos de extensão (se aplicável).
* Tente desconectar todos os outros dispositivos USB do seu PC.
* Tente conectar um hub USB 3,0 com energia externa ao seu PC e conecte seu headset ao Hub.
* Se você estiver usando um PC desktop, considere comprar uma placa USB 3,0 PCIe para adicionar outro controlador USB ao seu PC.

### <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Meu Headset faz com que meu PC trave ou mostre uma tela preta durante a inicialização.

Em alguns PCs, deixar o headset conectado antes de ligar ou durante a reinicialização do computador pode interferir no processo de inicialização. Seu PC pode selecionar o fone de ouvido exibido como o "monitor principal" para mostrar o progresso da inicialização do computador ou pode ser impedido de iniciar corretamente, podendo "travar" e/ou produzir um código de erro de bipe. O comportamento depende muito da marca e do modelo do PC e/ou da marca e do modelo da placa gráfica. Para corrigir isso:
* Conecte seu headset a uma porta diferente na placa gráfica (talvez seja necessário usar um adaptador para usar as outras portas).
* Verifique se o firmware BIOS/UEFI do computador está atualizado (mas Atualize apenas o firmware BIOS/UEFI do seu PC se você estiver familiarizado com isso).

### <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Meu PC ou headset exibe cintilação, flash ou permanece preto ao usar um PC de superfície.

* Verifique se você está usando um adaptador HDMI que dá suporte a HDMI 2,0. Muitos adaptadores HDMI mais antigos dão suporte apenas à resolução de 1080p, o que é insuficiente para headsets de realidade misturada.
* Verifique se o driver de gráficos está atualizado. Além de verificar Windows Update, talvez você queira verificar o site do fabricante do PC para obter um driver de gráficos atualizado.
* Alguns dispositivos de superfície são incompatíveis com a realidade mista do Windows. Saiba mais sobre [os requisitos e compatibilidade da superfície](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

### <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Minha exibição de headset não funciona depois de desligar e fazer uma inicialização rápida.

Desconecte o cabo HDMI e o cabo USB do headset e, em seguida, conecte-os novamente.

### <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Minhas exibições de headset estão muito ruins, mas a janela de visualização do portal de realidade misturada aparece bem.

* Verifique se os recursos do sistema do PC (CPU, memória e disco rígido) estão disponíveis e não estão vinculados ou maximizados por outro aplicativo ou processo.
* Atualize o driver de gráficos.

### <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Estou recebendo um erro "a classe de instalação não está presente ou é inválido" em Device Manager.

Se você vir "sensores do HoloLens" com um ponto de exclamação amarelo em Device Manager, clique duas vezes no dispositivo para obter detalhes adicionais. Se você vir uma mensagem dizendo "os drivers para este dispositivo não estão instalados. (Código 28)--a classe de instalação não está presente ou é inválida ", isso normalmente ocorre porque seu computador está executando o [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). Observe que as N-edições do Windows 10 não dão suporte à realidade mista do Windows e você precisará instalar uma versão não-N do Windows 10.

### <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Meu ambiente do WMR é de tremulação ou de falhas quando eu movo o meu cabeçalho e exibe a visão dupla.

Em um laptop com gráficos integrados e uma GPU NVIDIA, um erro ocorre depois de um período de tempo que parece fazer com que um quadro anterior seja exibido após o próximo quadro, resultando em uma visão dupla do mais rápido que você move a sua cabeça em uma guinada, uma inclinação ou uma movimentação de rolagem. O problema parece estar em drivers após o driver de gráficos NVIDIA 436,48.  A instalação desse driver corrigirá o problema até que o NVIDIA resolva o problema nos drivers atualizados. Para uma instalação direta do driver de gráficos NVIDIA 436,48, visite [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

### <a name="im-experiencing-discomfort-when-i-use-my-headset"></a>Estou tendo discomfort quando uso meu headset.
Para obter informações gerais sobre o conforto na realidade misturada do Windows, consulte [integridade de fone de ouvido de imersão, segurança e conforto do Windows Mixed Reality](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort). Para obter detalhes sobre o fone de ouvido específico, verifique com o fabricante do headset.

### <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Como posso obter uma exibição mais clara em meu Headset?
Tente ajustar o ajuste do seu headset. Ajuste sua posição no seu rosto movendo-o para cima e para baixo ou para a esquerda e para a direita, e ajuste as pulseiras para que fique perfeitamente.

Se o headset der suporte a ele, você também poderá ajustar suas configurações de calibragem. Se o headset tiver um botão para ajustar a calibragem, use-o. Se não estiver, vá para **configurações > realidade misturada > qualidade visual** e ajuste a calibragem lá. Para obter mais informações sobre a calibragem para seu dispositivo específico, verifique com o fabricante do headset.

## <a name="mixed-reality-portal-error-messages-and-problems"></a>Mensagens de erro e problemas do portal da realidade misturada

### <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Recebi uma mensagem de erro "algo deu errado" ou estou tendo problemas no portal de realidade misturada.

Reinicie a realidade mista do Windows:
1. Desconecte ambos os cabos de headset do seu PC.
2. Reinicie o computador.
3. Reconecte seu headset.

Se isso não funcionar, verifique se o seu PC reconhece o headset:
1. Selecione Iniciar.
2. Digite "Gerenciador de dispositivos" na caixa de pesquisa e selecione-o na lista. 
3. Expanda "dispositivos de realidade misturada" e veja se o headset está listado. 

Se não estiver listado, tente o seguinte:
1. Conecte o headset em portas diferentes no computador, se disponível.
2. Verifique as atualizações de software mais recentes do Windows Update.
3. Desinstalar e reinstalar o Windows Mixed Reality:
    1. Desconecte ambos os cabos de headset do seu PC.
    2. Selecione **configurações > realidade misturada > desinstalar** .
    3. Selecione **configurações > dispositivos > Bluetooth & outros dispositivos** para desemparelhar seus controladores de movimento. Selecione cada controlador e, em seguida, selecione "remover dispositivo".
    4. Conecte seu headset ao seu PC para reinstalar a realidade mista do Windows.
    
### <a name="im-getting-a-check-your-usb-cable-error-message"></a>Estou recebendo uma mensagem de erro "verificar o cabo USB".

Conecte seu headset a uma porta USB diferente (e verifique se é um SuperSpeed USB 3,0). Além disso, tente remover todos os extensores ou hubs entre o headset e o computador.

### <a name="im-getting-a-check-your-display-cable-error-message"></a>Estou recebendo uma mensagem de erro "Verifique seu cabo de vídeo".

Experimente o seguinte:
* Conecte seu headset a um DisplayPort 1,2 ou posterior, ou HDMI 1,4 ou posterior. Verifique se a porta corresponde à placa gráfica mais avançada em seu computador.
* Se você estiver usando um adaptador, verifique se ele é compatível com 4K.
* Tente usar uma porta HDMI diferente.
* Se você tiver um monitor externo conectado a uma porta HDMI, tente conectá-lo em um DisplayPort em vez disso e use a porta HDMI para o headset.


## <a name="something-went-wrong-error-codes-and-how-to-resolve-them"></a>Códigos de erro "algo deu errado" e como resolvê-los

| **Códigos de erro do Windows 10** (versão 1809/versões 1709, 1803) | **Mensagem de erro e sugestões de solução de problemas**                    |
|-------------------------------------------------------------|--------------------------------------------------------------------|
|   1-4 / 2197815297-4  | **Verifique o cabo de vídeo: Verifique se o cabo de vídeo do headset está conectado corretamente.** <br/><br/><ol start="1"><li>Desconecte os cabos USB e HDMI de seu headset e conecte-os novamente.</li><li>Marque Device Manager e confirme que, em "monitores", o monitor "headset da realidade mista" está presente.</li><li>Verifique se os drivers gráficos estão atualizados (no site do fabricante da placa gráfica).</li><li>Se você estiver usando um adaptador para conectar seu headset, verifique se ele [dá suporte à realidade mista do Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).</li><li>Se a placa gráfica tiver portas DisplayPort e HDMI, tente usar a porta DisplayPort na placa gráfica e use um adaptador DisplayPort-to-HDMI misto de realidade com suporte.</li><li>Experimente uma porta USB 3,0 diferente em seu PC</li></ol> |
|   1-5 / 2197815297-5  | **Verifique seu cabo de vídeo: as exibições de headset não foram inicializadas corretamente. Tente reiniciar o computador e reconectar o headset.**<br/><br/>O Windows vê seu monitor de fone de ouvido, mas a realidade mista do Windows está tendo problemas para se comunicar com os vídeos em seu headset de realidade misturada. Para corrigir isso:<br/><ol start="1"><li>Verifique se os drivers gráficos estão atualizados (no site do fabricante da placa gráfica).</li><li>Se você estiver usando um adaptador para conectar seu headset, verifique se ele [dá suporte à realidade mista do Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).</li><li>Se a placa gráfica tiver portas DisplayPort e HDMI, tente usar a porta DisplayPort na placa gráfica e use um adaptador DisplayPort-to-HDMI misto de realidade com suporte.</li><li>Tente reiniciar o computador.</li></ol> |
|   7-1, 7-2, 7-3/2181038087-1, 2181038087-2, 2181038087-3  | **A realidade mista do Windows está tendo problemas para se conectar ao headset. Tente desconectar seu headset e conectá-lo novamente.**<br/><br/>A realidade misturada Headset falhou ao inicializar completamente. Esse é provavelmente um erro transitório. Desconecte seu headset e ligue-o novamente para resolver esse problema.
|   7-4 / 2181038087-4  | **A realidade mista do Windows está tendo problemas para se conectar ao headset. Tente desconectar seu headset e conectá-lo novamente.**<br/><br/>O driver de headset de realidade misturada falhou ao inicializar as câmeras de rastreamento no headset. Esse é provavelmente um erro transitório. Desconecte seu headset e conecte-o novamente para resolver esse problema.
|   7-5 / 2181038087-5  | **A realidade mista do Windows está tendo problemas para se conectar ao headset. Tente conectar seu headset em uma porta USB diferente e desconectar temporariamente quaisquer outros dispositivos USB conectados ao seu PC.**<br/><br/>A realidade mista do Windows perdeu a sincronização entre a realidade misturada dos carimbos de data e hora do quadro da câmera e seus carimbos de data/hora Isso pode ser um erro transitório ou uma indicação de problemas de integridade de sinal USB. Para corrigir isso:</li><li>Desconecte temporariamente todos os seus dispositivos USB e periféricos, remova todos os cabos de extensão e conecte apenas seu headset.</li><li>Desabilite os recursos de economia/energia de USB em seu PC, como a suspensão seletiva nas opções de energia do Windows, a configuração "permitir que o computador desligue este dispositivo para economizar energia" em Device Manager e quaisquer configurações de economia de energia USB no firmware do seu PC.</li></ul>
|   7-6 / 2181038087-6  | **Há um problema com o firmware do headset. Tente desconectar seu headset e conectá-lo novamente.** <br/><br/>Isso pode ser um erro transitório. Tente desconectar e reconectar seu headset. Se isso não funcionar:</li><li>Verifique as atualizações do Windows para garantir que você esteja executando o driver de headset mais recente disponível.</li><li>Experimente o headset em outro PC. Se você vir a mesma mensagem de erro, o headset precisará ser atendido.</li></ul>
|   7-7 / 2181038087-7  | **A realidade mista do Windows está tendo problemas para se conectar ao headset. Tente conectar seu headset em uma porta USB diferente e desconectar temporariamente quaisquer outros dispositivos USB conectados ao seu PC.**<br/><br/>O driver de headset de realidade misturada falhou ao inicializar o firmware no headset. Isso pode ser um erro transitório. Tente desconectar e reconectar seu headset. Se isso não funcionar:<li>Desconecte temporariamente dispositivos USB e periféricos que você não precisa para executar a realidade mista do Windows.</li><li>Verifique as atualizações do Windows para garantir que você esteja executando o driver de headset mais recente disponível.</li></ul>
|   7-11 / 2181038087-11 | **Sua CPU é muito antiga para ser compatível com a realidade mista do Windows.**<br/><br/>O computador está falhando na verificação de compatibilidade porque sua CPU não tem o conjunto de instruções AVX exigido pelos controladores de movimento de realidade misturada. Você precisará de um [PC compatível com realidade mista do Windows](https://www.microsoft.com/en-us/windows/view-all-devices?col=wmr-pcs#icons).
|   7-12 / 2181038087-12 | **O headset está conectado a um controlador USB incompatível. Tente conectar seu headset em uma porta USB diferente, se disponível. Ou então, tente instalar um driver USB da Microsoft no lugar de quaisquer drivers incompatíveis.**<br/><br/>O headset pode estar conectado a uma porta USB conectada a um driver de controlador USB não compatível da Microsoft. Esses drivers do controlador USB 3,0 geralmente não têm a capacidade de ler e manipular o [descritor de ContainerId](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-containerids-in-windows), que agrega as partes diferentes do headset da realidade misturada em uma unidade coesa (para reproduzir áudio dos fones de ouvido corretos, exibir as telas corretas e extrair os dados de rastreamento dos sensores corretos). Para alterar o driver do controlador USB: <ol start="1"><li>Iniciar Device Manager.</li><li>Expanda a categoria para controladores de barramento serial universal e clique com o botão direito do mouse para desinstalar o driver de cada item que inclui o texto "controlador de host extensível" **e** não tem "Microsoft" no nome.</li><li>Selecione "excluir o software de driver para este dispositivo" para garantir que os drivers antigos sejam removidos.</li><li>Verifique se cada item que inclui o texto "controlador de host extensível" tem "Microsoft" no final.</li><li>Conecte o HMD.</li></ol>Como alternativa, se o problema for intermitente, o HMD poderá não estar respondendo corretamente aos comandos do driver HMD. Para corrigir, desconecte o HMD por 30 ou mais segundos e, em seguida, conecte-o novamente. | 
|   7-13 / 2181038087-13 | **O headset está conectado a um controlador USB incompatível. Tente conectar seu headset em uma porta USB diferente, se disponível. Caso contrário, você precisará instalar um novo controlador USB 3,0.**<br/><br/>O Windows Mixed Reality não é capaz de sincronizar os carimbos de data/hora da realidade misturada do quadro nos carimbos de data/hora do seu PC. Isso provavelmente é causado por um controlador de host USB 3,0 incompatível que não oferece suporte a ITP (pacotes de carimbo de data/hora Isochronous). Entre em contato com o fabricante do seu PC para ver se o ITP pode ser habilitado ou alterne para outro controlador de host USB com suporte a ITP. |
|   7-14 / 2181038087-14 | **A realidade mista do Windows está tendo problemas para se conectar ao headset. Tente desconectar seu headset e conectá-lo novamente.**<br/><br/>A realidade mista do Windows está tendo problemas para inicializar o sensor de presença em seu headset de realidade misturada. Em Device Manager, o headset mostrará a mensagem de erro "PoseThread falhou ao inicializar o sensor de presença". Para corrigir isso:<br/><ol start="1"><li>Desconecte seu headset e conecte-o novamente. Verifique se o cabo USB está conectado a todo o caminho.</li><li>Tente outra porta USB em seu PC.</li><li>Experimente o headset em outro PC para ver se o fone de ouvido é enumerado completamente em Device Manager nesse PC.</li><li>Verifique se algum outro driver HID conflitante está instalado em seu PC, por exemplo, do teclado ou mouse. (Procure por dispositivos HID em Device Manager com um logotipo de ponto de interrogação neles.)</li><li>Se você estiver usando um headset de realidade mista Samsung executando o Windows 10 versão 1709 ou 1803, siga as instruções para o código de erro 2181038087-12 para verificar se o controlador USB 3,0 está executando um driver de controlador USB não Microsoft.</li></ol> |
|   7-15 / 2181038087-15 | **A realidade mista do Windows detectou um driver WinUSB incompatível instalado.**<br/><br/><ol start="1"><li>Verifique se o driver WinUSB em seu PC é o fornecido com o Windows e se qualquer driver USB de terceiros não substituiu a cópia de WinUSB em seu computador.</li><li>Talvez seja necessário recuperar ou reinstalar a instalação do Windows se o problema persistir.</li></ol> |
|   13-11/-            | O portal de realidade misturada encontrou um problema de registro de aplicativo com o Windows. Verifique o log de eventos do aplicativo (usando Visualizador de Eventos) para ver se há detalhes adicionais. |
|   14-1/-            | O portal de realidade misturada está tendo problemas para inicializar os gráficos e a pilha de composição. Para corrigir isso:<ul><li>Gerenciador de Janelas da Área de Trabalho (DWM, um componente-chave da pilha de gráficos do Windows) pode estar falhando. Verifique o log de eventos do aplicativo (usando Visualizador de Eventos) para ver se isso está ocorrendo.</li><li>Experimente uma desinstalação limpa do seu driver de gráficos e, em seguida, instale o driver de gráficos mais recente no site do fabricante da placa de gráficos.</li></ul> |
|   14-2/C0001160-101  | **Ocorreu um problema ao conectar-se ao seu headset. Tente remover os cabos de extensão que você pode estar usando e verifique se você conectou o headset à porta correta para a placa gráfica. Se você estiver usando qualquer adaptador, verifique se eles são compatíveis com realidade misturada. Se você ainda tiver problemas, tente atualizar o driver de gráficos.**<br/><br/>Falha na inicialização da pilha de exibição e composição da realidade misturada. A placa gráfica ou o driver de placa gráfica do seu PC pode não ser compatível com a realidade mista do Windows. Para verificar isso: <ul><li>Verifique se o seu PC atende aos requisitos mínimos do sistema para a realidade mista do Windows.</li><li>Se você estiver usando PCs Dell Inspiron 5577 no Windows 10, versão 1809 ou mais recente, poderá ver esse erro devido a um conflito com a funcionalidade de pós-processamento de gráficos TrueColor da Dell. Para contornar esse problema, use o aplicativo TrueColor da Dell para desativar o recurso TrueColor e tente executar o portal da realidade misturada novamente.</li><li>Em um PC desktop, instale o driver de gráficos mais recente no site do fabricante da placa de gráficos. Em um laptop, instale o driver de gráficos mais recente para sua marca e modelo no site do fabricante do laptop.</li><li>Se você tiver gráficos de terceiros ou de vídeo/acessórios, desinstale temporariamente esses aplicativos e drivers.</li><li>Selecione "tentar novamente" para ver se é um problema transitório.</li></ul> |
|   14-3/-             | **Ocorreu um problema ao conectar-se ao seu headset. Tente remover os cabos de extensão que você pode estar usando e verifique se você conectou o headset à porta correta para a placa gráfica. Se você estiver usando qualquer adaptador, verifique se eles são compatíveis com realidade misturada. Se você ainda tiver problemas, tente atualizar o driver de gráficos.** <br/><br/><ul><li>Se você estiver usando qualquer modo personalizado ou taxas de atualização no monitor do seu PC, tente definir suas taxas de atualização para 60Hz.</li><li>Verifique se os adaptadores que você está usando dão suporte à realidade mista do Windows.</li><li>Tente instalar o driver de gráficos mais recente no site do fabricante da placa de gráficos.</li><li>Clique em "tentar novamente" para ver se é um problema transitório.</li></ul> |
| 14-4/-             | **Ocorreu um problema ao conectar-se ao seu headset. Tente remover os cabos de extensão que você pode estar usando e verifique se você conectou o headset à porta correta para a placa gráfica. Se você estiver usando qualquer adaptador, verifique se eles são compatíveis com realidade misturada. Se você ainda tiver problemas, tente atualizar o driver de gráficos.** <br/><br/><ul><li>Seu computador pode ter mais monitores de PC conectados do que o seu adaptador gráfico pode dar suporte. Desconecte tudo, exceto seu monitor de PC primário.</li><li>Verifique se os adaptadores que você está usando dão suporte à realidade mista do Windows.</li><li>Instale o driver de gráficos mais recente no site do fabricante da placa de gráficos.</li><li>Clique em "tentar novamente" para ver se é um problema transitório.</li></ul> |
|   15-5/-             | **O portal de realidade misturada perdeu a sincronização com a realidade misturada principal e com os componentes do Windows dos quais depende.**<br/><br/><ul><li>Isso pode ser causado por um problema de desempenho com seu PC. Verifique se sua CPU, GPU e HDD não estão vinculados no Gerenciador de tarefas.</li><li>Desconecte temporariamente todos os outros dispositivos USB do seu PC.</li><li>Reinicie o computador.</li></ul> |
|   -/H0002000-0    | **O sistema operacional do seu PC entrou em um estado incompatível para a realidade mista do Windows**<br/><br/>Verifique se há atualizações no Windows. |
|   -/S0002261-101, S0002361-101 | **Um problema com um componente de Shell de realidade misturada está impedindo que o portal da realidade misturada seja iniciado corretamente**<br/><br/><ul><li>Abra o log do aplicativo usando Visualizador de Eventos no seu PC para verificar se há falhas no aplicativo no momento em que você tentou iniciar a realidade mista do Windows.</li><li>Verifique se o driver de gráficos está atualizado.</li><li>O adaptador HDMI que você está usando é incompatível com a realidade mista do Windows. Consulte o dongle de HDMI para mini porta (DP) com suporte e recomendado [aqui](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).</li></ul> |


## <a name="motion-controller-problems"></a>Problemas do controlador de movimento

### <a name="my-motion-controllers-arent-working-properly"></a>Meus controladores de movimento não estão funcionando corretamente.

Se os seus [controladores de movimento](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality) não estiverem funcionando, não estiver se conectando ou se você não vir uma imagem dos controladores quando estiver desgastando o headset, tente o seguinte:
1. Verifique se os controladores estão ativados. Para ativá-los, pressione e mantenha pressionado o botão Windows por dois segundos.
2. Certifique-se de que os controladores sejam totalmente cobrados e substitua as baterias, se não estiverem.
3. Desligue os controladores e ligue-os novamente enquanto os mantém na frente de você. Pressione e mantenha pressionado o botão do Windows por quatro segundos para desativar um controlador e, em seguida, pressione e mantenha-o pressionado novamente por dois segundos para ativá-lo. 
4. Selecione **configurações > dispositivos > Bluetooth & outros dispositivos** em seu PC e verifique se os controladores estão listados como emparelhados. Se não forem, você precisará [emparelhar](https://support.microsoft.com/en-us/help/4040517/windows-10-controllers-windows-mixed-reality). 
5. Verifique se os controladores de movimento aparecem como "conectado". "Emparelhado" não significa necessariamente que os controladores estejam conectados ao PC. Os controladores devem aparecer na categoria "mouse, teclado & caneta". Os controladores de movimento em "outros dispositivos" falharam no processo de emparelhamento e não estão funcionais. Verifique os LEDs dos controladores de movimento: controladores acesos brilhantes estão emparelhados e conectados, Dimly os controladores acesos não estão conectados.
6. Acesse **iniciar > portal de realidade misturada** no seu PC e selecione "menu". Você deve ver seus controladores de movimento listados, juntamente com uma mensagem de status:
    * Pronto – os controladores estão todos definidos.
    * Rastreamento perdido – o portal de realidade misturada não pode localizar seus controladores. Mantenha-os na frente do headset e reinicie-os pressionando o botão Windows por 4 segundos e, novamente, por 2 segundos.
    * Bateria fraca – Substitua as baterias do controlador.
7. Se você estiver usando um adaptador USB Bluetooth externo, verifique se ele está conectado a uma porta USB 2,0 preta. Ele também deve ser conectado o mais distante possível de qualquer outro transmissor sem fio ou unidades flash USB, incluindo o conector USB para o headset. 
8. Verifique se há apenas um rádio Bluetooth no PC clicando com o botão direito do mouse no menu Iniciar do Windows e selecione Device Manager. Expanda a seção Bluetooth e procure um adaptador. Se você estiver usando a configuração de computador desktop com rádio interno, verifique se uma antena externa está conectada. Se não houver nenhuma antena externa conectada, isso poderá causar problemas de controle. Ou use um dongle Bluetooth externo (USB), desabilite o recurso Bluetooth interno e tente emparelhar e se conectar novamente.
9. Feche a janela configurações de Bluetooth se ela estiver aberta. Se ele estiver aberto em segundo plano, muitas chamadas extras serão feitas no protocolo Bluetooth.
10. Verifique o nível da bateria virtual no controlador de movimento. Em realidade misturada, ative os controladores e você poderá ver um ícone de bateria. Se ele estiver vermelho, substitua as baterias. Relatórios de bateria normalmente são relatórios mais altos do que o nível real imediatamente após conectar um controlador. Aguarde cerca de 15 segundos para deixar o nível da bateria estabilizar e, em seguida, ler o nível.
11. Remova os fones de ouvido e os alto-falantes Bluetooth em **configurações > dispositivos > Bluetooth & outros dispositivos** e desligue os dispositivos. Use a tomada de fone de ouvido ou os palestrantes internos em seu headset de realidade misturada para obter a melhor experiência de áudio.
12. Se você tiver outros dispositivos Bluetooth emparelhados com seu PC, como fones de ouvido ou gamepads, remova alguns deles. Selecione **configurações > dispositivos > Bluetooth & outros dispositivos em seu PC** , selecione os dispositivos e, em seguida, selecione "remover dispositivo".
13. Desconecte o cabo USB em seu headset e conecte-o de volta ao computador para reiniciar a funcionalidade do controlador no PC.
14. As luzes do controlador piscam quando estão passando por uma atualização de firmware. Aguarde a conclusão da atualização do firmware e os controladores devem aparecer em realidade misturada.
15. Verifique se o computador está conectado a uma rede Wi-Fi de 5 GHz. Se o seu laptop estiver conectado a uma rede WiFi de 2,4 GHz, ele normalmente está compartilhando a conexão Bluetooth. Isso pode afetar negativamente o desempenho de WiFi ou Bluetooth, dependendo do design do produto. Altere a banda preferencial para 5 GHz nas configurações do adaptador de rede. Se sua rede não der suporte a 5 GHz, um dongle Bluetooth poderá ser usado em vez do recurso Bluetooth interno.
16. Se as configurações de Bluetooth já tiverem os controladores de movimento emparelhados, o Windows não descobrirá os novos dispositivos até que eles sejam removidos (se tiverem sido adicionados usando um dongle específico, eles só poderão ser removidos com esse dongle).
17. Se o seu computador tiver um Bluetooth interno e você estiver tendo problemas de conexão, tente usar um adaptador USB Bluetooth em vez disso. Para fazer isso, você precisará desligar seu rádio Bluetooth interno em Device Manager e emparelhar os outros dispositivos Bluetooth com o novo adaptador.

### <a name="motion-controller-troubleshooting-flowchart"></a>Fluxograma de solução de problemas do controlador de movimento

![Solucionando problemas de fluxograma para controladores de animação](images/motion-controllers.jpg)

### <a name="my-controller-is-stuck-in-an-infinite-reboot-buzzing-after-leds-cycle"></a>Meu controlador está preso em uma reinicialização infinita (repercussão após o ciclo dos LEDs).

Esse é um indicador de bateria crítica, portanto, verifique se você tem baterias novas no dispositivo. Se o problema persistir, execute a [recuperação do dispositivo](motion-controller-problems.md#how-can-i-restore-the-controllers-to-factory-settings) para redefinir o controlador para as configurações de fábrica.

### <a name="im-trying-to-pair-my-controllers-but-they-never-show-up-in-the-add-a-new-device-menu-in-bluetooth-settings"></a>Estou tentando emparelhar meus controladores, mas eles nunca aparecem no menu "adicionar um novo dispositivo" nas configurações de Bluetooth.

Verifique se você já tem controladores emparelhados, remova-os e tente novamente. Se o problema persistir, reinicie o computador e tente novamente. Se isso falhar, consulte as [perguntas frequentes sobre o Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology).

### <a name="wi-fi-speeds-becomes-slow-on-my-notebook-when-motion-controllers-are-turned-on"></a>As velocidades de Wi-Fi tornam-se lentas no meu notebook quando os controladores de movimento são ativados.

Seu notebook pode compartilhar sua antena Wi-Fi com Bluetooth quando conectado ao ponto de acesso de 2,4 GHz. Verifique no Gerenciador de dispositivos se você pode alternar a preferência de banda para 5 GHz. Se a rede de 5 GHz não estiver disponível e o desempenho for seriamente afetado, considere usar um dongle Bluetooth.

![As configurações de seleção de banda WiFi podem ser encontradas por meio do Gerenciador de dispositivos](images/wifi5ghz.png)

### <a name="my-second-controller-takes-a-long-time-to-reconnect"></a>Meu segundo controlador leva muito tempo para se reconectar.

Alguns rádios da Intel mais antigos terão esse problema se os controladores de movimento estiverem ligados ao mesmo tempo. Evite ligar os controladores ao mesmo tempo.

### <a name="my-qualcomm-bluetooth-radio-cannot-pair-controllers-after-a-pc-crash"></a>Meu rádio do Qualcomm Bluetooth não pode emparelhar controladores após uma falha do PC.

Os drivers de rádio do Qualcomm (QCA) Bluetooth anteriores ao 10.0.0.448 podem terminar em estado inadequado após uma falha do Windows. Desligue o PC completamente para solucionar esse problema. 

### <a name="im-experiencing-poor-controller-tracking-with-marvell-radio"></a>Estou tendo um controle insatisfatório do controlador com o Marvell Radio.

Vá para **Device Manager > bluetooth > adaptador de rádio Bluetooth Marvell AVASTAR > propriedades > driver** e verifique se você está usando o driver 15.68.9210.47 ou posterior.

### <a name="the-mixed-reality-portal-is-working-but-my-motion-controllers-are-tracking-poorly-controllers-keep-flying-away-shaking-etc"></a>O portal de realidade misturada está funcionando, mas meus controladores de movimento estão acompanhando mal (os controladores continuam voando, agitando, etc.).

1. Algumas condições de iluminação podem afetar o controle. Certifique-se de que você não está exposto para direcionar a luz solar e que você não tem muitas fontes de luz de ponto visíveis para seu HMD (por exemplo, cadeias de caracteres de luzes como uma árvore de Natal). 
2. Verifique as [perguntas frequentes do Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). Esses sintomas geralmente são causados por falhas na comunicação entre o controlador e o PC host e indicam uma qualidade de link Bluetooth ruim.

### <a name="motion-controller-leds-are-not-lit-but-the-buttons-and-thumbstick-still-work-in-mixed-reality-portal"></a>Os LEDs do controlador de movimento não estão acesos, mas os botões e Thumbstick ainda funcionam no portal de realidade misturada.

O cache de calibragem do controlador de movimento pode estar corrompido. Para excluir o cache, execute o seguinte comando em um prompt de comando de administrador:

`rmdir /S /Q C:\Windows\ServiceProfiles\LocalService\AppData\Local\Microsoft\Windows\MotionController\Calibration`

Essa pasta não está acessível no Windows Explorer e só pode ser modificada a partir de um prompt de comando de administrador. Depois de excluir a pasta, reinicie o computador e reconecte seus controladores de movimento para restaurar os arquivos de calibragem.

### <a name="motion-controllers-do-not-appear-in-steamvr-apps-and-games"></a>Os controladores de movimento não aparecem em aplicativos e jogos do SteamVR.

Se você conseguir ver seus controladores de movimento na casa Cliff, mas não em aplicativos e jogos do SteamVR, talvez o driver do modelo do controlador de movimento não esteja instalado corretamente. Esse driver é baixado e instalado automaticamente por meio do Windows Update, mas se você estiver em um PC que tenha políticas corporativas ou se Windows Update for, de outra forma, restrito, talvez seja necessário instalar isso manualmente. Para verificar se o driver do modelo do controlador de movimento está instalado corretamente:
1. Ative os dois controladores de movimento e verifique se eles aparecem como "conectado" no aplicativo de configurações em **dispositivos > Bluetooth & outros dispositivos** . Se eles não aparecerem ou aparecerem como "emparelhados", [emparelhá-los](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality).
2. Abra Device Manager e procure "controlador de movimento à esquerda" e "controlador de movimento à direita" em "Bluetooth".
3. Selecione o dispositivo e, em seguida, vá para **exibir > dispositivos por conexão** .
4. Agora, você verá uma exibição dos dispositivos Bluetooth do controlador de movimento acumulados no rádio Bluetooth. No mesmo nó que os dois controladores de movimento devem ser dois dispositivos de "dispositivo HID Bluetooth" e, em cada dispositivo HID Bluetooth, devem ser dispositivos chamados "controlador de movimento" (com ícones cinzas).
5. Clique duas vezes em cada um dos dispositivos "controlador de movimento" e vá para a guia **Driver** . Confirme se a versão do driver listada corresponde a uma dessas [versões do driver do modelo do controlador de movimento](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history).

Para baixar e instalar manualmente o driver de modelo do controlador de movimento, visite [esta página](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/mixed-reality-software#mixed-reality-motion-controller-model-driver-release-history) e procure a versão do driver correspondente à sua versão do Windows 10. As instruções de instalação estão disponíveis na página de download.

### <a name="the-motion-controllers-firmware-update-takes-significantly-longer-than-two-minutes"></a>A atualização do firmware dos controladores de movimento leva muito mais tempo do que dois minutos.

Verifique as [perguntas frequentes do Bluetooth](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology). A baixa qualidade de link Bluetooth geralmente é a causa desses problemas.

### <a name="i-just-inserted-fresh-batteries-but-the-controller-virtual-battery-level-does-not-indicate-full-level"></a>Acabei de inserir baterias novas, mas o nível de bateria virtual do controlador não indica o nível completo.

O nível de bateria do controlador de movimento está ajustado para baterias AA. Algumas baterias recarregáveis de baixa voltagem podem não ser relatadas como completas, embora sejam totalmente cobradas.

### <a name="my-controller-does-not-vibrate-when-battery-is-low"></a>Meu controlador não vibra quando a bateria está baixa.

Haptics é desabilitado quando o nível da bateria fica baixo. Substitua suas baterias.

### <a name="my-device-vibrated-three-times-and-then-shutdown"></a>Meu dispositivo vibrau três vezes e depois desligamos.

Suas baterias estão em execução baixa e atingiu o limite de corte. Substitua suas baterias.

### <a name="my-samsung-motion-controllers-touchpad-is-off-center-or-has-a-dead-spot"></a>Meu touchpad do controlador de movimento Samsung está fora do centro ou tem um ponto de inatividade.

Isso provavelmente é um defeito de hardware e você deve voltar para o fabricante do equipamento ou revendedor para uma substituição ou troca.

### <a name="the-controller-isnt-working-correctly-and-i-cant-update-the-device"></a>O controlador não está funcionando corretamente e não é possível atualizar o dispositivo.

Restaure-o para as condições de fábrica (você precisará de novas baterias):
1. Desconecte e desligue os controladores.
2. Abra a tampa da bateria.
3. Insira suas novas baterias.
4. Pressione e segure o botão de emparelhamento (a guia na parte inferior sob as baterias).
5. Enquanto mantém o botão de emparelhamento, ligue o controlador pressionando e segurando o botão Windows por cinco segundos (Mantenha ambos os botões pressionados).
6. Solte os botões e aguarde até que o controlador ligue. Isso leva até 15 segundos e não há indicadores quando a recuperação do dispositivo está ocorrendo. Se o dispositivo ligar imediatamente na versão do botão, a sequência do botão de recuperação não será registrada e você precisará tentar novamente.
7. Vá para **configurações > Bluetooth > outros dispositivos** e selecione "controlador de movimento-esquerda" ou "controlador de movimento à direita" e "remover dispositivo") para remover associações de controlador antigas das configurações de Bluetooth. 
8. Emparelhe o controlador com o PC novamente.
9. Depois de se conectar com o host e o HMD, o dispositivo será atualizado para o firmware mais recente disponível.

### <a name="lights-and-indicators"></a>Luzes e indicadores

O LED Constellation Ring e haptics indicam o estado do controlador de movimento.

| Estado    | O que causa o estado | Comportamento de luz e vibração associado ao estado |
|----------------------------|-----------------------------|----------------------------------------------------------------------|
| **Ligue**               | Pressione e mantenha o botão do Windows no controlador por dois segundos para ativar o controlador.       | Os LEDs acendem e o controlador vibra uma vez. |
| **Desligar**              | Pressione e mantenha o botão do Windows no controlador por quatro segundos para desligar o controlador.      | Os LEDs desligam e o controlador vibra duas vezes. |
| **Hibernando**               | O controlador entra em estado de suspensão automaticamente quando não está em movimento por 30 segundos. O controlador é ativado automaticamente quando detecta um movimento, exceto quando o dispositivo não está emparelhado com o PC host. Nesse caso, um pressionamento de botão será necessário para ativá-lo. | Os LEDs desligam e piscam a cada três segundos durante o estado de suspensão. |
| **Emparelhamento**                | Pressione e mantenha o botão de emparelhamento dentro do caso da bateria por três segundos.     | Os LEDs pulsam lentamente enquanto estão no modo de emparelhamento e entram sólidos ao sair do modo de emparelhamento. O controlador vibra uma vez se o emparelhamento tiver sido bem-sucedido ou vibrar três vezes se o emparelhamento não for bem-sucedido e atingir o tempo limite. |
| **O controlador conecta/desconecta do PC** | O controlador se conecta com êxito ao PC depois que você o liga, ou o controlador se desconecta do PC durante o uso por algum motivo.| O controlador vibra uma vez na conexão do PC ou na desconexão. |
| **Nível de bateria fraca**      | O nível da bateria é baixo.| Não há nenhuma indicação de LED ou vibração quando a bateria está fraca. Há um ícone de indicador de bateria na alça da representação do controlador em headset. Quando a bateria estiver baixa, o ícone de indicador mostrará 1/4 Full. |
| **Nível de bateria crítica** | Durante a ativação, quando o nível da bateria é "crítico". O nível de bateria "crítico" significa que não há energia suficiente e o controlador será desligado automaticamente.| O controlador vibra três vezes quando você o ativa e, em seguida, desliga automaticamente. Conforme você abordar esse Estado, o ícone de indicador de bateria exibirá vermelho. |


### <a name="how-can-i-tell-if-im-using-bluetooth-technology"></a>Como saber se estou usando a tecnologia Bluetooth?

Os controladores de movimento usam a mesma tecnologia Bluetooth encontrada em muitos dispositivos de consumo e foram projetados para funcionar com o recurso de Bluetooth incluído em qualquer PC recente. Para verificar se o seu PC tem um rádio Bluetooth (se o dispositivo passou pelo verificador de compatibilidade da realidade misturada): 
* Clique com o botão direito do mouse no menu Iniciar do Windows e selecione "Device Manager". 
* Expanda a seção Bluetooth e procure um adaptador. 
* Se o seu computador não tiver o Bluetooth, um dongle recomendado é o [adaptador de baixa energia micro USB Bluetooth 4,0 de baixo consumo](https://www.amazon.com/Plugable-Bluetooth-Adapter-Raspberry-Compatible/dp/B009ZIILLI/ref=sr-1-1?ie=UTF8&qid=1490148230&sr=8-1&keywords=plugable+broadcom). \
![Captura de tela de um exemplo Device Manager. O adaptador é o rádio Bluetooth.](images/devicemanagerbtadapterpic.png) 


### <a name="my-pc-has-bluetooth-technology-but-im-having-problems-with-my-motion-controllers"></a>Meu PC tem tecnologia Bluetooth, mas estou tendo problemas com meus controladores de movimento.

Os controladores de movimento devem funcionar com outros teclados, mouse e controladores de jogo Bluetooth, mas a experiência variará dependendo do modelo de Keyboard, mouse ou controlador de jogo que você usar. Aqui estão algumas coisas que você pode fazer para melhorar o desempenho:
* Se o seu computador tiver o Bluetooth, mas você ainda tiver problemas com os controladores de movimento, considere substituir o rádio Bluetooth pelo adaptador Bluetooth externo plug-in conectado ao USB. Observe que você só pode ter um adaptador de rádio Bluetooth ativo por vez. Se você conectar um rádio externo Além de um rádio existente, será necessário desabilitar o rádio Bluetooth existente no Device Manager (clique com o botão direito do mouse no adaptador e selecione "desabilitar dispositivo") e desemparelhar/emparelhar todos os seus dispositivos Bluetooth anteriores.
* Se você estiver usando um adaptador USB Bluetooth, conecte-o a uma porta USB 2,0 (as portas 2,0 são pretas e não são rotuladas "SS"), se disponíveis. A porta deve ser fisicamente separada de:
    - o conector USB do HMD
    - unidades flash
    - discos rígidos
    - receptores USB sem fio como aqueles para teclados/mouses de preferência, conecte o adaptador Bluetooth USB ao lado oposto do computador o máximo possível desses outros conectores.
* Não instale nenhum software de terceiros.
* Feche a janela configurações de Bluetooth se ela estiver aberta. Deixá-lo aberto em segundo plano significa que muitas chamadas extras são feitas no protocolo Bluetooth.
* Desabilite a configuração "mostrar notificação para se conectar usando o par Swift" em Bluetooth & outros dispositivos para reduzir a atividade de verificação de rádio do host.
* Se você estiver usando uma placa Bluetooth interna, verifique se está usando uma antena Bluetooth externa. 
  * A falta de antenas externas de Bluetooth, nesse caso, é conhecida por causar problemas de controle. 
  * Se isso não funcionar, use um dongle Bluetooth externo (USB) depois de desabilitar o Bluetooth interno.
* É importante que o dispositivo apareça na categoria "mouse, teclado & caneta" nas configurações de Bluetooth. Se em "outros dispositivos", desemparelhe e emparelhe o dispositivo.
* Remova, desemparelhe e desligue os fones de ouvido e os alto-falantes Bluetooth. Eles não têm suporte com a realidade mista do Windows. Você pode usar a tomada de fone de ouvido ou os palestrantes internos em seu headset de realidade misturada para obter a melhor experiência de áudio.

### <a name="how-can-i-pair-my-motion-controllers-to-a-windows-mixed-reality-headset-with-built-in-bluetooth-radio-or-return-them-to-their-factory-pairing"></a>Como posso emparelhar meus controladores de movimento com um headset de realidade mista do Windows com rádio Bluetooth interno ou retorná-los ao emparelhamento de fábrica?

Alguns headsets de realidade misturada do Windows, incluindo o Acer OJO 500 e o Samsung Odyssey +, têm rádios Bluetooth internos para uso com os controladores de movimento. Os controladores de movimento que acompanham esses headsets são emparelhados com o headset da fábrica e não exigem que seu PC tenha um rádio Bluetooth separado. Esses controladores de movimento _podem_ ser emparelhados manualmente para o rádio Bluetooth do seu PC, por exemplo, para uso com headsets de realidade mista do Windows que não têm rádios Bluetooth internos. Para retornar os controladores de movimento ao emparelhamento de fábrica, ou para emparelhá-los com um headset de realidade mista do Windows com rádio Bluetooth interno, execute o aplicativo de dispositivo do headset (por exemplo, o aplicativo "Acer OJO 500" ou o aplicativo "Samsung HMD Odyssey + Setup", instalado automaticamente na primeira vez em que o headset está conectado) e siga as instruções para o emparelhamento do controlador de movimento.


## <a name="performance-questions"></a>Perguntas de desempenho

### <a name="how-can-i-tell-if-the-windows-mixed-reality-headset-is-rendering-at-60hz-or-90hz-framerate"></a>Como saber se o headset de realidade misturada do Windows está renderizando na taxa de quadros de 60Hz ou 90Hz?

Verifique o **portal do dispositivo > guia desempenho** . 

**Observação** : se você tiver uma GPU discreta com portas HDMI 2,0 e uma CPU com quatro ou mais núcleos físicos, deverá obter 90 Hz. Se sua GPU tiver apenas uma saída HDMI 1,4, você poderá usar um DisplayPort para [adaptador HDMI 2,0](https://holodocswiki.com/wiki/Recommended_adapters_for_Windows_Mixed_Reality_Capable_PCs) como solução alternativa. 

**Observação** : a **exibição do headset > as configurações de qualidade visual** afetam apenas a renderização da experiência inicial do Windows Mixed Reality.

### <a name="what-do-i-do-if-my-pc-appears-to-be-running-slowly"></a>O que devo fazer se meu PC parecer estar lento?

O sistema pode estar lento por muitos motivos e, na maioria dos casos, isso será sublado após alguns segundos. Se você tiver esse problema por longos períodos de tempo:
1. Feche todos os aplicativos não utilizados na área de trabalho.
2. Verifique se o seu laptop está conectado a uma fonte de alimentação.
3. Verifique se o PC não está aquecendo.
4. Reduza a qualidade visual na sua página inicial do Windows Mixed Reality.
5. Verifique se você tem os drivers gráficos mais recentes para seu PC (consulte a seção drivers gráficos).

### <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Meu PC está se aquecendo enquanto eu executo as experiências de realidade misturada. Como fazer mantê-lo interessante?

1. Verifique se a bateria é cobrada e se a fonte de alimentação está conectada.
2. Certifique-se de que os ventiladores que ficam com o ar para dentro ou para fora do PC não estejam bloqueados.
3. Use o PC em um ambiente relativamente interessante.
4. Verifique se não há fontes de calor (por exemplo, as aberturas do sol ou do calor) apontadas para o PC.

### <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Meus elementos visuais são ruins, carregam lentamente ou não parecem bons.
* Verifique se o headset está conectado à placa gráfica correta no seu computador. Alguns PCs têm placas gráficas integradas e discretas. O cartão discreto geralmente oferecerá o melhor desempenho. [Saiba mais sobre hardware de PC](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).
* Feche os aplicativos não utilizados na sua área de trabalho.
* Verifique se o fone de ouvido se ajusta perfeitamente (Mova-o para baixo e para cima ou para a direita para ajustar).
* Ajuste as configurações visuais do headset em **configurações > realidade misturada > tela de headset** . Quando "qualidade visual" estiver definida como "automática", escolheremos a melhor experiência de realidade misturada para seu PC. Para obter uma experiência com mais detalhes visuais, defina "qualidade visual" como "alta". Se os visuais estiverem ruins, talvez você queira selecionar uma configuração mais baixa.
* Tente ajustar a calibragem do headset. As lentes devem ser ajustadas para corresponder à sua distância de Interpupillary (IPD), a distância entre o Pupils. Se você não souber seu IPD, um optometrist deverá ser capaz de medir para você. Também há sites criados para medir o IPD. Depois de saber seu IPD, use o botão de calibragem do headset para fazer ajustes. Se o headset não tiver um botão de calibragem, selecione **configurações > realidade misturada > tela de headset** e ajuste o "controle de calibragem".


## <a name="tracking-system-problems"></a>Controlando problemas do sistema

### <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>O sistema não pode encontrar o limite e estou sendo apresentado à interface do usuário da instalação.

Isso significa que o sistema de controle não conseguiu reconhecer seu ambiente. Se você estiver em um novo ambiente, deverá configurar o [limite](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/set-up-windows-mixed-reality#set-up-your-room-boundary). Se você já usou o dispositivo neste ambiente e configurou um limite:
* Verifique se a sala tem luz suficiente.
* Verifique se você gastou o dispositivo e procurou a sala. O dispositivo deve observar seu ambiente para saber onde ele está. Ele não encontrará seus limites se estiver sentado em uma mesa ou escrivaninha.
* Desconecte o dispositivo, feche a realidade mista do Windows e conecte o dispositivo novamente.
* Algo pode ter mudado em seu ambiente e o dispositivo não o reconhece mais. Tente configurar um novo limite.

Se essas etapas não resolverem o problema, exclua os dados do ambiente e configure o limite novamente.

### <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>O sistema está apresentando a interface do usuário que me pede para escolher a configuração de todas as experiências ou de ser encaixada/posicionada, e eu vejo meus limites.

O dispositivo está demorando muito para localizar os limites. Você pode ignorar essa mensagem escolhendo a opção para usar um limite e você será levado para sua página inicial do Windows Mixed Realm com seus limites presentes.

### <a name="i-frequently-see-a-message-saying-ive-lost-my-bounds"></a>Com frequência, vejo uma mensagem dizendo "Eu perdi meus limites".

O sistema de controle está tendo um controle de tempo rígido e identificando seu ambiente. Nesse estado, o dispositivo não pode mais exibir seus limites e os comutadores do headset para 3DOF para evitar que você se aprofunde no mundo real até localizar os limites novamente. Para corrigir isso:
1. Certifique-se de que a sala tenha luz suficiente.
2. Execute a instalação novamente se você redecorau ou remodelou a sala recentemente.
3. Desconecte o dispositivo, feche a realidade mista do Windows e conecte-o novamente.
4. Limpe os dados do ambiente e configure o dispositivo novamente.
5. Se a mensagem persistir, contate o atendimento ao cliente.

### <a name="i-can-look-around-but-i-cant-translate-im-stuck-in-3dof"></a>Posso examinar, mas não posso traduzir (estou preso por 3DOF).

Isso significa que o sistema de controle não pode gerar pose ou o aplicativo foi interrompido usando novos dados de pose a serem renderizados. Verifique o seguinte:
* Verifique se a sala tem luz suficiente.
* Verifique se a sala tem detalhes suficientes para acompanhar.
* Desconecte o dispositivo, feche a realidade mista do Windows e conecte o dispositivo novamente.
* Se a mensagem persistir, contate o atendimento ao cliente

### <a name="the-view-in-the-hmd-is-completely-frozen"></a>A exibição no HMD é completamente congelada.

Isso geralmente significa que o aplicativo ou um componente de nível de sistema falhou. Tente:
1. Pressione o botão "página inicial" para sair do aplicativo.
2. Desconecte o dispositivo, feche o MRP e conecte o dispositivo novamente.
3. Reinicialize o PC.

### <a name="i-frequently-see-a-black-border-around-the-edges-of-the-view-in-the-hmd-sometimes-it-looks-like-im-looking-down-a-tunnel"></a>Eu vejo com frequência uma borda preta em torno das bordas da exibição no HMD. Às vezes, parece que estou procurando um túnel.

Isso significa que o aplicativo não é capaz de pressionar a taxa de quadros em seu computador e o sistema está usando quadros antigos para renderizar a exibição no HMD. Como os aplicativos só renderizam a parte do mundo que você está vendo, se eles não atingirem as taxas de quadros de forma consistente, o sistema tentará continuar a renderizar o mundo a partir de um ponto de vista anterior e preencherá os detalhes ausentes com preto. Se isso ocorrer com frequência:
1. Fechar ou encerrar todos os programas desnecessários para liberar memória e CPU.
2. Reduza as configurações de detalhes em seu aplicativo.
3. Reduza as configurações de detalhes nas configurações de realidade mista do Windows.

### <a name="the-view-in-the-hmd-is-jittering-and-stuttering-a-lot"></a>O modo de exibição no HMD está se estremindo e se esficando muito.

Há vários motivos pelos quais isso pode acontecer. As principais causas são o sistema não poder renderizar o conteúdo para o headset ou o sistema de rastreamento está enfrentando problemas. Verifique o seguinte:
1. Verifique se o PC não está sob contenção de recursos. Abra o Gerenciador de tarefas e verifique se os recursos de computação são gratuitos (por exemplo, 80% de CPU livre, 400 MB de RAM e e/s de disco estão abaixo de 80%).
2. Verifique se você tem os drivers gráficos mais recentes para seu hardware. Consulte a seção driver de gráficos para obter mais informações.
3. Verifique se a sala tem luz suficiente.
4. Desconecte o dispositivo, feche a realidade mista do Windows e conecte o dispositivo novamente.
5. Reinicie o computador.
6. Se o problema persistir, entre em contato com o atendimento ao cliente.

### <a name="the-world-briefly-froze-and-perhaps-tilted-or-flipped-upside-before-returning-to-normal"></a>O mundo brevemente froze e talvez se inclinasse ou se inverteu de cabeça antes de retornar ao normal.

Isso pode ser causado por um aplicativo ou componente no nível do sistema que está atingindo um erro fatal ou uma falta temporária de memória ou recursos de CPU. Verifique o seguinte:
1. Abra "Gerenciador de tarefas" e verifique se você tem pelo menos 20% de memória livre e livre de 400 MB (por exemplo, 80% de CPU livre, 400 MB de RAM e e/s de disco está abaixo de 80%).
2. Abra "Visualizador de Eventos" e vá para **logs do Windows >** entradas de eventos de aplicativo e de erro no momento do congelamento. Verifique se algum processo falhou.
3. Tente reinicializar o computador se esse problema persistir.

### <a name="the-world-flipped-upside-down-momentarily-and-returned-to-normal"></a>O mundo se inverteu de cabeça momentaneamente e retornou ao normal.

Isso geralmente é causado por erros na obtenção de dados de sensor do headset para informar os algoritmos de controle. Se isso ocorrer com frequência:
1. Conecte o headset em uma porta USB 3,0 diferente.
2. Conecte o headset diretamente ao PC em vez de um hub USB 3,0.
3. Se o problema persistir, entre em contato com o atendimento ao cliente.

### <a name="the-world-is-tilted-but-i-can-navigate-and-walk-around-fine-in-windows-mixed-reality"></a>O mundo está inclinado, mas posso navegar e percorrer o problema na realidade mista do Windows.

Isso geralmente é causado por erros de dados de sensor sendo registrados nos dados de ambiente armazenados no seu computador. Isso pode fazer com que a realidade mista do Windows pareça inclinada, às vezes permanentemente. Experimente o seguinte:
1. Desconecte o HMD, feche a realidade mista do Windows e conecte o headset novamente.
2. Reinicialize o PC.
3. Apague os dados do seu ambiente.

## <a name="webvr-questions"></a>Perguntas WebVRs

### <a name="why-cant-i-see-my-controllers-when-viewing-vr-content-from-edge"></a>Por que não consigo ver meus controladores ao exibir o conteúdo VR do Edge?

Nem todo o conteúdo do WebVR é criado para dar suporte a controladores de movimento. O WebVR permite que os desenvolvedores de conteúdo ofereçam suporte a diferentes tipos de entrada, como controladores de jogos ou controladores de movimento. Se você não vir seus controladores em um site, provavelmente ele não terá suporte ao controlador de movimento.

### <a name="why-cant-i-use-the-mouse-in-an-immersive-webvr-view"></a>Por que não posso usar o mouse em uma exibição WebVR de imersão?

Esse é um recurso opcional da especificação WebVR. Nem todos os navegadores oferecem suporte a esse recurso, e nem todo o conteúdo do WebVR é criado para dar suporte à entrada do mouse. O WebVR permite que os desenvolvedores de conteúdo ofereçam suporte a diferentes tipos de entrada, como mouse, teclado, controladores de jogos ou controladores de movimento. O comportamento de entrada do mouse varia de acordo com o navegador. No Microsoft Edge, os autores de sites devem garantir que eles tomam ' pointerlock ' ao apresentar o fone de ouvido para que a entrada do mouse funcione.

### <a name="why-does-my-controller-look-like-a-viveoculus-has-strange-orientation-or-the-buttons-are-incorrectly-mapped"></a>Por que meu controlador parece um Naopak/oculus, tem uma orientação estranha ou os botões estão mapeados incorretamente?

O site provavelmente não tem suporte ao controlador de movimento completo.

### <a name="why-cant-i-view-360-degree-videos-from-youtubefacebookvimeothe-guardiannew-york-times-etc-from-edge-in-vr"></a>Por que não consigo exibir vídeos 360 graus do YouTube/Facebook/Vimeo/do guardião/Nova York vezes, etc. do Edge no VR?

Assim como qualquer outra especificação da Web ou padrão, o autor tem a opção de implementá-lo ou não. Há uma especificação WebVR que permite que sites iniciem experiências VR diretamente do navegador e os autores desses sites não implementaram essa especificação no momento. Pode haver aplicativos para download em algumas plataformas que permitem a exibição de conteúdo VR desses fornecedores.

### <a name="why-cant-i-enter-vr-from-firefox-or-chrome"></a>Por que não posso inserir o VR no Firefox ou no Chrome?

O WebVR só tem suporte dos dispositivos Windows Mixed Reality no Edge no momento.

### <a name="when-i-enter-vr-from-a-website-why-do-i-see-a-blank-screen-in-my-headset"></a>Quando eu inseri o VR em um site, por que vejo uma tela em branco no meu Headset?

O site pode não ter implementado suporte para computadores com várias GPU (incluindo laptops GPU híbridos). Tente:
* Recarregue a página.
* Em computadores desktop, conecte o headset no mesmo adaptador gráfico que o monitor que está exibindo o Microsoft Edge. Conecte ambos à placa gráfica mais alta, não ao adaptador gráfico integrado.

### <a name="when-i-exit-vr-when-watching-a-video-from-edge-the-sound-continues-playing-but-the-edge-window-is-grayed-out"></a>Quando eu sair de VR ao assistir a um vídeo do Edge, o som continuará sendo reproduzido, mas a janela de borda ficará esmaecida.

Esse é um problema conhecido ao executar o WebVR do Edge no cliffhouse de realidade misturada. Para resolvê-lo, pressione escape no teclado em vez de pressionar o botão Windows para sair da experiência do WebVR ou ativar a janela de borda esmaecida selecionando-a e, em seguida, pare o vídeo.

### <a name="can-i-use-webvr-on-the-hololens"></a>Posso usar WebVR no HoloLens?

A Microsoft não anunciou nada sobre WebVR no HoloLens neste momento.

### <a name="why-is-my-view-at-floor-level-when-viewing-webvr-content-from-edge"></a>Por que a minha exibição no nível do piso ao exibir o conteúdo do WebVR da borda?

O site não dá suporte adequado a headsets do Windows Mixed Reality. Para solucionar esse problema:
1. Coloque o headset no chão do seu espaço.
2. Navegue até a página do WebVR usando o Microsoft Edge na área de trabalho (não dentro da realidade misturada).
3. Clique no botão na página da Web para inserir VR.
4. Aguarde 5-10 segundos para a experiência entrar totalmente no modo de imersão.
5. Pegue o headset e coloque-o em sua cabeça.

### <a name="the-display-is-very-low-resolution-in-some-webvr-experiences"></a>A exibição tem uma resolução muito baixa em algumas experiências de WebVR.

Os sites não dão suporte adequado a headsets de alta resolução. Para solucionar este problema:
* Se iniciar o WebVR da área de trabalho (em vez de dentro da realidade misturada cliffhouse), verifique se a janela está maximizada antes de entrar em VR.
* Evite redimensionar a janela do Microsoft Edge depois de inserir o VR.

### <a name="why-does-the-webvr-immersive-view-exit-when-i-change-browser-tabs"></a>Por que a exibição de imersão de WebVR é encerrada quando eu altero as guias do navegador?

Este comportamento é esperado. Por motivos de segurança, somente a guia active browser pode acessar fones de ouvido conectados.

### <a name="why-cant-i-hear-audio-on-a-particular-webvr-experience"></a>Por que não consigo ouvir áudio em uma experiência específica do WebVR?

O site pode estar usando o formato de arquivo de áudio OGG, ao qual o Microsoft Edge não oferece suporte no momento.

Você pode relatar sites desfeitos diretamente à equipe do navegador Microsoft Edge no [Issue Tracker](https://developer.microsoft.com/en-us/microsoft-edge/platform/issues/)ou por meio do twitter usando [#EdgeBug hashtag](https://blogs.windows.com/msedgedev/2016/08/11/edgebug-twitter/).

### <a name="why-does-haptic-feedback-not-work-in-webvr-with-motion-controllers"></a>Por que os comentários do Haptic não funcionam no WebVR com os controladores de movimento?

No momento, o Microsoft Edge não dá suporte a haptics nas extensões da API do gamepad do WebVR.


## <a name="steamvr-questions"></a>Perguntas SteamVRs

### <a name="how-can-i-play-steamvr-games-in-my-windows-mixed-reality-immersive-headset"></a>Como posso jogar SteamVR Games em meu headset de imersão de realidade mista do Windows?

Você deve instalar o Windows Mixed Reality para SteamVR em seu computador e configurar o SteamVR:
* [Baixe e instale o SteamVR](https://steamcdn-a.akamaihd.net/client/installer/SteamWindowsMRInstaller.exe).
* Inicie o SteamVR. O tutorial do SteamVR deve ser iniciado automaticamente.
* Conecte seu headset ao seu PC e ligue seus controladores de movimento.
* Depois que a página inicial do Windows Mixed Reality for carregada e seus controladores estiverem visíveis, abra o aplicativo de fluxo em sua área de trabalho.
* Use o aplicativo de fluxo para iniciar um jogo SteamVR da sua biblioteca de fluxo. Para iniciar jogos do SteamVR sem desligar o headset, você pode encontrá-los e iniciá-los no início da realidade mista do Windows **> todos os aplicativos** . 

### <a name="i-get-a-message-that-says-to-use-steamvr-with-windows-mixed-reality-you-need-to-install-the-latest-windows-update-or-windows-developer-mode-required"></a>Recebo uma mensagem que diz "para usar o SteamVR com o Windows Mixed Reality, você precisa instalar o Windows Update mais recente" ou "o modo de desenvolvedor do Windows necessário".

1. Verifique se o PC está executando a versão mais recente do Windows 10. Para verificar isso, vá para **configurações > > do sistema** . Em "especificações do Windows", verifique se "Build do sistema operacional" é 16299,64 ou superior.
2. Verifique se você não tem nenhuma atualização aguardando para baixar ou instalar. Vá para **configurações > atualização & segurança > Windows Update** e selecione "verificar atualizações". Talvez seja necessário verificar se há atualizações várias vezes para continuar verificando se há atualizações até que nenhuma outra atualização esteja disponível e reinicie o computador.

### <a name="steamvr-is-crashing-after-updating-windows"></a>O SteamVR está falhando após a atualização do Windows.

Algumas versões mais antigas do Windows Mixed Reality for SteamVR não são mais compatíveis com o Windows. Você pode ter uma versão antiga do Windows Mixed Reality para SteamVR. Para garantir que você está atualizado:
1. Em sua biblioteca de fluxo, acesse **Software > a realidade mista do Windows para SteamVR** .
2. Clique com o botão direito do mouse e vá para "Propriedades".
3. Selecione a guia "atualizar" e selecione "sempre manter este aplicativo atualizado".
4. Force a atualização acessando a guia "arquivos locais" e selecionando "verificar a integridade dos arquivos de aplicativo".
5. Reinicie o fluxo e o SteamVR.

Se o SteamVR ainda estiver falhando após a atualização, você poderá ter duas instalações do Windows Mixed Reality para SteamVR em seu computador. Para confirmar se este é o caso:
1. Localize%LocalAppData%\openvr\openvrpaths.vrpath e abra-o no bloco de notas.
2. Nas seções "drivers externos", procure várias entradas para "MixedRealityVRDriver" 
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver",
      "E:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
3. Se você vir várias entradas, remova as duas entradas mais antigas. Observe que, quando você tiver apenas uma entrada, não deverá mais ser uma vírgula no final da linha, por exemplo:
   ```json
   "external_drivers" : [
      "D:\\Steam\\steamapps\\common\\MixedRealityVRDriver"
   ],
   ```
4. Salve o arquivo e feche-o.
5. Reinicie o fluxo e o SteamVR.

### <a name="my-controllers-arent-working-as-expected-in-steamvr"></a>Meus controladores não estão funcionando conforme o esperado no SteamVR.

1. Feche o SteamVR.
2. Retorne ao início da realidade misturada e confirme se os controladores estão funcionando conforme o esperado.
3. Inicie a experiência do SteamVR novamente e os controladores devem voltar ao normal.
4. Se os problemas persistirem, envie comentários usando o [Hub de comentários do Windows](https://support.microsoft.com/en-us/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app) na categoria realidade misturada e inclua SteamVR no resumo.

Observe que você usará seus controladores de movimento de forma diferente em jogos diferentes. Aqui estão alguns conceitos básicos para ajudá-lo a começar:
* Para abrir o painel de fluxo, pressione direto para baixo no Thumbstick esquerdo.
* Para sair de um jogo SteamVR e retornar para a página inicial do Windows Mixed Reality, pressione o botão Windows. Em seguida, selecione o botão Home da realidade misturada que aparece na tela.

### <a name="my-left-and-right-controllers-are-reversed-in-steamvr"></a>Meus controladores à esquerda e à direita são revertidos em SteamVR.

Inicie o jogo com os controladores desligados e, em seguida, gire o lado esquerdo, seguido pelo correto.

### <a name="my-games-are-running-slowly"></a>Meus jogos estão em execução lenta.

1. Confirme se seu PC atende às especificações do SteamVR no Windows Mixed Reality
2. Confirme se seu PC atende às especificações do jogo SteamVR que você está jogando.
2. No portal da realidade misturada na área de trabalho, selecione "Pausar" para parar a visualização da área de trabalho.
3. Siga as instruções acima para verificar se você está executando o Windows 10 Build 16299,64 ou posterior.
4. Verifique se seu PC tem os drivers gráficos mais recentes.
5. Verifique o Gerenciador de tarefas para ver quais outros processos podem estar em execução no seu computador e consumir recursos.
6. Verifique se o vapor está baixando um jogo em segundo plano. Isso pode consumir recursos e fazer com que jogos funcionem mal.
7. Há um problema de desempenho conhecido que afeta uma pequena classe de aplicativos que não têm uma janela visível, por exemplo, SteamVR Home. A grande maioria dos aplicativos não se enquadra nessa categoria, e uma correção estará disponível em uma atualização futura.

Se ainda estiver com problemas de desempenho inesperados, envie-nos seus comentários usando o Hub de comentários do Windows. Certifique-se de seguir as instruções para [incluir um rastreamento de desempenho SteamVR](using-steamvr-with-windows-mixed-reality.md#sharing-feedback-on-steamvr). 

### <a name="steamvr-is-showing-a-compositor-error-for-example-shared-ipc-compositor-connect-failed-400"></a>SteamVR está mostrando um erro de compositor (por exemplo, "falha de conexão do compositor de IPC compartilhado (400)").

Há um problema conhecido em que isso pode acontecer se o headset e o monitor primário estiverem em dois adaptadores de vídeo diferentes. Anexe o monitor ao mesmo adaptador do headset e configure esse monitor para ser o monitor principal no **aplicativo configurações > sistema > exibição** .

### <a name="steamvr-content-appears-in-the-wrong-place-like-beneath-the-floor-or-above-my-head"></a>O conteúdo do SteamVR aparece no lugar errado, como abaixo do piso ou acima da minha cabeça.

Redefina sua posição: 
1. Clique no Thumbstick do controlador à esquerda para abrir o "painel do SteamVR".
2. Selecione o botão "configurações".
3. Selecione "redefinir posição encaixada".

### <a name="my-steam-app-closed-unexpectedly"></a>Meu aplicativo de fluxo fechou inesperadamente.

O aplicativo de fluxo será fechado se você bloquear a tela do seu PC, remover o headset, trocar os usuários ou se seu PC entrar em suspensão.


## <a name="speech-and-audio-problems"></a>Problemas de fala e áudio

### <a name="i-cant-hear-any-sound-in-my-headset-or-sound-is-playing-through-my-computer-instead-of-my-headset"></a>Não consigo ouvir nenhum som em meu headset ou o som está passando pelo meu computador em vez do meu headset.

* Se o headset de imersão não incluir fones de ouvido internos, você precisará conectar fones de ouvido à tomada de áudio no headset. A tomada muitas vezes está localizada logo atrás ou abaixo do visor ou das lentes do headset. Verifique com seu fabricante de headset se você não conseguir encontrá-lo.
* Alguns headsets de áudio têm botões físicos para controlar o volume. Se o áudio não estiver funcionando, verifique se o volume está desativado ou mudo.
* A realidade mista do Windows foi projetada para reproduzir som pelo headset de imersão quando o portal da realidade misturada estiver em execução e você tiver fones de ouvido conectados a ele. Quando você tirar o fone de ouvido ou virar o visor, fechar o aplicativo do portal de realidade misturada ou quando esse aplicativo não tiver sido usado por 15 minutos, o áudio mudará para o dispositivo de reprodução padrão do Windows. Você pode alterar essa configuração em **configurações > realidade misturada > áudio e fala.**
* Verifique se o headset de áudio está conectado completamente à tomada de áudio. O headset do Acer em particular pode exigir mais cuidado para garantir que o headset de áudio esteja conectado.
* Verifique se o headset/microfone de áudio está conectado ao headset e não ao PC.
* O painel de controle de som do Windows mostra apenas os pontos de extremidade de áudio habilitados, não os pontos de extremidade desabilitados. O dispositivo de áudio do headset será desabilitado quando você não estiver desgastando o headset, portanto, você precisa clicar com o botão direito do mouse no painel de controle de som e escolher "mostrar dispositivos desabilitados" para vê-lo; o nome do dispositivo é "áudio Realtek USB 2.0". Depois de fazer isso, você pode alterar o nome na página "Propriedades" para algo que você reconhecerá com mais facilidade. Você pode fazer isso para as guias de reprodução e gravação.
* Se o áudio não estiver funcionando em aplicativos de realidade misturados (por exemplo, Netflix), isso pode ser causado por um problema conhecido em que a realidade mista do Windows não é atualizada automaticamente para corresponder à versão do sistema operacional. Para corrigir esse problema e obter a melhor experiência de realidade misturada, acesse **configurações > atualização & segurança > Windows Update > verificar se há atualizações** .

**Observação:** O áudio espacial da realidade mista do Windows funciona melhor com fones de ouvido incorporados ou conectados diretamente ao headset de imersão. Alto-falantes de PC ou fones de ouvido conectados ao PC podem não funcionar bem para áudio espacial.

**Observação:** A realidade mista do Windows não dá suporte a headsets de áudio Bluetooth.

### <a name="im-experiencing-sudden-volume-changes-lost-audio-or-buzzing"></a>Estou enfrentando alterações de volume repentinas, perda de áudio ou repercussão.

* Alguns aplicativos, incluindo muitos daqueles iniciados por meio de SteamVR, podem perder áudio ou parar quando o dispositivo de áudio muda conforme você inicia ou interrompe o portal de realidade misturada. Reinicie o aplicativo depois de abrir o aplicativo do portal de realidade misturada para corrigir isso.
* Se outro dispositivo USB de multimídia (como uma Web Cam) compartilhar o mesmo hub USB interno ou externo com o headset de realidade mista do Windows, a tomada de áudio/fone de ouvido do headset pode ocasionalmente ter um som de zumbi ou nenhum áudio. Conecte seu headset em uma porta USB que usa um Hub diferente ou desconecte/Desabilite seu outro dispositivo de multimídia USB.
* Se você notar uma intermitência alta de ruído de fones de ouvido conectados ao headset, é possível que o hub USB do PC não seja capaz de fornecer energia suficiente para o headset de realidade mista do Windows. Se isso ocorrer, envie um bug do [Hub de comentários](https://docs.microsoft.com/hololens/hololens-feedback) imediatamente. Soluções alternativas que podem ajudar a não usar cabos de extensão, usando um HUB USB 3,0 dedicado, com alimentação externa, ou tentando uma porta USB diferente no PC.

### <a name="my-bluetooth-audio-headset-isnt-working-as-expected"></a>Meu headset de áudio Bluetooth não está funcionando conforme o esperado.

A Microsoft não recomenda o uso de headsets de áudio Bluetooth com a realidade mista do Windows. Os periféricos de áudio Bluetooth não funcionam bem com experiências de voz e de som espacial do Windows Mixed, e os headsets de áudio Bluetooth não dão suporte à entrada de microfone e à saída de estéreo ao mesmo tempo, para que você não ouça estéreo ou som espacial ao usá-lo para gamechat ou outra entrada de voz. Fones de ouvido de áudio Bluetooth também podem afetar negativamente sua experiência com o controlador de movimento. 

### <a name="sound-isnt-coming-from-expected-directions"></a>O som não provém de direções esperadas.

A página inicial do Windows Mixed Realm inclui som espacial (áudio que parece ser proveniente dos aplicativos localizados em sua casa). À medida que você muda e avança mais ou longe de cada aplicativo, a direção e o nível de som mudarão para o sentido de realismo. Aqui estão alguns motivos para direções de som inesperadas: 
* Quando você abre e joga música de um aplicativo de música com capacidade de fundo (como o Groove Music) em sua casa e, em seguida, abre uma experiência de VR de imersão (como um jogo), o som do aplicativo de música irá fading cruzado do som espacial para o estéreo. Ele pode parecer mais alto do que antes porque não há mais nenhuma distância entre você e o som.
* Se você tiver o Cortana habilitado em seu PC host antes de usar o headset de realidade misturada do Windows, poderá perder o som espacial aplicado aos aplicativos em sua página inicial do Windows Mixed Reality. Para corrigir isso, desative "permitir que a Cortana responda à Ei Cortana" em **configurações > Cortana** na área de trabalho antes de iniciar a realidade mista do Windows ou habilite "Windows Sonic para fones de ouvido" na janela do aplicativo de desktop no Windows Mixed Reality Home:
    1. Clique com o botão esquerdo do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione-o na lista de dispositivos de áudio.
    2. Clique com o botão direito do mouse no ícone do orador na barra de tarefas da área de trabalho e selecione "Windows Sonic para fones de ouvido" no menu "configuração do orador".
    3. Repita essas etapas para todos os seus dispositivos de áudio (pontos de extremidade).

### <a name="speech-commands-are-not-working-as-expected"></a>Os comandos de fala não estão funcionando conforme o esperado.

* Para usar comandos de fala, as configurações de fala e idioma em seu computador devem ser definidas como um [idioma com suporte na realidade mista do Windows](https://support.microsoft.com/en-us/help/4039262/windows-10-mixed-reality-setup-faq#Languages). Para verificar as configurações de idioma e de fala do Windows, selecione **configurações > hora & idioma > região & idioma** e **configurações > hora & linguagem > fala** .
* Se o headset não tiver um microfone interno, você precisará anexar fones de ouvido com um microfone ao headset ou ao seu PC. Para que a entrada do microfone seja alternada automaticamente para o headset quando você o tiver ativado, vá para **configurações > realidade misturada > áudio e fala** e ative "quando eu usar meu Headset, mude para microfone MIC".
* Alguns headsets de áudio têm um botão físico para ativar mudo e mudo do microfone. Se os comandos de fala não estiverem funcionando, verifique se o microfone está mudo.
* Os headsets de áudio com um microfone que Dangles do cabo earbud não têm um bom desempenho para comandos de voz em ambientes com ruídos de ambiente.
* A Cortana pode ser lenta na primeira vez que ela é invocada em uma sessão do portal da realidade misturada. Vá para **configurações > Cortana > fale com a Cortana** e certifique-se de que "permitir que a Cortana responda ao Ei Cortana" esteja habilitado.
* Em alguns PCs, o lucro de captura de voz padrão para o microfone conectado ao headset pode estar definido como muito baixo. Se você tiver comandos de fala não confiáveis ou ditado, poderá tentar executar a solução de problemas de configuração do microfone. Você pode acessar essa solução de problemas por meio das **configurações > hora & idioma > fala** e, em seguida, selecione "introdução" na seção "microfone". Faça isso por meio do aplicativo de desktop na casa do Windows Mixed Reality enquanto aproveita o headset para afetar o microfone que você usa para a realidade mista do Windows. Selecione o ponto de extremidade apropriado no assistente de solução de problemas.

### <a name="i-only-have-one-audio-headset-and-i-want-to-use-it-for-both-desktop-and-my-headset"></a>Tenho apenas um headset de áudio e quero usá-lo para área de trabalho e meu headset.

Se você tiver apenas um headset de áudio e não tiver um headset com fones de ouvido internos, conecte o headset de áudio ao PC host em vez do headset. Em seguida, desligue "alternar para áudio do headset" nas configurações do MRP.

### <a name="i-want-to-switch-to-dolby-atmos-for-headphones"></a>Quero mudar para o Dolby Atmos para fones de ouvido.

Os ambientes de realidade mista do Windows e seus aplicativos usam a tecnologia de áudio espacial do Windows Sonic para fone de ouvido que é personalizada para experiências de realidade misturada. Outras tecnologias espaciais de áudio, como o Dolby Atmos for fones de ouvido, podem ser aplicadas a aplicativos de tela inteira, como jogos SteamVR, mas não para os ambientes e aplicativos do Shell de realidade mista do Windows (como colocar um navegador da Web na parede da casa Cliff ou o céu loft) que foram projetados usando o Windows Sonic para sons espaciais e acústicos.


## <a name="questions-about-desktop-in-mixed-reality"></a>Perguntas sobre a área de trabalho em realidade misturada

### <a name="how-do-i-access-my-pc-desktop-in-mixed-reality"></a>Como fazer acessar minha área de trabalho de PC em realidade misturada?
Você pode acessar sua área de trabalho de PC em realidade misturada usando o aplicativo de desktop. Inicie-o no botão de fone de ouvido do **Windows > todos os aplicativos > área de trabalho** . 

### <a name="how-can-i-see-multiple-monitors-in-mixed-reality"></a>Como posso ver vários monitores em realidade misturada?
Por padrão, o aplicativo de desktop alterna automaticamente para exibir o monitor com foco. Se você quiser ver todos os monitores em realidade misturada: 
* Clique no ícone de monitor no canto superior esquerdo do aplicativo
* Desabilitar "alternar monitor automaticamente"
* Escolha o monitor que você deseja ver
* Iniciar outra instância do aplicativo de área de trabalho
* Escolha o monitor que você deseja ver nessa instância 
* Repita para todos os seus monitores físicos Observe que você precisará selecionar novamente o monitor para mostrar em cada aplicativo de desktop sempre que reiniciar a realidade misturada. 

### <a name="my-desktop-app-only-shows-a-black-screen"></a>Meu aplicativo de área de trabalho mostra apenas uma tela preta.
Se o seu computador tiver uma GPU híbrida Nvidia, o problema poderá ser causado pelo dispositivo NVIDIA executando o runtimebroker.exe na GPU discreta em vez de um integrado. Para corrigir esse problema, siga estas instruções em "[como fazer criar configurações de Optimus para um novo programa?](http://nvidia.custhelp.com/app/answers/detail/a_id/2615/~/how-do-i-customize-optimus-profiles-and-settings%3F)" para adicionar C:\windows\system32\runtimebroker.exe e forçá-lo a ser executado no processador "gráficos integrados". 


## <a name="other-questions"></a>Outras perguntas

### <a name="my-samsung-odyssey-or-odyssey-headset-firmware-update-is-getting-stuck"></a>Minha atualização do firmware Samsung Odyssey ou Odyssey + Headset está ficando presa.

A Samsung possui e publica as atualizações de firmware do headset fornecidas por meio de seus aplicativos de dispositivo "Samsung HMD Odyssey Setup" e "Samsung HMD Odyssey + Setup". Para obter mais detalhes e ajuda com problemas de atualização de firmware do Samsung, entre em contato com o atendimento ao cliente da Samsung.

Se o processo de atualização de firmware estiver travando e não houve progresso por mais de cinco minutos:
* Desconecte todos os outros dispositivos USB temporariamente e repita a atualização do firmware.
* Conecte seu headset Samsung a uma porta USB 3,0 diferente em seu PC.
* A desabilitação e/ou desinstalação de qualquer software instalado que possa interferir nas atualizações de firmware, como o AORUS da Gigabyte App Center.
* Use um computador diferente para executar a atualização de firmware do Samsung headset.

### <a name="my-wi-fi-slows-down-when-im-using-windows-mixed-reality"></a>Meu Wi-Fi fica lento quando estou usando a realidade mista do Windows.

Se você estiver usando uma conexão Wi-Fi de 2,4 GHz, seus controladores de movimento poderão retardar o Wi-Fi. Tente uma das seguintes opções:
* Mude para uma conexão Wi-Fi de 5 GHz, se houver uma disponível. [Saiba mais](https://support.microsoft.com/en-us/help/4000461).
* Use um adaptador Bluetooth separado para conectar seus controladores de movimento ao seu computador. Consulte [adaptadores recomendados](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines).

### <a name="i-got-a-message-that-said-to-plug-in-and-charge-my-pc-why"></a>Recebi uma mensagem que disse para conectar e encarregar meu PC. Por quê?

Se você estiver usando um laptop, a realidade mista do Windows funcionará melhor quando o PC for totalmente cobrado e conectado. 

### <a name="what-is-the-experience-options-setting"></a>O que é a configuração de opções de experiência?

A configuração opções de experiência ( **configurações > realidade misturada > exibição de fone de ouvido > opções de experiência** ) permite alterar as configurações de desempenho da realidade mista do Windows. Isso permite que você escolha a melhor experiência possível para sua configuração de hardware em uma variedade de conteúdo. A experiência do 90Hz está disponível para todos os sistemas, mas talvez você queira tentar automaticamente para ver qual configuração prefere. Aqui estão as opções:
* Automático: a realidade mista do Windows determinará a melhor experiência para sua configuração de hardware. Para a maioria das pessoas, essa é a melhor opção para começar.
* 60Hz: define a taxa de atualização para 60Hz e desativa determinados recursos, como captura de vídeo e visualização no portal de realidade misturada.
* 90Hz: define a taxa de atualização para 90Hz.

### <a name="what-languages-are-supported-in-windows-mixed-reality"></a>Quais idiomas têm suporte no Windows Mixed Reality?

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

O teclado da tela de realidade mista do Windows é inglês (Estados Unidos) apenas. Para inserir texto em outro idioma, use um teclado físico conectado ao seu PC. Você também pode usar o ditado em uma das linguagens de realidade mista do Windows listadas acima — Basta selecionar microfone no teclado da tela.

A realidade mista do Windows também está disponível nos seguintes idiomas sem comandos de fala ou recursos de ditado:

* Chinês tradicional (Taiwan e Hong Kong)
* Holandês (Países Baixos)
* Coreano (Coreia do Sul)
* Russo (Rússia)

### <a name="i-have-questions-about-my-headset-hardware"></a>Tenho dúvidas sobre o meu hardware de headset.

Para obter detalhes sobre o headset, verifique com o fabricante. Pode haver um guia de produto na caixa, ou você pode experimentar o site do fabricante.


## <a name="how-to-uninstall-windows-mixed-reality"></a>Como desinstalar a realidade mista do Windows

### <a name="how-do-i-uninstall-windows-mixed-reality"></a>Como fazer desinstalar o Windows Mixed Reality?

1. Desconecte o headset do seu PC.
2. Feche o portal de realidade misturada.
2. Vá para  **iniciar > configurações > realidade misturada** e selecione "Desinstalar".

Quando você estiver pronto para começar a usar o headset novamente, conecte-o e o portal de realidade mista o guiará pela instalação.

### <a name="i-got-a-we-couldnt-finish-uninstalling-windows-mixed-reality-message"></a>Recebi uma mensagem "não foi possível concluir a desinstalação do Windows Mixed Reality".

Isso significa que alguns arquivos, incluindo informações sobre seu ambiente, ainda podem estar no seu computador. Isso pode causar problemas se você decidir reinstalar o Windows Mixed Reality posteriormente. Você pode remover manualmente todas as informações restantes da realidade do Windows mista do seu computador, modificando o registro e usando o Windows PowerShell para executar comandos. _Se você modificar o registro incorretamente, poderão ocorrer problemas sérios. Certifique-se de seguir estas etapas com cuidado. Para proteção adicional, faça backup do registro antes de modificá-lo para que você possa restaurá-lo se um problema ocorrer._ Para obter mais informações, consulte [como fazer backup e reconstituir o registro no Windows](https://support.microsoft.com/en-us/help/322756/how-to-back-up-and-restore-the-registry-in-windows). 

Para desinstalar o Windows Mixed Reality usando estes comandos:
1. Reinicie o computador.
2. Na caixa de **pesquisa** , digite "regedit" e, em seguida, selecione **Sim** .
3. Remova os seguintes valores de registro:
   <ul>
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, em seguida, exclua <b>FirstRunSucceeded</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic\speechandaudio</b>, em seguida, exclua <b>PreferDesktopSpeaker</b> e <b>PreferDesktopMic</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\ Speech_OneCore &gt; Settings\Holographic</b>, em seguida, exclua <b>DisableSpeechInput</b>. Observação: os itens do registro no HHKEY_CURRENT_USER devem ser excluídos para cada conta de usuário no computador que usou a realidade mista do Windows.</li> 
    <li><b>HKEY_LOCAL_MACHINE \software\microsoft\windows\currentversion\perceptionsimulationextensions</b>, em seguida, exclua <b>DeviceID</b> e o <b>modo</b>.</li> 
    <li><b>HKEY_CURRENT_USER \software\microsoft\windows\currentversion\holographic</b>, em seguida, exclua <b>OnDeviceLearningCompleted</b>.</li> 
   </ul>
4. Remova as seguintes chaves do registro: <ul>
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_LOCAL_MACHINE \Software\Microsoft\Windows\CurrentVersion\HoloSI</b></li> 
   <li> <b>HKEY_CURRENT_USER \Software\Microsoft\ Speech_OneCore \Settings\HolographicPreferences</b></li><br/></ul>
5. Feche o editor do registro.
6. Navegue até **C:\Users\user name\appdata\local\packages\ Microsoft.Windows.HolographicFirstRun_cw5n1h2txyewy \localstate** e exclua **RoomBounds.jsem** . Repita isso para cada usuário que usou a realidade mista do Windows.
7. Abra o prompt do administrador CMD e navegue até **C:\ProgramData\WindowsHolographicDevices\SpatialStore\HoloLensSensors** . Em seguida, exclua o conteúdo da pasta de **dados HeadTracking** (mas não a pasta em si).
8. Digite "PowerShell" na **caixa de pesquisa** , clique com o botão direito do mouse em **Windows PowerShell** e selecione **Executar como administrador** .
9. No Windows PowerShell, faça o seguinte: <ul>
   <li>Copie e cole o seguinte no prompt de comando e pressione ENTER: <b>DISM/online/Get-Capabilities</b></li> 
   <li>Copie a identidade de recurso que começa com Analog. Holographic. desktop (se não&#39;t, isso significa que esse item não&#39;está instalado. Nesse caso, pule para a etapa 10).</li> 
   <li>Copie e cole o seguinte prompt de comando e pressione ENTER: <b>DISM/online/remove-Capability/CapabilityName: a identidade de recurso copiada na última etapa</b></li>
   </ul>
10. Reinicie o computador.




