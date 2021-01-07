---
title: Obtenha ajuda com a compatibilidade do PC no Windows Mixed Reality
description: Recurso de ajuda para problemas de compatibilidade de PC ao trabalhar com a realidade mista do Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, comentários, Hub de comentários, bugs
appliesto:
- Windows 10
ms.openlocfilehash: 8f6ba747c2f336194cb30241dce18bc1138143f2
ms.sourcegitcommit: b331ec40b1e8869e6a6e7b2e32a03ff68e04b956
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97956059"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Obtenha ajuda com a compatibilidade do PC no Windows Mixed Reality

Quando estiver configurando a realidade mista do Windows ou usando o [portal de realidade misturada](install-windows-mixed-reality.md), você receberá um relatório sobre se seu PC está com a tarefa. Fizemos detalhes específicos sobre o que você pode ver nas seções abaixo.

Antes de continuar, tente as correções mais comuns abaixo: 

> [!div class="checklist"]
> * Verifique se o computador atende aos [requisitos mínimos de compatibilidade de hardware do PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
> * Verifique se a [placa gráfica e o processador](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) são compatíveis
> * Verificar a lista de [adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
> * Atualize o driver de gráficos selecionando **iniciar > configurações > atualizar & segurança > verificar** se há atualizações 

Se você quiser entrar em contato, [solicite à comunidade](https://answers.microsoft.com), [entre em contato com o suporte](https://support.microsoft.com/contactus/)ou passe pelas informações de [solução de problemas](troubleshooting-windows-mixed-reality.md) .

## <a name="youre-good-to-go"></a>Você está pronto para começar

Boas notícias, se você vir a mensagem **está pronto para começar** , seu PC poderá executar a realidade mista do Windows! Ainda há variação entre o hardware e a configuração do computador, portanto, a experiência de realidade mista pode não ser a mesma em todos os PCs.

## <a name="supports-some-features"></a>Dá suporte a alguns recursos

Se você estiver vendo a mensagem **dá suporte a alguns recursos** , seu PC poderá executar algumas experiências de realidade mista do Windows, mas poderá não fornecer a melhor experiência possível. As desvantagens possíveis incluem a defasagem de gráficos, acertos de desempenho e alguns aplicativos e jogos que você não pode executar. Listamos as mensagens que você pode ver e o que fazer sobre elas abaixo:

* [Este computador tem uma placa gráfica integrada com RAM de canal único](#this-pc-has-an-integrated-graphics-card-with-single-channel-ram)
* [Este computador tem uma configuração gráfica híbrida com um link PCIe incompatível](#this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link)
* [O driver gráfico do PC pode não funcionar bem com a realidade mista do Windows](#this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality)
* [O processador deste computador pode não funcionar bem com a realidade mista do Windows](#this-pcs-processor-might-not-work-well-with-windows-mixed-reality)
* [Este computador pode não ter uma configuração de USB compatível](#this-pc-might-not-have-a-compatible-usb-configuration)
* [Este computador não tem Bluetooth 4,0 para controladores](#this-pc-doesnt-have-bluetooth-40-for-controllers)
* [Dependendo do headset, talvez seja necessário um adaptador Bluetooth para usar os controladores de movimento](#depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers)
* [Este computador não tem uma porta USB autoalimentada](#this-pc-doesnt-have-a-self-powered-usb-port)
* [A placa gráfica deste computador não funcionará com a realidade mista do Windows](#this-pcs-graphics-card-wont-work-with-windows-mixed-reality)
* [O driver gráfico deste computador não funcionará com a realidade mista do Windows](#this-pcs-graphics-driver-wont-work-with-windows-mixed-reality)
* [O processador deste computador não funcionará com a realidade mista do Windows](#this-pcs-processor-wont-work-with-windows-mixed-reality)
* [Este computador não tem espaço livre em disco suficiente para executar a realidade mista do Windows](#this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality)
* [Este computador está executando uma edição do Windows que não dá suporte à realidade mista do Windows](#this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality)
* [Este computador não está executando a versão mais recente do Windows 10](#this-pc-isnt-running-the-latest-version-of-windows-10)
* [Este computador não tem nenhuma porta USB 3,0](#this-pc-has-no-usb-30-port)
* [Você não pode executar este aplicativo por meio da área de trabalho remota](#you-cant-run-this-app-via-remote-desktop)

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este computador tem uma placa gráfica integrada com RAM de canal único

Placas gráficas integradas fornecerão a melhor experiência de realidade misturada do Windows em PCs com RAM de canal duplo. Se você encontrar problemas de desempenho:

> [!div class="checklist"]
> * Instalar uma [placa gráfica discreta compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)
> * Instalar um pente de RAM adicional para criar RAM de canal duplo
> * Alternar para um [PC compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este computador tem uma configuração gráfica híbrida com um link PCIe incompatível

O PCIe significa *interconexão de componente periférica Express*, que é a conexão que um computador usa para se comunicar com uma placa gráfica. Sua configuração pode funcionar, mas se você tiver problemas, será necessário alternar para um [computador compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>O driver gráfico do PC pode não funcionar bem com a realidade mista do Windows

Tente baixar um novo driver de gráficos usando Windows Update por:

> [!div class="checklist"]
> * Selecionando **iniciar > configurações > atualizar & segurança > verificar** se há atualizações ou acessar o site do fabricante do seu PC ou da placa de gráficos
> * [Verificar atualizações](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se isso não funcionar, você precisará:

> [!div class="checklist"]
> * Adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Alternar para um [PC compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>O processador deste computador pode não funcionar bem com a realidade mista do Windows

O processador do seu PC pode não funcionar bem com o Windows Mixed Reality porque ele não tem núcleos suficientes. Se o Windows Mixed Reality não for bem executado:

> [!div class="checklist"]
> * Substitua o processador por um [compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) 
> * Alternar para um [PC compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Este computador pode não ter uma configuração de USB compatível

Para problemas ao executar a realidade mista do Windows:

> [!div class="checklist"]
> * Verifique a [documentação dos adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para obter soluções para problemas comuns de compatibilidade
> * Considere usar um [hub USB com alimentação externa](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets)

Se os problemas persistirem:

> [!div class="checklist"]
> * Conecte seu headset em uma porta USB diferente, se você tiver uma disponível.
> * Se isso não funcionar, desinstale o driver USB atual do PC e reinstale um driver da Microsoft:

1. Selecione **Iniciar** e, em seguida, digite "Gerenciador de dispositivos" na caixa de **pesquisa** .
2. Selecione **Device Manager** nos resultados.
3. Expanda a categoria para controladores de barramento serial universal, examine os dispositivos listados e desinstale os drivers incompatíveis.
    * Se a lista incluir um item de "controlador de host extensível" que não tenha "Microsoft" no final do nome do dispositivo, esse driver não será compatível com a realidade mista do Windows. Você precisará desinstalá-lo. Para desinstalar um driver, clique com o botão direito do mouse no dispositivo na lista e selecione **desinstalar dispositivo**. Marque a caixa de seleção **excluir o software do driver para este dispositivo** e selecione **desinstalar**.
    * Se a lista incluir um item de "controlador de host extensível" que inclui "Etron" no nome, esse controlador USB não será compatível com a realidade mista do Windows. Você precisará usar uma porta USB diferente no PC ou adquirir um controlador de host USB 3,0 diferente.
4. Reinicie o computador.
5. Retorne para Device Manager e localize o item do controlador de host extensível novamente. Se agora você vir "Microsoft" no final do nome do dispositivo, você está pronto para começar. Caso contrário, repita as etapas de desinstalação para remover quaisquer versões adicionais que não sejam da Microsoft do driver.

> [!div class="checklist"]
> * Se isso ainda não funcionar, adicione uma placa USB PCIe ao seu PC.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este computador não tem Bluetooth 4,0 para controladores

2018 e os headsets de realidade mista do Windows mais recentes já têm o Bluetooth interno, mas se você tiver um headset mais antigo, o Bluetooth 4,0 será necessário para controladores de movimento de realidade misturada. Você ainda pode [usar a realidade mista do Windows com um controlador Xbox](motion-controller-problems.md#can-i-pair-my-xbox-controller-to-my-pc-so-i-can-use-it-in-headset), um [mouse e um teclado](https://docs.microsoft.com/windows/mixed-reality/discover/navigating-the-windows-mixed-reality-home#keyboard-and-mouse)ou um [adaptador USB Bluetooth para conectar os controladores de movimento](motion-controller-problems.md#how-can-i-tell-if-im-using-bluetooth-technology) ao seu PC. [Consulte adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>Dependendo do headset, talvez seja necessário um adaptador Bluetooth para usar os controladores de movimento

Alguns headsets têm o Bluetooth interno para que os controladores possam emparelhar diretamente com os headsets. Outros exigem um rádio Bluetooth no PC (ou um dongle separado) para usar controladores de movimento. Para obter mais informações, consulte a página [adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#windows-mixed-reality-compatible-usb-bluetooth-adapters) .

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este computador não tem uma porta USB autoalimentada

Uma porta USB 3,0 de alimentação automática é necessária para conectar um headset do Windows Mixed Reality. Conecte um [hub USB 3,0 alimentado](recommended-adapters-for-windows-mixed-reality-capable-pcs.md#using-external-usb-30-hubs-with-windows-mixed-reality-headsets) ao PC e use-o para conectar seu headset.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>A placa gráfica deste computador não funcionará com a realidade mista do Windows

A placa gráfica do computador não é compatível com a realidade mista do Windows. Você precisará:

> [!div class="checklist"]
> * Adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Alternar para um [PC compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>O driver gráfico deste computador não funcionará com a realidade mista do Windows

O driver gráfico deste computador não funcionará com a realidade mista do Windows. Tente baixar um novo driver de gráficos usando Windows Update por:

> [!div class="checklist"]
> * Selecionando **iniciar > configurações > atualizar & segurança > verificar** se há atualizações ou acessar o site do fabricante do seu PC ou da placa de gráficos
> * [Verificar atualizações](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se isso não funcionar, você precisará:

> [!div class="checklist"]
> * Adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Alternar para um [PC compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>O processador deste computador não funcionará com a realidade mista do Windows

O processador deste computador não dá suporte a instruções AVX/Popcnt. Para executar a realidade mista do Windows, você precisará:

> [!div class="checklist"]
> * Substituí-lo por uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) 
> * Alternar para um [PC compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines)

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Este computador não tem espaço livre em disco suficiente para executar a realidade mista do Windows

A realidade mista do Windows requer 10 GB de espaço livre em disco para a instalação e o melhor desempenho. Libere espaço na unidade e tente configurar novamente desde o início.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Este computador está executando uma edição do Windows que não dá suporte à realidade mista do Windows

A realidade mista do Windows funciona no [Windows 10 Home](https://www.microsoft.com/p/windows-10-home/d76qx4bznwk4?activetab=pivot:overviewtab) e no [Windows 10 pro](https://www.microsoft.com/p/windows-10-pro/DF77X4D43RKT?icid=W10Pro_upsell_071817&activetab=pivot:overviewtab). Você precisará instalar uma dessas edições para usar a realidade mista do Windows.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Este computador não está executando a versão mais recente do Windows 10

A realidade mista do Windows requer a atualização dos criadores de outono do Windows 10. [Atualize seu computador](https://support.microsoft.com/help/4028685) e tente novamente.

### <a name="this-pc-has-no-usb-30-port"></a>Este computador não tem nenhuma porta USB 3,0

Você precisará de uma porta USB 3,0 para conectar um headset de realidade mista do Windows. Se você estiver usando um PC desktop, adicione uma placa USB PCIe. Para laptops, você precisará alternar para um [computador compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Você não pode executar este aplicativo por meio da área de trabalho remota

Para usar a realidade mista do Windows, você precisa de um PC com um monitor conectado. Se você estiver usando uma máquina virtual ou não tiver um monitor, tente usar um adaptador de vídeo virtual. Esse é um dispositivo que se conecta ao DisplayPort do PC e emula uma exibição do computador.

## <a name="getting-the-best-performance"></a>Obtendo o melhor desempenho

Algumas configurações de hardware podem causar problemas de desempenho com a realidade mista do Windows. Para problemas como carregamento lento, visuais instável ou baixa qualidade visual, experimente estas correções comuns:

* Feche todos os aplicativos abertos em execução no seu computador desktop
* Se você estiver usando um USB-C ou um DisplayPort para adaptador HDMI, tente um diferente. Consulte adaptadores recomendados
* Se houver monitores extras conectados à placa gráfica do PC, desconecte-os
* Tente baixar alguns aplicativos de realidade misturada diferentes da Windows Store – alguns podem funcionar melhor com a configuração do computador
* Confira nossa [documentação de perguntas sobre desempenho](performance-questions.md)

Se você ainda tiver problemas de desempenho, atualize as seguintes configurações de [realidade mista do Windows](set-up-windows-mixed-reality.md) para obter uma experiência de usuário ideal:

* Experiência
* Resolução
* Taxa de quadros
* Calibragem

> [!NOTE]
> Se você vir uma mensagem dizendo "esta configuração de hardware pode funcionar com a realidade mista do Windows, mas ela ainda não foi testada", você poderá encontrar alguns problemas de desempenho ao executar a realidade mista do Windows para sessões longas.

## <a name="working-with-steamvr"></a>Trabalhando com SteamVR

Aproveitar os jogos do SteamVR é uma ótima maneira de experimentar tudo o que o VR tem a oferecer. No entanto, você desejará ter certeza de que está [obtendo o melhor desempenho](performance-questions.md) do seu dispositivo de imersão. Depois de instalar o [fluxo](https://store.steampowered.com/about):

* Siga as instruções para [usar o SteamVR com o Windows Mixed Reality](using-steamvr-with-windows-mixed-reality.md)
* Instalar os aplicativos de [teste de desempenho do SteamVR](https://store.steampowered.com/app/323910/SteamVR_Performance_Test)

## <a name="next-vr-checkpoint"></a>Próximo ponto de verificação VR

Se você estiver seguindo a jornada VR que apresentamos, estará quase pronto para comprar um dispositivo. A partir daqui, você pode continuar para o último antes de comprar o ponto de verificação:

> [!div class="nextstepaction"]
> [Perguntas frequentes sobre compra](before-you-buy-faqs.md)

Ou vá diretamente para a seção Introdução:

> [!div class="nextstepaction"]
> [Configurando a realidade mista do Windows](set-up-windows-mixed-reality.md)

Você sempre pode voltar para a [jornada VR](vr-journey.md) a qualquer momento.