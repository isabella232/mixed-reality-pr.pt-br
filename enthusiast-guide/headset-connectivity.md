---
title: Perguntas frequentes sobre conectividade com Headset
description: a conectividade do headset Windows Mixed Reality a solução de problemas de conectividade do headset que vai além da nossa documentação de suporte padrão do consumidor.
author: qianwen
ms.author: v-qianwen
ms.date: 09/30/2021
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, MR, solução de problemas, erros, ajuda, suporte, Headset
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: 47c726c5beeac0463fe4286bd7a949e4e4d4cc45
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436606"
---
# <a name="headset-connectivity-faqs"></a>Perguntas frequentes sobre conectividade com Headset

## <a name="my-headset-will-not-wake-up"></a>Meu Headset não será ativado

Se o headset estiver em suspensão e clicar no botão acordar não funcionar, reinicie o computador.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Meu computador não tem um HDMI e/ou uma porta de exibição

Talvez seja necessário usar um adaptador. Acesse [aqui](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para obter uma lista de adaptadores com suporte.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>posso usar cabos de extensão USB ou HDMI e/ou DisplayPort com Windows Mixed Reality headsets

Windows Mixed Reality headsets não dão suporte oficialmente ao uso de cabos de extensão USB, HDMI ou DisplayPort. Se você estiver usando esses cabos, a experiência de realidade misturada poderá ser afetada devido a variações na integridade do sinal e na potência do barramento entre o controlador USB do PC e o headset da realidade misturada. Tente usar o headset sem cabos de extensão se:

* A tela de fone de ouvido mostra resumidamente um ecrã azul e, em seguida, transforma as reinicializações do portal de realidade em preto e misto ou as enumerações completamente durante o uso
* O áudio do headset é retirado ou se torna um problema
* Os movimentos de headset entre preto e a exibição correta

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Estou recebendo um erro "verificar o cabo de vídeo"

* se você estiver usando qualquer adaptador para conectar seu headset ao seu PC, verifique se eles dão suporte a Windows Mixed Reality e têm capacidade de 4k. Além disso, tente conectar o adaptador ao PC antes de conectar o headset ao adaptador.
* Tente usar uma porta HDMI ou DisplayPort diferente.
* Conexão o headset a um DisplayPort 1,2 ou posterior, ou HDMI 1,4 ou posterior. Verifique se a porta corresponde à placa gráfica mais avançada em seu computador.
* Se o seu PC tiver gráficos integrados e discretos, verifique se você está usando a porta HDMI ou DisplayPort na placa gráfica ativa. Isso pode significar que você precisará conectar a exibição do seu PC a uma porta não HDMI.
* se o seu PC tiver gráficos integrados e discretos e os gráficos integrados forem mais antigos e não oferecer suporte a Windows Mixed Reality, tente desabilitar a GPU integrada.
* Conexão um monitor de pc à porta HDMI ou DisplayPort do seu pc. Verifique se os drivers gráficos estão atualizados. baixe e instale os drivers diretamente do AMD, Nvidia ou Intel, pois eles provavelmente serão mais recentes do que o que foi publicado para Windows Update.
* Se você tiver um monitor externo conectado a uma porta HDMI, tente conectá-lo em um DisplayPort em vez disso e use a porta HDMI para o headset.
* Certifique-se de que você conectou o cabo HDMI do headset em uma porta "HDMI" em seu PC, e não uma porta "HDMI in".
* Windows pode não conseguir detectar a conexão do cabo de vídeo. Abra o Gerenciador de Dispositivos e veja se o headset está listado em "monitores". Caso contrário, selecione **ação > verificar se há alterações de hardware**.

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Uma mensagem diz "Put on the headset", mas tenho meu Headset em

quando você coloca em seu headset, Windows Mixed Reality pode precisar de alguns segundos para recarregar seu espaço. Se essa mensagem não desaparecer, verifique se o adesivo de proteção foi removido do sensor de proximidade no interior do headset entre as lentes. Entre em contato com seu fabricante de headset se o problema persistir.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>uma mensagem diz "Conexão seu headset", mas eu me conectei ao meu headset

- Verifique se os cabos USB e HDMI ou DisplayPort do headset estão conectados às portas corretas no seu PC. Veja como identificar as portas corretas:

    - As portas USB 3,0 têm um logotipo especial com uma marca "SS" (indicando "SuperSpeed"). A parte interna da porta é normalmente azul, mas as portas USB 2,0 mais antigas geralmente são pretas ou brancas no interior.
    - Se o computador tiver duas portas HDMI ou DisplayPort, use aquela que se conecta à placa gráfica, não à placa-mãe do computador. Nem sempre é óbvio, que, embora as portas discretas estejam localizadas com freqüência em um slot de expansão no computador. Se você tentar uma porta e ela não funcionar, tente a outra.

- Desconecte e conecte os cabos USB e HDMI ou DisplayPort do headset para garantir que eles estejam conectados com segurança. Ao conectar-se ao cabo USB, tente não pausar durante a inserção do cabo USB.
- Experimente um hub USB 3,0 ligado externamente se você estiver vendo a enumeração parcial do headset, por exemplo, uma série de dispositivos USB enumerar, mas nada em "a realidade misturada headsets" em Gerenciador de Dispositivos.
- Acesse o site do fabricante do headset e atualize os drivers e o firmware do headset.
- Conexão o headset a outro computador e abra Gerenciador de Dispositivos. mesmo que o computador não seja totalmente compatível com Windows Mixed Reality, você pode verificar se o headset é enumerado. Se o headset não enumerar em vários PCs, ele poderá ter um problema de hardware.

> [!NOTE]
> para usuários do surface: as versões anteriores do encaixe de superfície e Surface Book software de atualização de firmware do Hub USB são incompatíveis com headsets de realidade misturada. se você receber uma mensagem "Conexãondo o headset" em um PC de superfície, verifique se algum dispositivo está relatando um erro "código 10: o dispositivo não pode iniciar" em Gerenciador de Dispositivos. Nesse caso, [remova o driver conflitante](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book). Você só precisa fazer isso uma vez.

observação para os usuários Windows 10-n e Windows 11-n: se o seu computador estiver executando Windows 10-n ou Windows 11-n, você verá um erro "código 28: a classe de instalação não está presente ou é inválido" em Gerenciador de Dispositivos depois de conectar seu headset de realidade misturada. as edições N do Windows 10 e do Windows 11 não são suportadas pelo Windows Mixed Reality. Siga estas [instruções](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) para obter mais informações.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Uma mensagem diz "verificar o cabo USB" ou "velocidade de USB insuficiente"

* Verifique se você está usando uma porta USB 3,0 com suporte em seu PC:

    * Certifique-se de que o cabo USB do headset esteja conectado.
    * execute o [Portal de Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) para verificar se há suporte para o controlador USB 3,0 do computador.
    * Conexão o headset às outras portas USB 3,0 em seu PC. Alguns PCs têm mais de um controlador USB 3,0.
    * Desconecte temporariamente todos os dispositivos USB conectados ao seu PC e conecte-se somente ao headset.
    * Em computadores personalizados, embora uma porta possa ser marcada como uma porta USB 3,0, ela pode estar conectada a um controlador USB 2,0. Com o fone de ouvido conectado, abra Gerenciador de Dispositivos, localize e clique único em qualquer um dos dispositivos enumerados de seu headset, em seguida, vá para **exibir > dispositivos por conexão**.
* Experimente o headset em outro PC. se esse computador não for totalmente compatível com Windows Mixed Reality, consulte Gerenciador de Dispositivos para ver se você vê a mensagem "velocidade de USB insuficiente". Se ele não for enumerado corretamente em vários PCs, o headset poderá estar com defeito.
* Remova todos os extensores ou hubs entre o headset e o computador.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>O portal de realidade misturada não foi iniciado depois que eu me conectei ao meu Headset

O headset pode não ter sido detectado corretamente devido a um problema subjacente. Inicie o portal de realidade misturada manualmente e procure as mensagens de erro que aparecem.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Meu Headset parou de funcionar quando meu PC entra no modo de suspensão ou hibernação ou ao reiniciar meu PC com meu Headset anexado

1. Abra Gerenciador de Dispositivos e confirme se o headset está listado em "dispositivos de realidade misturada".
2. Selecione o headset em "dispositivos com realidade misturada" e confirme se o status do dispositivo indica "este dispositivo está funcionando corretamente".
3. Se você vir um erro de "código 43" dizendo que o dispositivo parou de funcionar, ou se você não vir o headset listado em "dispositivos de realidade misturada", desconecte e reconecte o cabo USB do headset. A Microsoft está investigando um problema potencial de interoperabilidade de software/driver, o que pode resultar nesse erro. Esse problema afeta um pequeno número de computadores e deve ser resolvido em uma atualização futura para o driver de headset de realidade misturada.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Meu Headset faz com que meu computador gere uma verificação de bug (tela azul) quando coloco meu computador em suspensão ou quando ele está no modo de hibernação

Verifique se você está no driver 10.0.19041.2034 ou mais recente.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>O driver Headset não foi instalado automaticamente quando eu conectei o headset

em novos computadores ou pcs com uma cópia recentemente instalada de Windows 10 ou Windows 11, o driver de headset pode ser enfileirado por trás de outras atualizações de Windows e pode não ser instalado imediatamente.

1. Acesse **iniciar > Gerenciador de dispositivos** e procure "dispositivos de realidade misturada" para o headset. O status do dispositivo deve indicar que "o dispositivo está funcionando corretamente".
2. Clique com o botão direito do mouse no dispositivo e selecione "Atualizar driver".

Se isso não funcionou, tente desinstalar o driver:

1. Acesse **iniciar > Gerenciador de dispositivos** e procure "dispositivos de realidade misturada" para o headset. O status do dispositivo deve indicar que "o dispositivo está funcionando corretamente".
2. Clique com o botão direito do mouse no dispositivo e selecione "desinstalar dispositivo".
3. No novo pop-up que aparece, marque a caixa de seleção "excluir o software de driver para este dispositivo" e, em seguida, selecione "Desinstalar".
4. Quando isso for concluído, desconecte o headset do seu PC e conecte-o novamente. Windows Agora, a atualização baixará e instalará um novo driver.

observação: se você tiver uma edição N do Windows, será necessário alternar para uma edição regular do Windows 10 ou Windows 11 para usar Windows Mixed Reality.