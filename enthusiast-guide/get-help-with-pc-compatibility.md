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
ms.openlocfilehash: 5b24edd88a55bedea2d288f27363714cbfe768b4
ms.sourcegitcommit: 9a489e8a3bf90b20f1b61606eea42c859c833424
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94340584"
---
# <a name="get-help-with-pc-compatibility-in-windows-mixed-reality"></a>Obtenha ajuda com a compatibilidade do PC no Windows Mixed Reality

Quando estiver configurando a realidade mista do Windows ou executando o aplicativo de [verificação do PC do Windows Mixed Reality](https://www.microsoft.com/p/windows-mixed-reality-pc-check/9nzvl19n7cnc?rtc=1#activetab=pivot:overviewtab) no seu computador, você receberá um relatório sobre se o seu PC está pronto para executá-lo. Fizemos detalhes específicos sobre o que você pode ver nas seções abaixo.

Antes de continuar, verifique se o computador atende aos [requisitos mínimos de compatibilidade de hardware do PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) para executar realidade misturada.

## <a name="youre-good-to-go"></a>Você está pronto para começar

Boa notícia, seu PC pode executar a realidade mista do Windows! Tenha em mente que ainda há variação entre o hardware e a configuração do computador, portanto, a experiência de realidade mista pode não ser a mesma em todos os PCs.

## <a name="supports-some-features"></a>Dá suporte a alguns recursos

Seu PC é capaz de executar algumas experiências do Windows Mixed Reality, mas pode não fornecer a melhor experiência possível. Possíveis desvantagens incluem gráficos de retardo, acertos de desempenho para aplicativos e jogos, com alguns aplicativos e jogos que não podem ser executados. Listamos as mensagens que você pode ver e o que fazer sobre elas abaixo:

### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este computador tem uma placa gráfica integrada com RAM de canal único

Placas gráficas integradas fornecerão a melhor experiência de realidade misturada do Windows em PCs com RAM de canal duplo. Se você tiver problemas de desempenho, tente um dos seguintes:

* Instale uma [placa gráfica discreta compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines).
* Instale um pente de RAM adicional para criar uma RAM de canal duplo.
* Alterne para um [computador compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este computador tem uma configuração gráfica híbrida com um link PCIe incompatível

O PCIe significa *interconexão de componentes de periféricos Express*. Essa é a conexão que um computador usa para se comunicar com uma placa gráfica. Sua configuração pode funcionar, mas se você tiver problemas, será necessário alternar para um [computador compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>O driver gráfico do PC pode não funcionar bem com a realidade mista do Windows

Tente baixar um novo driver de gráficos usando Windows Update selecionando **iniciar > configurações > atualizar & segurança > verificar se há atualizações** ou acesse o site fabricante do PC ou fabricante da placa gráfica.

> [!div class="nextstepaction"]
> [Verificar atualizações](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se isso não funcionar, você precisará adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ou alternar para um [PC compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>O processador deste computador pode não funcionar bem com a realidade mista do Windows

O processador do seu PC pode não funcionar bem com a realidade mista do Windows, pois não tem núcleos suficientes. Se a realidade mista do Windows não for bem executada, substitua o processador por um [compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou mude para um [PC compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Este computador pode não ter uma configuração de USB compatível

Se você tiver problemas ao executar a realidade mista do Windows, tente o seguinte:

* Conecte seu headset em uma porta USB diferente, se disponível.
* Se isso não funcionar, desinstale o driver USB atual do PC e reinstale um driver da Microsoft:

1. Selecione **Iniciar** e, em seguida, digite "Gerenciador de dispositivos" na caixa de **pesquisa** .
2. Selecione **Device Manager** nos resultados.
3. Expanda a categoria para controladores de barramento serial universal, examine os dispositivos listados e desinstale os drivers incompatíveis.
    * Se a lista incluir um item de "controlador de host extensível" que não tenha "Microsoft" no final do nome do dispositivo, esse driver não será compatível com a realidade mista do Windows. Você precisará desinstalá-lo. Para desinstalar um driver, clique com o botão direito do mouse no dispositivo na lista e selecione **desinstalar dispositivo**. Marque a caixa de seleção **excluir o software do driver para este dispositivo** e selecione **desinstalar**.
    * Se a lista incluir um item de "controlador de host extensível" que inclui "Etron" no nome, esse controlador USB não será compatível com a realidade mista do Windows. Você precisará usar uma porta USB diferente no PC ou adquirir um controlador de host USB 3,0 diferente.
4. Reinicie o computador.
5. Retorne para Device Manager e localize o item do controlador de host extensível novamente. Se agora você vir "Microsoft" no final do nome do dispositivo, você está pronto para começar. Caso contrário, repita as etapas de desinstalação para remover quaisquer versões adicionais que não sejam da Microsoft do driver.

* Se isso ainda não funcionar, adicione uma placa USB PCIe ao seu PC.

### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este computador não tem Bluetooth 4,0 para controladores

2018 e os headsets de realidade mista do Windows mais recentes já têm o Bluetooth interno, mas se você tiver um headset mais antigo, o Bluetooth 4,0 será necessário para controladores de movimento de realidade misturada. Você ainda pode usar a realidade mista do Windows com um controlador Xbox ou com um mouse e um teclado, ou pode usar um adaptador USB Bluetooth para conectar os controladores de movimento ao seu PC. [Consulte adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)

### <a name="depending-on-your-headset-you-may-need-a-bluetooth-adapter-to-use-motion-controllers"></a>Dependendo do headset, talvez seja necessário um adaptador Bluetooth para usar os controladores de movimento

Alguns headsets têm o Bluetooth interno para que os controladores possam emparelhar diretamente com os headsets. Outros exigem um rádio Bluetooth no PC (ou um dongle separado) para usar controladores de movimento. [Consulte a página adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para obter mais informações.

### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este computador não tem uma porta USB autoalimentada

Uma porta USB 3,0 de alimentação automática é necessária para conectar um headset do Windows Mixed Reality. Conecte um hub USB 3,0 alimentado ao PC e use-o para conectar seu headset.

### <a name="this-pcs-graphics-card-wont-work-with-windows-mixed-reality"></a>A placa gráfica deste computador não funcionará com a realidade mista do Windows

A placa gráfica do computador não é compatível com a realidade mista do Windows. Você precisará adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ou alternar para um [PC compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-graphics-driver-wont-work-with-windows-mixed-reality"></a>O driver gráfico deste computador não funcionará com a realidade mista do Windows

O driver gráfico deste computador não funcionará com a realidade mista do Windows. Tente baixar um novo driver de gráficos usando Windows Update selecionando **iniciar > configurações > atualizar & segurança > Verifique** se há atualizações ou vá para o site fabricante do PC ou fabricante da placa gráfica.

> [!div class="nextstepaction"]
> [Verificar atualizações](ms-settings:windowsupdate?activationSource=SMC-Article-4045777)

Se isso não funcionar, você precisará adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ou alternar para um [PC compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="this-pcs-processor-wont-work-with-windows-mixed-reality"></a>O processador deste computador não funcionará com a realidade mista do Windows

O processador deste computador não dá suporte a instruções AVX/Popcnt. Para executar a realidade mista do Windows, você precisará substituí-lo por uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#compatibility-guidelines) ou alternar para um PC compatível.

### <a name="this-pc-doesnt-have-enough-free-disk-space-to-run-windows-mixed-reality"></a>Este computador não tem espaço livre em disco suficiente para executar a realidade mista do Windows

A realidade mista do Windows requer 10 GB de espaço livre em disco para a instalação e o melhor desempenho. Libere espaço na unidade e tente configurar novamente desde o início.

### <a name="this-pc-is-running-an-edition-of-windows-that-doesnt-support-windows-mixed-reality"></a>Este computador está executando uma edição do Windows que não dá suporte à realidade mista do Windows

A realidade mista do Windows funciona no Windows 10 Home e no Windows 10 pro. Você precisará instalar uma dessas edições para usar a realidade mista do Windows.

### <a name="this-pc-isnt-running-the-latest-version-of-windows-10"></a>Este computador não está executando a versão mais recente do Windows 10

A realidade mista do Windows requer a atualização dos criadores de outono do Windows 10. [Atualize seu computador](https://support.microsoft.com/help/4028685) e tente novamente.

### <a name="this-pc-has-no-usb-30-port"></a>Este computador não tem nenhuma porta USB 3,0

Você precisará de uma porta USB 3,0 para conectar um headset de realidade mista do Windows. Se você estiver usando um PC desktop, adicione uma placa USB PCIe. Se estiver usando um laptop, você precisará alternar para um [PC compatível](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1).

### <a name="you-cant-run-this-app-via-remote-desktop"></a>Você não pode executar este aplicativo por meio da área de trabalho remota

Para usar a realidade mista do Windows, você precisa de um PC com um monitor conectado. Se você estiver usando uma máquina virtual ou não tiver um monitor, tente usar um adaptador de vídeo virtual. Esse é um dispositivo que se conecta ao DisplayPort do PC e emula uma exibição do computador.

## <a name="getting-the-best-performance"></a>Obtendo o melhor desempenho

Algumas configurações de hardware podem causar problemas de desempenho com a realidade mista do Windows. Para problemas como carregamento lento, visuais instável ou baixa qualidade visual, experimente estas correções comuns:

* Feche todos os aplicativos abertos em execução na área de trabalho do seu PC.
* Se você estiver usando um USB-C ou um DisplayPort para adaptador HDMI, tente um diferente. Consulte adaptadores recomendados
* Se houver monitores extras conectados à placa gráfica do PC, desconecte-os.
* Tente baixar alguns aplicativos de realidade misturados diferentes da Windows Store – alguns podem funcionar melhor com a configuração do computador.

> [!NOTE]
> Se você vir uma mensagem dizendo "esta configuração de hardware pode funcionar com a realidade mista do Windows, mas ela ainda não foi testada", você poderá encontrar alguns problemas de desempenho ao executar a realidade mista do Windows para sessões longas.

## <a name="see-also"></a>Veja também

* [Pergunte à comunidade](https://answers.microsoft.com)
* [Entre em contato conosco para obter suporte](https://support.microsoft.com/contactus/)
* [Solução de problemas](troubleshooting-windows-mixed-reality.md)