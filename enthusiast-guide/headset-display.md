---
title: Perguntas frequentes sobre a exibição do headset
description: Exibir Windows Mixed Reality solução de problemas de exibição do headset que vão além da nossa documentação de suporte ao consumidor padrão.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Solução de Problemas, Erros, Ajuda, Suporte
appliesto:
- Windows 10
ms.openlocfilehash: 811b5160c739c8b19fde737e7a61bcef84e0cf60a87927adbe21241e229f3f22
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189381"
---
# <a name="headset-display-faqs"></a>Perguntas frequentes sobre a exibição do headset

## <a name="my-headset-displays-are-black"></a>As exibições do meu headset são pretas

* Verifique o desempenho e a estabilidade do computador:
    * Use o Gerenciador de Tarefas para ver se algum processo está maxing out out your PC's CPU, GPU ou disk drives.
    * Verifique os logs "Aplicativo" e "Sistema" **Visualizador de Eventos > Windows logs** para ver se um aplicativo está falhando e gerando relatórios Relatório de Erros do Windows (WER).
    * Verifique Windows Atualizar para verificar se sua versão do Windows está atual. Talvez seja preciso selecionar "Verificar atualizações" várias vezes.
* Verifique a estabilidade do aplicativo e do jogo:
    * Verifique se o computador atende aos requisitos mínimos do sistema de qualquer aplicativo ou jogo que não está sendo executado corretamente.
    * Verifique se a versão do driver gpu é recente e verifique se há novos problemas de desempenho e compatibilidade e regressões em novos drivers.
    * Se você estiver usando aplicativos e jogos Do SteamVR, certifique-se de que o SteamVR e Windows Mixed Reality componentes do SteamVR estão atualizados.
* Verifique a compatibilidade do adaptador HDMI:
    * Certifique-se de que o cabo HDMI esteja conectado o tempo todo.
    * Se você estiver usando um adaptador HDMI (por exemplo, um Mini DisplayPort para adaptador HDMI), certifique-se de que ele seja compatível com Windows Mixed Reality. O adaptador deve dar suporte ao HDMI 2.0 e há muitos adaptadores mais antigos que só suportam 1080p. Consulte [Adaptadores recomendados para Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * A ordem de plug pode ser importante. Conexão adaptador HDMI ao computador antes de conectar o headset ao adaptador, especialmente se você estiver usando um adaptador USB-C para HDMI.
    * Tente remover cabos de extensão se você estiver usando-os.
* Verifique a compatibilidade do driver e da placa gráfica:
    * Experimente a porta HDMI do computador com um monitor de computador. Alguns PCs podem ter mais de uma porta HDMI e nem todos eles podem estar ativos.
    * Se o computador tiver uma iGPU (unidade de processamento gráfico) integrada e uma dGPU (unidade de processamento gráfico discreto), certifique-se de que você está conectado à porta HDMI da DGPU.
    * Verifique a versão do driver de GPU. Certifique-se de que seja recente, mas também preste atenção a novos problemas de desempenho e compatibilidade e regressões em drivers novos.
    * Se você estiver usando a Realidade Misturada em um laptop e tiver instalado um driver gráfico mais recente do site do fabricante da placa gráfica, tente fazer downgrade para o driver de placa gráfica mais recente fornecido no site do fabricante do computador ou no Windows Update.
    * Se você tiver vários monitores de computadores conectados ao computador, tente desconectar temporariamente todos, menos um monitor de computador.
    * Se você tiver definido uma taxa de atualização personalizada para o monitor do computador, tente reverter temporariamente para uma taxa de atualização padrão, como 60 Hz.
    * Se você alterou recentemente sua placa gráfica sem reinstalar Windows, verifique se o monitor do headset ainda tem o driver correto instalado. Com o headset conectado, confirme se o "headset de Realidade Misturada" está listado no nó Monitores no Gerenciador de Dispositivos.
    * Se o computador tiver uma placa gráfica Nvidia, certifique-se de que o software de Visão 3D da Nvidia está desabilitado.
    * Em algumas placas gráficas (especialmente cartões mais antigos), a porta HDMI pode não dar suporte ao HDMI 2.0 ou pode não ser totalmente compatível com Windows Mixed Reality. Tente usar o DisplayPort da sua placa gráfica com um [adaptador DisplayPort 1.2 para HDMI 2.0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
    * Os PCs hp Omen com o número do produto HP 1RJ99EA#SEMPRE têm portas HDMI incompatíveis com o Windows Mixed Reality (abra o "Assistente de Suporte HP" e o número será listado na parte inferior do aplicativo).
    * Se o computador tiver uma placa gráfica da série AMD R9 e você estiver usando um headset samsung Mixed Reality, atualize o firmware do headset para a versão 1.0.8 ou mais recente para usar a porta HDMI da sua placa gráfica com o headset.
    * Se você estiver usando um Surface Book 2, certifique-se de estar usando o [Adaptador do Surface USB-C para HDMI](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).
* Verifique se há um problema de hardware de headset de Realidade Misturada:
    * Para confirmar ou descartar problemas de hardware com o headset, conecte o headset de Realidade Misturada a outro computador.
    * Primeiro, verifique se há problemas de compatibilidade e configuração do computador, pois os sintomas são semelhantes.
* Certifique-se de que o cabo USB esteja conectado a uma porta USB 3.0 ou mais rápida. As portas USB 3.0 têm SS (Super Velocidade) ao lado delas e geralmente são coloridas em azul.

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>A exibição do meu headset ocasionalmente fica preta após algum uso

* Tente desabilitar qualquer suspensão de USB ou recursos de economia de energia em seu computador. Por exemplo, no Configurações > System **> Power & Sleep > USB [selective suspend](/windows-hardware/drivers/usbcon/usb-selective-suspend)**, a configuração "Permitir que o computador desligue esse dispositivo para economizar energia" no Gerenciador de Dispositivos e as configurações de economia de energia USB no firmware do computador.
* Desconecte temporariamente quaisquer outros dispositivos USB e periféricos conectados ao computador.
* Verifique se a versão do driver gpu é recente e verifique se há novos problemas de desempenho e compatibilidade e regressões em novos drivers.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Uma das exibições no meu headset é preta

* Se você estiver usando um adaptador HDMI, certifique-se de que ele dá suporte ao HDMI 2.0.
* Remova os cabos de extensão USB e HDMI que você possa estar usando.
* Certifique-se de que o driver de gráficos está atualizado.
* Experimente o headset de Realidade Misturada em outro computador.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>Meu headset exibe azul e, em seguida, Portal de Realidade Misturada reinicializa

Normalmente, isso indica um problema ocasional de confiabilidade do controlador USB em seu computador:

* Tente outra porta USB. O computador pode ter vários controladores USB 3.0.
* Remova os cabos de extensão (se aplicável).
* Desconectar todos os outros dispositivos USB do computador.
* Conexão um hub USB 3.0 conectado externamente ao seu computador e conecte seu headset ao hub.
* Se você estiver usando um computador desktop, considere a compra de um cartão USB 3.0 PCIe para adicionar outro controlador USB ao seu computador.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Meu headset faz com que meu computador desligue ou mostre uma tela preta ao iniciar

Em alguns computadores, deixar o headset conectado antes de ligar ou durante a reinicialização do computador pode interferir no processo de inicialização. O computador pode selecionar as exibições do headset como o "monitor primário" para mostrar o progresso da inicialização do computador, não iniciar corretamente ou "desligar" ou produzir um código de erro de aviso. O comportamento depende da make e do modelo do COMPUTADOR ou da make e do modelo da placa gráfica. Para corrigir isso:

* Conexão headset para uma porta diferente em sua placa gráfica (talvez seja necessário usar um adaptador para usar as outras portas).
* Certifique-se de que o firmware BIOS/UEFI do computador esteja atualizado (mas atualize apenas o firmware BIOS/UEFI do computador se você estiver confortável fazendo isso).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Meu pc ou headset exibe cintilação, flash ou permanece preto ao usar um Surface PC

* Certifique-se de que você está usando um adaptador HDMI que dá suporte ao HDMI 2.0. Muitos adaptadores HDMI mais antigos só são compatíveis com a resolução de 1080p, o que é insuficiente para headsets de Realidade Misturada.
* Certifique-se de que o driver de gráficos está atualizado. Verifique Windows Atualizar e o site do fabricante do computador para ver se há um driver gráfico atualizado.
* Alguns dispositivos Surface são incompatíveis com Windows Mixed Reality. Saiba mais sobre a [compatibilidade e os requisitos do Surface.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface)

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>A exibição do meu headset não funciona depois que eu desligar e fazer uma inicialização rápida

Desconectar o cabo HDMI e o cabo USB do headset e, em seguida, conecte-os novamente.

## <a name="my-headset-displays-are-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>As exibições do meu headset são finas, mas Portal de Realidade Misturada janela de visualização da empresa parece estar boa

* Certifique-se de que os recursos do sistema do computador (CPU, memória e disco rígido) estão disponíveis e não são consumidos por outro aplicativo ou processo.
* Atualize o driver de gráficos.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Estou recebendo um erro "A classe de instalação não está presente ou é inválida" no Gerenciador de Dispositivos

Se você vir "HoloLens sensores" com um ponto de exclamação amarelo no Gerenciador de Dispositivos, selecione o dispositivo para obter detalhes adicionais. Se você vir uma mensagem dizendo "Os drivers para este dispositivo não estão instalados. (Código 28)--A classe de instalação não está presente ou é inválida", isso normalmente é porque o computador está executando Windows 10 [N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). N edições Windows 10 não são suportadas Windows Mixed Reality e você precisará instalar uma versão não N do Windows 10.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Meu ambiente wmr está tremida ou gagueja quando eu mover minha cabeça e exibe a visão dupla

Em um laptop com elementos gráficos integrados e uma GPU Nvidia, ocorre um erro após um período de tempo que parece fazer com que um quadro anterior seja exibido após o próximo quadro, resultando em visão dupla, quanto mais rápido você mover a cabeça em um yaw, tom ou movimento de rolagem. O problema parece estar nos drivers após o Nvidia Graphics Driver 436.48.  A instalação desse driver corrigirá o problema até que a Nvidia resolva o problema nos drivers atualizados. Para uma instalação direta do Nvidia Graphics Driver 436.48, visite [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>Estou constrangido no meu headset

Para obter informações gerais sobre o conforto Windows Mixed Reality, consulte Windows Mixed Reality de headset imersivo, segurança [e conforto.](wmr-health-safety-comfort.md) Para obter detalhes sobre seu headset específico, verifique com o fabricante do headset.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Como posso obter uma exibição mais clara no meu headset

Tente ajustar o ajuste do headset. Mova-o para cima e para baixo, ou para a esquerda e para a direita, em seu rosto e ajuste as alças para que ele se sinta confortável.

Se o headset tiver um botão para ajustar a calibragem, ajuste suas configurações de calibragem. Se não tiver, vá para Configurações > realidade misturada **> visual e** ajuste a calibragem lá. Para obter mais informações sobre calibragem para seu dispositivo específico, verifique com o fabricante do headset.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Frequentemente, vejo uma borda preta ao redor da exibição no headset. Às vezes, é como estou procurando um túnel

Isso significa que o aplicativo não pode pressionar a taxa de quadros em seu computador e o sistema está usando quadros antigos para renderizar a exibição no headset. Como os aplicativos só renderizam a parte do mundo que você está vendo, se eles não atingirem suas taxas de quadros de forma consistente, o sistema tentará renderizar o mundo a partir de um ponto de vista anterior e preencherá os detalhes ausentes com preto. Se isso ocorrer com frequência:

1. Feche ou interrompa todos os programas desnecessários para liberar memória e CPU.
2. Reduza as configurações de detalhes em seu aplicativo.
3. vá para **Configurações > realidade mista > tela de Headset** para reduzir a quantidade de detalhes mostrada na página inicial do Windows Mixed Reality.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>O modo de exibição do headset está se estremindo e se esficando muito

O sistema pode não ser capaz de renderizar o conteúdo para o headset ou o sistema de controle pode estar tendo problemas:

1. Abra o Gerenciador de tarefas para certificar-se de que seu computador tem recursos de computação suficientes. Você deve ter 80% de CPU livre, 400 MB de RAM e e/s de disco devem estar abaixo de 80%.
2. Verifique se você tem os drivers gráficos mais recentes para seu hardware. Consulte a [seção driver de gráficos](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Verifique se a sala tem luz suficiente.
4. desconecte o dispositivo, feche Windows Mixed Reality e conecte-o novamente.
5. Reinicie o computador.
6. Se o problema persistir, entre em contato com o atendimento [ao cliente](https://support.microsoft.com/).