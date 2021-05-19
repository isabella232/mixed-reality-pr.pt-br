---
title: Perguntas frequentes sobre conectividade de headset
description: Conectividade do headset Windows Mixed Reality solução de problemas de conectividade do headset que vai além da nossa documentação de suporte ao consumidor padrão.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Solução de Problemas, Erros, Ajuda, Suporte, Headset
appliesto:
- Windows 10
ms.openlocfilehash: 2d46275fd86eedbe93a81bc97c156f29794e8c42
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143238"
---
# <a name="headset-connectivity-faqs"></a>Perguntas frequentes sobre conectividade de headset

## <a name="my-headset-will-not-wake-up"></a>Meu Headset não será a wake up

Se o headset estiver inocligado e clicar no botão de a wake up não funcionar, reinicie o computador.

## <a name="my-computer-does-not-have-an-hdmi-andor-display-port"></a>Meu computador não tem um HDMI e/ou porta de exibição

Talvez seja necessário usar um adaptador. Acesse [aqui](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para ver uma lista de adaptadores com suporte.

## <a name="can-i-use-usb-or-hdmi-andor-displayport-extension-cables-with-windows-mixed-reality-headsets"></a>Posso usar cabos de extensão USB ou HDMI e/ou DisplayPort com Windows Mixed Reality headsets

Windows Mixed Reality headsets não são oficialmente compatíveis com o uso de cabos de extensão USB, HDMI ou DisplayPort. Se você estiver usando esses cabos, a experiência de Realidade Misturada poderá ser afetada devido a variações na integridade do sinal e na energia do barramento entre o controlador USB do computador e o headset de Realidade Misturada. Tente usar o headset sem cabos de extensão se:

* A exibição do headset mostra brevemente uma tela azul e, em seguida, fica preta e Portal de Realidade Misturada é reiniciada ou completamente des enumerada durante o uso
* O áudio do headset corta ou se torna uma falha
* O headset pisca entre preto e a exibição correta

## <a name="i-am-getting-a-check-your-display-cable-error"></a>Estou recebendo um erro "Verificar o cabo de exibição"

* Se você estiver usando adaptadores para conectar seu headset ao computador, certifique-se de que eles sejam compatíveis com Windows Mixed Reality e sejam compatíveis com 4K. Tente também conectar o adaptador ao computador antes de conectar o headset ao adaptador.
* Tente usar uma porta HDMI ou DisplayPort diferente.
* Conecte seu headset a um DisplayPort 1,2 ou posterior, ou HDMI 1,4 ou posterior. Verifique se a porta corresponde à placa gráfica mais avançada em seu computador.
* Se o seu PC tiver gráficos integrados e discretos, verifique se você está usando a porta HDMI ou DisplayPort na placa gráfica ativa. Isso pode significar que você precisará conectar a exibição do seu PC a uma porta não HDMI.
* Se o seu PC tiver gráficos integrados e discretos, e os gráficos integrados forem mais antigos e não oferecerem suporte à realidade mista do Windows, tente desabilitar a GPU integrada.
* Conecte um monitor de PC à porta HDMI ou DisplayPort do seu PC. Verifique se os drivers gráficos estão atualizados. Baixe e instale os drivers diretamente do AMD, Nvidia ou Intel, pois eles provavelmente serão mais recentes do que o que foi publicado para Windows Update.
* Se você tiver um monitor externo conectado a uma porta HDMI, tente conectá-lo em um DisplayPort em vez disso e use a porta HDMI para o headset.
* Certifique-se de que você conectou o cabo HDMI do headset em uma porta "HDMI" em seu PC, e não uma porta "HDMI in".
* O Windows pode não conseguir detectar a conexão do cabo de vídeo. Abra o Gerenciador de Dispositivos e veja se o headset está listado em "monitores". Caso contrário, selecione **ação > verificar se há alterações de hardware**.

## <a name="a-message-says-put-on-your-headset-but-i-have-my-headset-on"></a>Uma mensagem diz "Put on the headset", mas tenho meu Headset em

Quando você coloca em seu headset, a realidade mista do Windows pode precisar de alguns segundos para recarregar seu espaço. Se essa mensagem não desaparecer, verifique se o adesivo de proteção foi removido do sensor de proximidade no interior do headset entre as lentes. Entre em contato com seu fabricante de headset se o problema persistir.

## <a name="a-message-says-connect-your-headset-but-ive-plugged-in-my-headset"></a>Uma mensagem diz "conectar seu headset", mas eu me conectei ao meu Headset

- Verifique se os cabos USB e HDMI ou DisplayPort do headset estão conectados às portas corretas no seu PC. Veja como identificar as portas corretas:

    - As portas USB 3.0 têm um logotipo especial com uma marca "SS" (indicando "SuperSpeed"). A parte interna da porta normalmente é azul, mas as portas USB 2.0 mais antigas normalmente são pretas ou brancas por dentro.
    - Se o computador tiver duas portas HDMI ou DisplayPort, use aquela que se conecta à placa gráfica, não à placa-mãe do computador. Nem sempre é óbvio, que é que, embora portas discretas geralmente estão localizadas em um slot de expansão no computador. Se você tentar uma porta e ela não funcionar, tente a outra.

- Desconectar e conectar os cabos USB e HDMI ou DisplayPort do headset para garantir que eles estão conectados com segurança. Ao conectar o cabo USB, tente não pausar durante a inserção do cabo USB.
- Experimente um hub USB 3.0 externo se você estiver vendo a enumeração parcial do headset, por exemplo, uma série de dispositivos USB enumerar, mas nada em "headsets de Realidade Misturada" no Gerenciador de Dispositivos.
- Acesse o site do fabricante do headset e atualize os drivers e o firmware do headset.
- Conecte o headset a outro computador e abra o Gerenciador de Dispositivos. Mesmo que esse computador não seja totalmente compatível com Windows Mixed Reality, você poderá verificar se o headset é enumerado. Se o headset não for enumerado em vários PCs, ele poderá ter um problema de hardware.

> [!NOTE]
> Para usuários do Surface: as versões anteriores do Surface Dock e Surface Book de atualização de firmware do Hub USB são incompatíveis com headsets de Realidade Misturada. Se você receber uma mensagem "Conectar seu headset" em um computador Surface, verifique se algum dispositivo está relatando um erro "Código 10: o dispositivo não pode iniciar" no Gerenciador de Dispositivos. Em caso afirmado, [remova o driver conflitante.](https://support.microsoft.com/en-us/help/4032123/kinect-sensor-is-not-recognized-on-a-surface-book) Você só deve precisar fazer isso uma vez.

Observação para usuários Windows 10-N: se o computador estiver executando o Windows 10 N, você verá um erro "Código 28: A classe de instalação não está presente ou é inválida" no Gerenciador de Dispositivos depois de conectar o headset de Realidade Misturada. N edições de Windows 10 não são suportadas pelo Windows Mixed Reality. Siga estas [instruções](headset-display.md#im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager) para obter mais informações.

## <a name="a-message-says-check-your-usb-cable-or-insufficient-usb-speed"></a>Uma mensagem diz "verificar o cabo USB" ou "velocidade de USB insuficiente"

* Verifique se você está usando uma porta USB 3,0 com suporte em seu PC:

    * Certifique-se de que o cabo USB do headset esteja conectado.
    * Execute o [portal do Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) para verificar se há suporte para o controlador USB 3,0 do seu PC.
    * Conecte seu headset às outras portas USB 3,0 em seu PC. Alguns PCs têm mais de um controlador USB 3,0.
    * Desconecte temporariamente todos os dispositivos USB conectados ao seu PC e conecte-se somente ao headset.
    * Em computadores personalizados, embora uma porta possa ser marcada como uma porta USB 3,0, ela pode estar conectada a um controlador USB 2,0. Com o fone de ouvido conectado, abra Gerenciador de Dispositivos, localize e clique único em qualquer um dos dispositivos enumerados de seu headset, em seguida, vá para **exibir > dispositivos por conexão**.
* Experimente o headset em outro PC. Se esse outro PC não for totalmente compatível com a realidade mista do Windows, faça check-in Gerenciador de Dispositivos para ver se você vê a mensagem "velocidade de USB insuficiente". Se ele não for enumerado corretamente em vários PCs, o headset poderá estar com defeito.
* Remova todos os extensores ou hubs entre o headset e o computador.

## <a name="the-mixed-reality-portal-did-not-launch-after-i-plugged-in-my-headset"></a>O portal de realidade misturada não foi iniciado depois que eu me conectei ao meu Headset

O headset pode não ter sido detectado corretamente devido a um problema subjacente. Inicie o portal de realidade misturada manualmente e procure as mensagens de erro que aparecem.

## <a name="my-headset-stopped-working-when-my-pc-goes-into-sleep-or-hibernation-mode-or-when-restarting-my-pc-with-my-headset-attached"></a>Meu Headset parou de funcionar quando meu PC entra no modo de suspensão ou hibernação ou ao reiniciar meu PC com meu Headset anexado

1. Abra Gerenciador de Dispositivos e confirme se o headset está listado em "dispositivos de realidade misturada".
2. Selecione o headset em "dispositivos com realidade misturada" e confirme se o status do dispositivo indica "este dispositivo está funcionando corretamente".
3. Se você vir um erro de "código 43" dizendo que o dispositivo parou de funcionar, ou se você não vir o headset listado em "dispositivos de realidade misturada", desconecte e reconecte o cabo USB do headset. A Microsoft está investigando um possível problema de interoperabilidade de software/driver, o que pode resultar nesse erro. Esse problema afeta um pequeno número de PCs e deve ser resolvido em uma atualização futura para o driver de headset de Realidade Misturada.

## <a name="my-headset-causes-my-pc-to-generate-a-bug-check-blue-screen-when-i-put-my-pc-to-sleep-or-when-it-is-in-hibernation-mode"></a>Meu headset faz com que meu computador gere uma Verificação de Bug (tela azul) quando eu colocar meu computador em espera ou quando ele estiver no modo de hibernação

Certifique-se de que você está no driver 10.0.19041.2034 ou mais novo.

## <a name="the-headset-driver-did-not-install-automatically-when-i-plugged-in-the-headset"></a>O driver do headset não foi instalado automaticamente quando eu conectei o headset

Em novos computadores ou computadores com uma cópia recém-instalada do Windows 10, o driver do headset pode ser enxuado atrás de outras atualizações do Windows e não pode ser instalado imediatamente.

1. Vá para **Iniciar > Gerenciador de Dispositivos** e procure em "Dispositivos de Realidade Misturada" para seu headset. O status do dispositivo deve indicar que "O dispositivo está funcionando corretamente".
2. Clique com o botão direito do mouse no dispositivo e selecione "Atualizar driver".

Se isso não funcionar, tente desinstalar o driver:

1. Vá para **Iniciar > Gerenciador de Dispositivos** e procure em "Dispositivos de Realidade Misturada" para seu headset. O status do dispositivo deve indicar que "O dispositivo está funcionando corretamente".
2. Clique com o botão direito do mouse no dispositivo e selecione "Desinstalar Dispositivo".
3. No novo pop-up exibido, marque a caixa de seleção "Excluir o software do driver para este dispositivo" e selecione "Desinstalar".
4. Quando isso for concluído, desconectar o headset do computador e conecte-o novamente. Windows Update baixará e instalará um novo driver.

Observação: se você tiver uma N edição do Windows, precisará alternar para uma edição regular do Windows 10 para usar Windows Mixed Reality.