---
title: Obtenha ajuda com a compatibilidade do PC
description: Mantenha-se atualizado com os recursos para resolver problemas de compatibilidade do computador ao trabalhar com Windows Mixed Reality aplicativos e dispositivos.
author: hferrone
ms.author: v-hferrone
ms.date: 01/07/2021
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Comentários, Hub de Comentários, bugs
appliesto:
- Windows 10
ms.openlocfilehash: cd5598147823670d1aa00eddda844bea21d7da262339624613f3724cbc5157fa
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189208"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Obter ajuda com a compatibilidade do computador Windows Mixed Reality

Quando você estiver configurando Windows Mixed Reality ou usando o Portal de Realidade Misturada [,](install-windows-mixed-reality.md)você obterá um relatório sobre se o computador está até a tarefa. Detalhamos detalhes específicos sobre o que você pode ver nas seções abaixo.

Antes de continuar, experimente as correções mais comuns abaixo: 

> [!div class="checklist"]
> * Certifique-se de que seu computador atenda aos [requisitos mínimos de compatibilidade de hardware do pc](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * Verifique se a [placa gráfica e o processador são](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) compatíveis
> * Verifique a [lista de adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Atualize o driver de elementos gráficos selecionando **Iniciar > Configurações > atualizar & segurança > Verificar se há atualizações** 

Se você quiser entrar em contato, peça [](https://support.microsoft.com/contactus/)à comunidade [,](https://answers.microsoft.com)entre em contato com o suporte ou consulte as informações de [solução de](troubleshooting-windows-mixed-reality.md) problemas.

## <a name="youre-good-to-go"></a>Você pode ir

Boas notícias, se você vir **a mensagem Você está bem para ir,** seu computador pode executar Windows Mixed Reality! Ainda há variação entre o hardware e a configuração do computador, portanto, a experiência de Realidade Misturada pode não ser a mesma em todos os computadores.

## <a name="supports-some-features"></a>Dá suporte a alguns recursos

Se você estiver  vendo a mensagem Dá suporte a alguns recursos, seu computador poderá executar algumas Windows Mixed Reality experiências, mas talvez não forneça a melhor experiência possível. Possíveis desvantagens incluem gráficos de atraso, acertos de desempenho e alguns aplicativos e jogos que você não pode executar. Listamos as mensagens que você pode ver e o que fazer sobre elas abaixo:

* [Este computador tem uma placa gráfica integrada com RAM de canal único](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [Este computador tem uma configuração de elementos gráficos híbridos com um link PCIe incompatível](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [O driver gráfico desse computador pode não funcionar bem com Windows Mixed Reality](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [O processador desse computador pode não funcionar bem com Windows Mixed Reality](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [Esse computador pode não ter uma configuração USB compatível](#this-pc-might-not-have-a-compatible-usb-configuration)
* [Este computador não tem Bluetooth 4.0 para controladores](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [Dependendo do headset, talvez você precise de um adaptador Bluetooth para usar controladores de movimento](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [Este computador não tem uma porta USB auto-alimentada](#this-pc-doesnt-have-a-self-powered-usb-port)
* [A placa gráfica desse computador não funcionará com Windows Mixed Reality](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [O driver gráfico desse computador não funcionará com Windows Mixed Reality](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [O processador desse computador não funcionará com Windows Mixed Reality](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [Este computador não tem espaço livre suficiente em disco para executar Windows Mixed Reality](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [Este computador está executando uma edição do Windows que não dá suporte a Windows Mixed Reality](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [Este computador não está executando a versão mais recente do Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Este computador não tem porta USB 3.0](#this-pc-has-no-usb-30-port)
* [Você não pode executar esse aplicativo por meio da área de trabalho remota](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este computador tem uma placa gráfica integrada com RAM de canal único

As placas gráficas integradas fornecerão a melhor Windows Mixed Reality em PCs com RAM de canal duplo. Se você tiver problemas de desempenho:

> [!div class="checklist"]
> * Instalar uma [placa gráfica discreta compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Instalar um stick de RAM adicional para criar RAM de canal duplo
> * Alternar para um [computador compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este computador tem uma configuração de elementos gráficos híbridos com um link PCIe incompatível

PCIe significa *Periférico Component Interconnect Express*, que é a conexão que um COMPUTADOR usa para se comunicar com uma placa gráfica. Sua configuração pode funcionar, mas se você tiver problemas, precisará alternar para um [computador compatível.](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>O driver gráfico desse computador pode não funcionar bem com Windows Mixed Reality

Tente baixar um novo driver de gráficos usando Windows Atualizar:

> [!div class="checklist"]
> * Selecionando Iniciar > Configurações > Atualizar & segurança **> Verificar** se há atualizações ou ir para o site do fabricante do computador ou da placa gráfica
> * [Verificar atualizações](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se isso não funcionar, você precisará:

> [!div class="checklist"]
> * Adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Alternar para um [computador compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>O processador desse computador pode não funcionar bem com Windows Mixed Reality

O processador do computador pode não funcionar bem com Windows Mixed Reality porque ele não tem núcleos suficientes. Se Windows Mixed Reality não for bem executado:

> [!div class="checklist"]
> * Substituir o processador por [um compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * Alternar para um [computador compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Esse computador pode não ter uma configuração USB compatível

Para problemas de execução Windows Mixed Reality:

> [!div class="checklist"]
> * Verifique nossa [documentação de adaptadores recomendada](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para encontrar soluções para problemas comuns de compatibilidade
> * Considere o uso de [um hub USB externo](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

Se os problemas persistirem:

> [!div class="checklist"]
> * Conecte o headset a uma porta USB diferente, se você tiver uma disponível.
> * Se isso não funcionar, desinstale o driver USB atual do computador e reinstale um driver da Microsoft:

1. Selecione **Iniciar** e digite "gerenciador de dispositivos" na **caixa** Pesquisar.
2. Selecione **Gerenciador de Dispositivos** nos resultados.
3. Expanda a categoria para controladores do Barramento Serial Universal, veja os dispositivos listados e desinstale todos os drivers incompatíveis.
    * Se a lista incluir um item "Controlador de Host eXtensible" que não tenha "Microsoft" no final do nome do dispositivo, esse driver não será compatível com Windows Mixed Reality. Você precisará desinstalá-lo. Para desinstalar um driver, clique com o botão direito do mouse no dispositivo na lista e selecione **Desinstalar o dispositivo**. Marque a **caixa de seleção Excluir o software do driver para** este dispositivo e, em seguida, selecione **Desinstalar**.
    * Se a lista incluir um item "Controlador de Host eXtensible" que inclui "Etron" no nome, esse controlador USB não será compatível com Windows Mixed Reality. Você precisará usar uma porta USB diferente no computador ou comprar um controlador de host USB 3.0 diferente.
4. Reinicie o computador.
5. Retorne ao Gerenciador de Dispositivos e localize o item controlador de host eXtensible novamente. Se agora você vir "Microsoft" no final do nome do dispositivo, tudo bem. Caso não, repita as etapas de desinstalação para remover qualquer versão extra não Microsoft do driver.

> [!div class="checklist"]
> * Se isso ainda não funcionar, adicione um cartão USB PCIe ao seu computador.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este computador não tem Bluetooth 4.0 para controladores

2018 e os headsets Windows Mixed Reality mais novos já têm o Bluetooth interno, mas se você tiver um headset mais antigo, o bluetooth 4.0 será necessário para controladores de movimento de realidade misturada. Você ainda pode usar Windows Mixed Reality com um controlador [](/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse) [Xbox,](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset)um mouse e um teclado ou um adaptador [de Bluetooth USB](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) para conectar controladores de movimento ao computador. [Consulte adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>Dependendo do headset, talvez você precise de um adaptador Bluetooth para usar controladores de movimento

Alguns headsets têm Bluetooth integrados para que os controladores possam emparelhar diretamente com os headsets. Outros exigem Bluetooth rádio no computador (ou um dongle separado) para usar controladores de movimento. Para obter mais informações, consulte a [página de adaptadores](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) recomendada.

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este computador não tem uma porta USB auto-alimentada

Uma porta USB 3.0 auto-alimentada é necessária para conectar um headset Windows Mixed Reality dispositivo. Conexão um [hub USB 3.0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) conectado ao computador e usá-lo para conectar o headset.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>A placa gráfica desse computador não funcionará com Windows Mixed Reality

A placa gráfica do computador não é compatível com Windows Mixed Reality. Você precisará:

> [!div class="checklist"]
> * Adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Alternar para um [computador compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>O driver gráfico desse computador não funcionará com Windows Mixed Reality

O driver gráfico desse computador não funcionará com Windows Mixed Reality. Tente baixar um novo driver de gráficos usando Windows Atualizar:

> [!div class="checklist"]
> * Selecionando Iniciar > Configurações > Atualizar & segurança **> Verificar** se há atualizações ou ir para o site do fabricante do computador ou da placa gráfica
> * [Verificar atualizações](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se isso não funcionar, você precisará:

> [!div class="checklist"]
> * Adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Alternar para um [PC compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>O processador deste computador não funcionará com Windows Mixed Reality

O processador deste computador não dá suporte a instruções AVX/Popcnt. para executar Windows Mixed Reality, você precisará:

> [!div class="checklist"]
> * Substituí-lo por uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Alternar para um [PC compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Este computador não tem espaço livre em disco suficiente para ser executado Windows Mixed Reality

Windows Mixed Reality requer 10 GB de espaço livre em disco para a instalação e o melhor desempenho. Libere espaço na unidade e tente configurar novamente desde o início.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>este computador está executando uma edição do Windows que não oferece suporte a Windows Mixed Reality

Windows Mixed Reality funciona em [Windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) e [Windows 10 Pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab). Você precisará instalar uma dessas edições para usar Windows Mixed Reality.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Este computador não está executando a versão mais recente do Windows 10

Windows Mixed Reality requer o Windows 10 Fall Creators Update. [Atualize seu computador](https://support.microsoft.com/help/4028685) e tente novamente.

### <a name="this-pc-has-no-usb-30-port"></a>Este computador não tem nenhuma porta USB 3,0

você precisará de uma porta USB 3,0 para conectar um Windows Mixed Reality headset. Se você estiver usando um PC desktop, adicione uma placa USB PCIe. Para laptops, você precisará alternar para um [computador compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Você não pode executar este aplicativo por meio da área de trabalho remota

para usar Windows Mixed Reality, você precisa de um PC com um monitor conectado. Se você estiver usando uma máquina virtual ou não tiver um monitor, tente usar um adaptador de vídeo virtual. Esse é um dispositivo que se conecta ao DisplayPort do PC e emula uma exibição do computador.

## <a name="getting-the-best-performance"></a>Obtendo o melhor desempenho

Algumas configurações de hardware podem causar problemas de desempenho com Windows Mixed Reality. Para problemas como carregamento lento, visuais instável ou baixa qualidade visual, experimente estas correções comuns:

* Feche todos os aplicativos abertos em execução no seu computador desktop
* Se você estiver usando um USB-C ou um DisplayPort para adaptador HDMI, tente um diferente. Consulte adaptadores recomendados
* Se houver monitores extras conectados à placa gráfica do PC, desconecte-os
* tente baixar alguns aplicativos de realidade misturados diferentes da Windows Store – alguns podem funcionar melhor com a configuração do computador
* Confira nossa [documentação de perguntas sobre desempenho](performance-questions.md)

se você ainda tiver problemas de desempenho, atualize as configurações de [Windows Mixed Reality](set-up-windows-mixed-reality.md) a seguir para obter uma experiência de usuário ideal:

* Experiência
* Resolução
* Taxa de quadros
* Calibragem

> [!NOTE]
> se você vir uma mensagem dizendo "esta configuração de hardware pode funcionar com Windows Mixed Reality, mas ainda não foi testada", você poderá encontrar alguns problemas de desempenho ao executar Windows Mixed Reality para sessões longas.

## <a name="working-with-steamvr"></a>Trabalhando com SteamVR

Aproveitar os jogos do SteamVR é uma ótima maneira de experimentar tudo o que o VR tem a oferecer. No entanto, você desejará ter certeza de que está [obtendo o melhor desempenho](performance-questions.md) do seu dispositivo de imersão. Depois de instalar o [fluxo](https://store.steampowered.com/about):

* Siga as instruções para [usar o SteamVR com Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)
* Instalar os aplicativos de [teste de desempenho do SteamVR](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)

## <a name="next-vr-checkpoint"></a>Próximo ponto de verificação VR

Se você estiver seguindo a jornada VR que apresentamos, estará quase pronto para comprar um dispositivo. A partir daqui, você pode continuar para o último antes de comprar o ponto de verificação:

> [!div class="nextstepaction"]
> [Perguntas frequentes sobre compra](before-you-buy-faqs.md)

Ou vá diretamente para a seção Introdução:

> [!div class="nextstepaction"]
> [Configurando Windows Mixed Reality](set-up-windows-mixed-reality.md)

Você sempre pode voltar para a [jornada VR](vr-journey.md) a qualquer momento.