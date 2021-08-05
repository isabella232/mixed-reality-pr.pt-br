---
title: Windows Mixed Reality Aplicativo de Verificação de PC
description: Como encontrar e usar o aplicativo Windows Mixed Reality pc check para testar a compatibilidade do computador antes de comprar um headset Windows Mixed Reality dispositivo.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, compatível, compatibilidade, PC, requisitos do sistema
appliesto:
- Windows 10
ms.openlocfilehash: 463e7dfc2c95ed9efc70a87ebbb0dac08b134251401a1114f3b9a364aa197073
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115188036"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Windows Mixed Reality Aplicativo de Verificação de PC

O **[Windows Mixed Reality pc check é](https://www.microsoft.com/store/p/windows-mixed-reality-pc-check/9nzvl19n7cnc)** a melhor maneira de verificar se o computador está pronto para ser executado Windows Mixed Reality. O Windows Mixed Reality pc check funciona apenas em computadores com pelo menos Windows 10 versão 1607 instalada. Para verificar sua versão do Windows, digite "winver" na barra de pesquisa e execute o comando . Para Windows 10 versões anteriores à 1607, o aplicativo ainda será aparecer na Store, mas você receberá um erro ao tentar instalar.

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Depois de executar o aplicativo, você obterá uma das seguintes mensagens:

* **Você pode ir.** Seu computador tem o que é necessário para executar Windows Mixed Reality.
* **Você está quase lá.** Esse computador pode ser executado Windows Mixed Reality, mas alguns recursos podem ser limitados.
* **Não é possível executar a realidade misturada.** Esse computador não atendem aos requisitos mínimos necessários para executar Windows Mixed Reality.

Em seguida, você obterá uma análise do computador em relação ao hardware, drivers e sistema operacional necessários.
![Captura de tela da Windows Mixed Reality pc](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>ícone</th><th>O que significa</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">O computador passa o item necessário.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Pode haver problemas com seu computador para o requisito determinado. Se você tiver problemas, talvez seja necessário solucionar problemas ou atualizar seu computador.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">O computador não atendem aos requisitos do item especificado.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Obter ajuda com os resultados Windows Mixed Reality PC

Você obterá um relatório de compatibilidade ao configurar o Windows Mixed Reality ou executar o aplicativo Windows Mixed Reality verificação de computador no computador. Aqui estão alguns detalhes sobre o que você pode ver.

### <a name="youre-good-to-go"></a>![Você pode ir](images/glyph-succeeded.png)

Boas notícias: seu computador pode ser executado Windows Mixed Reality. Tenha em mente que ainda há variação entre o hardware e a configuração do computador. A experiência de realidade misturada pode não ser a mesma em todos os computadores.

>[!NOTE]
>Se você vir uma mensagem que diz "Essa configuração de hardware pode funcionar com o Windows Mixed Reality, mas ela ainda não foi testada", você poderá ter alguns problemas de desempenho ao executar Windows Mixed Reality sessões longas.

### <a name="youre-nearly-there"></a>![Você está quase lá](images/glyph-warning.png)

Seu computador deve ser capaz de executar Windows Mixed Reality, mas pode não fornecer a melhor experiência possível. Os gráficos podem atrasar, alguns aplicativos e jogos podem não funcionar bem e alguns podem não ser executados.

Aqui estão as mensagens que você pode ver e o que fazer sobre elas:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este computador tem uma placa gráfica integrada com RAM de canal único

As placas gráficas integradas fornecerão a melhor Windows Mixed Reality em PCs com RAM de canal duplo. Se você tiver problemas de desempenho:

* Instale uma [placa gráfica discreta compatível.](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* Instale um stick de RAM adicional para criar RAM de canal duplo.
* Alternar para um [computador compatível.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este computador tem uma configuração de elementos gráficos híbridos com um link PCIe incompatível

PCIe significa *Interconnect Express de Componente Periférico*. Essa é a conexão que um computador usa para se comunicar com uma placa gráfica. Sua configuração pode funcionar, mas se você tiver problemas, precisará alternar para um [computador compatível.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>O driver gráfico desse computador pode não funcionar bem com Windows Mixed Reality

Se você tiver problemas, tente baixar um novo driver de gráficos usando a atualização do Windows ( Iniciar > Configurações > atualizar **&**> Verificar se há atualizações )– ou acesse o site do fabricante do computador ou do fabricante da placa gráfica.

Se isso não funcionar, você precisará adicionar uma placa [gráfica](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) compatível ou alternar para um [computador compatível.](https://www.microsoft.com/windows/windows-mixed-reality-devices)

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>O processador desse computador pode não funcionar bem com Windows Mixed Reality

O processador desse computador pode não funcionar bem com Windows Mixed Reality, pois ele não tem núcleos suficientes. Se Windows Mixed Reality não for bem executado, atualize para um compatível ou mude para um [computador compatível.](https://www.microsoft.com/windows/windows-mixed-reality-devices) [](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Esse computador pode não ter uma configuração USB compatível

Se você tiver problemas ao executar Windows Mixed Reality:

* Conecte o headset a uma porta USB diferente, se disponível.
* Se isso não funcionar, desinstale o driver USB atual do computador e reinstale um driver da Microsoft:

1. Selecione **Iniciar** e digite **"gerenciador de dispositivos"** na caixa Pesquisar.
1. Selecione **Gerenciador de Dispositivos** nos resultados.
1. Expanda a categoria para controladores do Barramento Serial Universal, veja os dispositivos listados e desinstale todos os drivers incompatíveis. 
 * Se a lista incluir um item "Controlador de Host eXtensible" sem "Microsoft" no final do nome do dispositivo, o driver não será compatível com Windows Mixed Reality. Você precisará desinstalá-lo. Para desinstalar um driver, clique com o botão direito do mouse no dispositivo na lista e selecione **Desinstalar o dispositivo**. Marque a **caixa de seleção Excluir o software do driver para** este dispositivo e, em seguida, selecione **Desinstalar**.
 * Se a lista incluir um item "Controlador de Host eXtensible" que inclui "Etron" no nome, esse controlador USB não será compatível com Windows Mixed Reality. Você precisará usar uma porta USB diferente no computador ou comprar um controlador de host USB 3.0 diferente.
1. Reinicie o computador. 
1. Retorne ao Gerenciador de Dispositivos e localize o item controlador de host eXtensible novamente. Se agora você vir "Microsoft" no final do nome do dispositivo, tudo bem. Caso não, repita as etapas de desinstalação para remover versões adicionais não Microsoft do driver.
* Se isso ainda não funcionar, adicione um cartão USB PCIe ao seu computador.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Esse computador não tem Bluetooth 4.0 para controladores.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Esse computador não tem uma porta USB auto-alimentada.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Esse computador deve funcionar, mas você terá a melhor experiência com um processador Intel de ® de alto desempenho.

### <a name="cant-run-mixed-reality"></a>![Não é possível executar a realidade misturada](images/glyph-error.png)

 [Obter ajuda com os resultados Windows Mixed Reality PC](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
