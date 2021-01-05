---
title: Perguntas frequentes sobre conectividade com Headset
description: Conectividade de fone de ouvido Windows Mixed Reality fone de problemas de conectividade que vai além da nossa documentação de suporte de consumidor padrão.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, solução de problemas, erros, ajuda, suporte, headset
appliesto:
- Windows 10
ms.openlocfilehash: f42994561d032245f4f0345ad494eb38015f3682
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725587"
---
# <a name="headset-connectivity-faqs"></a>Perguntas frequentes sobre conectividade com Headset

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Meu computador não tem um HDMI e/ou uma porta de exibição

Talvez seja necessário usar um adaptador. Acesse [aqui](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para obter uma lista de adaptadores com suporte.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Posso usar cabos de extensão USB ou HDMI e/ou DisplayPort com headsets de realidade mista do Windows

Os headsets de realidade mista do Windows não suportam oficialmente o uso de cabos de extensão USB, HDMI ou DisplayPort. Se você estiver usando esses cabos, a experiência de realidade misturada poderá ser afetada devido a variações na integridade do sinal e na potência do barramento entre o controlador USB do PC e o headset da realidade misturada. Tente usar o headset sem cabos de extensão se:
* A tela de fone de ouvido mostra resumidamente um ecrã azul e, em seguida, transforma as reinicializações do portal de realidade em preto e misto ou as enumerações completamente durante o uso
* O áudio do headset é retirado ou se torna um problema
* Os movimentos de headset entre preto e a exibição correta

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Estou recebendo um erro "verificar o cabo de vídeo"

* Se você estiver usando qualquer adaptador para conectar seu headset ao seu PC, verifique se eles dão suporte à realidade mista do Windows e têm capacidade de 4K. Além disso, tente conectar o adaptador ao PC antes de conectar o headset ao adaptador.
* Tente usar uma porta HDMI ou DisplayPort diferente.
* Conecte seu headset a um DisplayPort 1,2 ou posterior, ou HDMI 1,4 ou posterior. Verifique se a porta corresponde à placa gráfica mais avançada em seu computador.
* Se o seu PC tiver gráficos integrados e discretos, verifique se você está usando a porta HDMI ou DisplayPort na placa gráfica ativa. Isso pode significar que você precisará conectar a exibição do seu PC a uma porta não HDMI.
* Se o seu PC tiver gráficos integrados e discretos, e os gráficos integrados forem mais antigos e não oferecerem suporte à realidade mista do Windows, tente desabilitar a GPU integrada.
* Conecte um monitor de PC à porta HDMI ou DisplayPort do seu PC. Verifique se os drivers gráficos estão atualizados. Baixe e instale os drivers diretamente do AMD, Nvidia ou Intel, pois eles provavelmente serão mais recentes do que o que foi publicado para Windows Update.
* Se você tiver um monitor externo conectado a uma porta HDMI, tente conectá-lo em um DisplayPort em vez disso e use a porta HDMI para o headset.
* Certifique-se de que você conectou o cabo HDMI do headset em uma porta "HDMI" em seu PC, e não uma porta "HDMI in".
* O Windows pode não conseguir detectar a conexão do cabo de vídeo. Abra o Device Manager e veja se o headset está listado em "monitores". Caso contrário, selecione **ação > verificar se há alterações de hardware**. 

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Uma mensagem diz "Put on the headset", mas tenho meu Headset em

Quando você coloca em seu headset, a realidade mista do Windows pode precisar de alguns segundos para recarregar seu espaço. Se essa mensagem não desaparecer, verifique se o adesivo de proteção foi removido do sensor de proximidade no interior do headset entre as lentes. Entre em contato com seu fabricante de headset se o problema persistir.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Uma mensagem diz "conectar seu headset", mas eu me conectei ao meu Headset

- Verifique se os cabos USB e HDMI ou DisplayPort do headset estão conectados às portas corretas no seu PC. Veja como identificar as portas corretas:

    - As portas USB 3,0 têm um logotipo especial com uma marca "SS" (indicando "SuperSpeed"). A parte interna da porta é normalmente azul, mas as portas USB 2,0 mais antigas geralmente são pretas ou brancas no interior.
    - Se o computador tiver duas portas HDMI ou DisplayPort, use aquela que se conecta à placa gráfica, não à placa-mãe do computador. Nem sempre é óbvio, que, embora as portas discretas estejam localizadas com freqüência em um slot de expansão no computador. Se você tentar uma porta e ela não funcionar, tente a outra.

- Desconecte e conecte os cabos USB e HDMI ou DisplayPort do headset para garantir que eles estejam conectados com segurança. Ao conectar-se ao cabo USB, tente não pausar durante a inserção do cabo USB.
- Experimente um hub USB 3,0 ligado externamente se você estiver vendo a enumeração parcial do headset, por exemplo, uma série de dispositivos USB enumerar, mas nada em "a realidade misturada headsets" em Device Manager.
- Acesse o site do fabricante do headset e atualize os drivers e o firmware do headset.
- Conecte seu headset a outro computador e abra Device Manager. Mesmo que esse PC não seja totalmente compatível com a realidade mista do Windows, você pode verificar se o fone de ouvido é enumerado. Se o headset não enumerar em vários PCs, ele poderá ter um problema de hardware.

> [!NOTE]
> Para usuários de superfície: as versões anteriores dos softwares de atualização de firmware de Hub USB de encaixe de superfície e de superfície são incompatíveis com headsets de realidade misturada. Se você receber uma mensagem "conectar seu headset" em um PC de superfície, verifique se algum dispositivo está relatando um erro "código 10: o dispositivo não pode iniciar" em Device Manager. Nesse caso, [remova o driver conflitante](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Você só precisa fazer isso uma vez.

Observação para usuários do Windows 10-N: se o seu computador estiver executando o Windows 10 N, você verá um erro "código 28: a classe de instalação não está presente ou é inválido" em Device Manager depois de conectar seu headset de realidade misturada. N edições do Windows 10 não são suportadas pela realidade mista do Windows. Siga estas [instruções](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) para obter mais informações.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Uma mensagem diz "verificar o cabo USB" ou "velocidade de USB insuficiente"

* Verifique se você está usando uma porta USB 3,0 com suporte em seu PC:

    * Certifique-se de que o cabo USB do headset esteja conectado.
    * Execute o [portal do Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) para verificar se há suporte para o controlador USB 3,0 do seu PC.
    * Conecte seu headset às outras portas USB 3,0 em seu PC. Alguns PCs têm mais de um controlador USB 3,0.
    * Desconecte temporariamente todos os dispositivos USB conectados ao seu PC e conecte-se somente ao headset.
    * Em computadores personalizados, embora uma porta possa ser marcada como uma porta USB 3,0, ela pode estar conectada a um controlador USB 2,0. Com o fone de ouvido conectado, abra Device Manager, localize e clique único em qualquer um dos dispositivos enumerados de seu headset, em seguida, vá para **exibir > dispositivos por conexão**.
* Experimente o headset em outro PC. Se esse outro PC não for totalmente compatível com a realidade mista do Windows, faça check-in Device Manager para ver se você vê a mensagem "velocidade de USB insuficiente". Se ele não for enumerado corretamente em vários PCs, o headset poderá estar com defeito.
* Remova todos os extensores ou hubs entre o headset e o computador.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>O portal de realidade misturada não foi iniciado depois que eu me conectei ao meu Headset

O headset pode não ter sido detectado corretamente devido a um problema subjacente. Inicie o portal de realidade misturada manualmente e procure as mensagens de erro que aparecem.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Meu Headset parou de funcionar quando meu PC entra no modo de suspensão ou hibernação ou ao reiniciar meu PC com meu Headset anexado

1. Abra Device Manager e confirme se o headset está listado em "dispositivos de realidade misturada".
2. Selecione o headset em "dispositivos com realidade misturada" e confirme se o status do dispositivo indica "este dispositivo está funcionando corretamente".
3. Se você vir um erro de "código 43" dizendo que o dispositivo parou de funcionar, ou se você não vir o headset listado em "dispositivos de realidade misturada", desconecte e reconecte o cabo USB do headset. A Microsoft está investigando um problema potencial de interoperabilidade de software/driver, o que pode resultar nesse erro. Esse problema afeta um pequeno número de computadores e deve ser resolvido em uma atualização futura para o driver de headset de realidade misturada.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Meu Headset faz com que meu computador gere uma verificação de bug (tela azul) quando coloco meu computador em suspensão ou quando ele está no modo de hibernação

Verifique se você está no driver 10.0.19041.2034 ou mais recente.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>O driver Headset não foi instalado automaticamente quando eu conectei o headset

Em novos computadores ou PCs com uma cópia recém-instalada do Windows 10, o driver de headset pode ser enfileirado por trás de outras atualizações do Windows e pode não ser instalado imediatamente.

1. Acesse **iniciar > Device Manager** e procure "dispositivos de realidade misturada" para o headset. O status do dispositivo deve indicar que "o dispositivo está funcionando corretamente".
2. Clique com o botão direito do mouse no dispositivo e selecione "Atualizar driver".

Se isso não funcionou, tente desinstalar o driver:

1. Acesse **iniciar > Device Manager** e procure "dispositivos de realidade misturada" para o headset. O status do dispositivo deve indicar que "o dispositivo está funcionando corretamente".
2. Clique com o botão direito do mouse no dispositivo e selecione "desinstalar dispositivo".
3. No novo pop-up que aparece, marque a caixa de seleção "excluir o software de driver para este dispositivo" e, em seguida, selecione "Desinstalar".
4. Quando isso for concluído, desconecte o headset do seu PC e conecte-o novamente. Windows Update agora vai baixar e instalar um novo driver.

Observação: se você tiver uma edição N do Windows, precisará alternar para uma edição regular do Windows 10 para usar a realidade mista do Windows.