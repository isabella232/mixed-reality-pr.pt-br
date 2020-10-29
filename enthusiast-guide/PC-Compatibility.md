---
title: Aplicativo de verificação de PC do Windows Mixed Reality
description: Como localizar e usar o aplicativo de verificação de PC do Windows Mixed Reality para testar a compatibilidade do seu PC antes de comprar um headset de realidade mista do Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, compatível, compatibilidade, PC, requisitos do sistema
appliesto:
- Windows 10
ms.openlocfilehash: 5cf84768984691c253a557f6576685e89fb61078
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675178"
---
# <a name="windows-mixed-reality-pc-check-app"></a>Aplicativo de verificação de PC do Windows Mixed Reality

O aplicativo **[Windows Mixed Reality Check PC](windows-mixed-reality-pc-check-app.md)** é a melhor maneira de garantir que seu PC esteja pronto para executar a realidade mista do Windows. 

<a href="https://www.microsoft.com/store/productid/9NZVL19N7CNC"><img alt="Download Windows Mixed Reality PC Check app" src="images/WMR-PC-Check-app.png"/></a>

Depois de executar o aplicativo, você receberá uma das seguintes mensagens:
* **Você está pronto para começar.** Seu PC tem o que é necessário para executar a realidade mista do Windows.
* **Você está quase lá.** Este computador pode ser capaz de executar a realidade mista do Windows, mas alguns recursos podem ser limitados.
* **Não é possível executar a realidade misturada.** Este computador não atende aos requisitos mínimos necessários para executar a realidade mista do Windows.

Em seguida, você obterá uma análise do seu PC em relação ao hardware, aos drivers e ao sistema operacional necessários.
![Captura de tela da verificação de PC do Windows Mixed Reality](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>ícone</th><th>O que significa</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Seu PC passa o item necessário.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Pode haver problemas com seu PC para o requisito fornecido. Se você encontrar problemas, talvez seja necessário solucionar problemas ou atualizar seu computador.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Seu PC não atende aos requisitos do item especificado.</td>
</tr>
</table>

## <a name="get-help-with-windows-mixed-reality-pc-check-results"></a>Obtenha ajuda com o Windows Mixed Reality resultados da verificação do PC

Quando você configura a realidade mista do Windows ou executa o aplicativo de verificação do PC do Windows Mixed Reality no seu computador, você receberá um relatório sobre se o seu PC está pronto para executá-lo. Aqui estão alguns detalhes sobre o que você pode ver. 

### <a name="youre-good-to-go"></a>![Você está pronto para começar](images/glyph-succeeded.png)

Boas notícias – seu PC pode executar a realidade mista do Windows. Mas tenha em mente que ainda há variação entre o hardware e a configuração do computador, portanto, a experiência de realidade mista pode não ser a mesma em todos os PCs. 

>[!NOTE]
>Se você vir uma mensagem dizendo "esta configuração de hardware pode funcionar com a realidade mista do Windows, mas ela ainda não foi testada", você poderá encontrar alguns problemas de desempenho ao executar a realidade mista do Windows para sessões longas.


### <a name="youre-nearly-there"></a>![Você está quase lá](images/glyph-warning.png)

Seu PC deve ser capaz de executar a realidade mista do Windows, mas pode não fornecer a melhor experiência possível. Os gráficos podem atrasar, alguns aplicativos e jogos podem não funcionar bem, e alguns podem não ser executados. 

Aqui estão as mensagens que você pode ver e o que fazer sobre elas:

#### <a name="this-pc-has-an-integrated-graphics-card-with-single-channel-ram"></a>Este computador tem uma placa gráfica integrada com RAM de canal único.

Placas gráficas integradas fornecerão a melhor experiência de realidade misturada do Windows em PCs com RAM de canal duplo. Se você tiver problemas de desempenho, tente um dos seguintes:

* Instale uma [placa gráfica discreta compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Instale um pente de RAM adicional para criar uma RAM de canal duplo. 
* Alterne para um [computador compatível](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).

#### <a name="this-pc-has-a-hybrid-graphics-configuration-with-an-incompatible-pcie-link"></a>Este computador tem uma configuração gráfica híbrida com um link PCIe incompatível.

O PCIe significa *interconexão de componentes de periféricos Express* . Essa é a conexão que um computador usa para se comunicar com uma placa gráfica. Sua configuração pode funcionar, mas se você tiver problemas, será necessário alternar para um [computador compatível](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-graphics-driver-might-not-work-well-with-windows-mixed-reality"></a>O driver gráfico do PC pode não funcionar bem com a realidade mista do Windows.

Se você tiver problemas, tente baixar um novo driver de gráficos usando Windows Update ( **iniciar > configurações > atualizar & segurança > verificar se há atualizações** ) — ou vá para o site fabricante do PC ou fabricante da placa gráfica. 

Se isso não funcionar, você precisará adicionar uma [placa gráfica compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou alternar para um [PC compatível](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).

#### <a name="this-pcs-processor-might-not-work-well-with-windows-mixed-reality"></a>O processador deste computador pode não funcionar bem com a realidade mista do Windows.

O processador deste computador pode não funcionar bem com a realidade mista do Windows, pois não tem núcleos suficientes. Se a realidade mista do Windows não for bem executada, substitua o processador por um [compatível](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou mude para um [PC compatível](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).

#### <a name="this-pc-might-not-have-a-compatible-usb-configuration"></a>Este computador pode não ter uma configuração de USB compatível.

Se você tiver problemas ao executar a realidade mista do Windows, tente o seguinte:
* Conecte seu headset em uma porta USB diferente, se disponível.
* Se isso não funcionar, desinstale o driver USB atual do PC e reinstale um driver da Microsoft:
1. Selecione **Iniciar** e, em seguida, digite **"Gerenciador de dispositivos"** na caixa de pesquisa.
1. Selecione **Device Manager** nos resultados.
1. Expanda a categoria para controladores de barramento serial universal, examine os dispositivos listados e desinstale os drivers incompatíveis. 
 * Se a lista incluir um item de "controlador de host extensível" que não tenha "Microsoft" no final do nome do dispositivo, esse driver não será compatível com a realidade mista do Windows. Você precisará desinstalá-lo. Para desinstalar um driver, clique com o botão direito do mouse no dispositivo na lista e selecione **desinstalar dispositivo** . Marque a caixa de seleção **excluir o software do driver para este dispositivo** e selecione **desinstalar** .
 * Se a lista incluir um item de "controlador de host extensível" que inclui "Etron" no nome, esse controlador USB não será compatível com a realidade mista do Windows. Você precisará usar uma porta USB diferente no PC ou adquirir um controlador de host USB 3,0 diferente.
1. Reinicie o computador. 
1. Retorne para Device Manager e localize o item do controlador de host extensível novamente. Se agora você vir "Microsoft" no final do nome do dispositivo, você está pronto para começar. Caso contrário, repita as etapas de desinstalação para remover quaisquer versões adicionais que não sejam da Microsoft do driver.
* Se isso ainda não funcionar, adicione uma placa USB PCIe ao seu PC.

#### <a name="this-pc-doesnt-have-bluetooth-40-for-controllers"></a>Este computador não tem o Bluetooth 4,0 para controladores.

#### <a name="this-pc-doesnt-have-a-self-powered-usb-port"></a>Este computador não tem uma porta USB autoalimentada.

#### <a name="this-pc-should-work-but-youll-have-the-best-experience-with-a-high-performance-intel-processor"></a>Este computador deve funcionar, mas você terá a melhor experiência com um processador Intel® de alto desempenho.

### <a name="cant-run-mixed-reality"></a>![Não é possível executar a realidade misturada](images/glyph-error.png)

 [Obtenha ajuda com o Windows Mixed Reality resultados da verificação do PC](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)
