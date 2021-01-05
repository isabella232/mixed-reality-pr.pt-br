---
title: Diretrizes mínimas de compatibilidade de hardware do PC do Windows Mixed Reality
description: Gráfico que descreve os requisitos mínimos de sistema do PC para compatibilidade com a realidade mista do Windows.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, ultra, compatível, compatibilidade, requisitos do sistema, PC
appliesto:
- Windows 10
ms.openlocfilehash: bd287e2089056be56330c2c2e8e9af2c079009ac
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725657"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Diretrizes mínimas de compatibilidade de hardware do PC do Windows Mixed Reality

## <a name="features-and-experiences"></a>Recursos e experiências

O Windows 10 impulsiona a realidade mista do Windows e o Windows Mixed Reality ultra. Qual versão você enfrentará depende do hardware do seu PC.

Com o Windows Mixed Reality ultra, você obtém alguns recursos e recursos adicionais:

* Visuais mais nítidos e uma taxa de atualização mais alta (90 quadros por segundo).
* Mais aplicativos e experiências, incluindo os jogos com uso intensivo de gráficos.
* Uma janela ' ' espelho ' ' na área de trabalho que mostra o que você vê em realidade misturada.
* Registre e compartilhe vídeos e fotos de suas experiências de realidade misturada.

## <a name="minimum-pc-hardware-guidelines"></a>Diretrizes mínimas de hardware para PC

Para obter a melhor experiência com a realidade mista do Windows, comece com um novo [PC pronto para a realidade mista do Windows](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) ou um PC compatível com a realidade mista do Windows que pode fornecer ultra experiências do Windows Mixed Reality. A realidade mista do Windows oferece visuais mais nítidos a taxas de atualização mais altas, mais experiências de aplicativos, incluindo os jogos com uso intensivo de gráficos, espelhamento de sua experiência de realidade mista do Windows em sua área de trabalho e a capacidade de registrar e compartilhar (foto e vídeo) suas experiências com outras pessoas. 

Veja se seu computador pode executar a realidade mista do Windows examinando as diretrizes de hardware abaixo e executando o [aplicativo de portal de realidade misturada](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M).

Lembre-se de que seu desempenho irá variar dependendo da configuração exata. Você também precisará certificar-se de que seu PC tem as [portas certas](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para o headset de imersão de realidade mista do Windows que você está usando.

>[!NOTE]
>As diretrizes para PCs de desenvolvimento são maiores do que aquelas para PCs de consumidores que executam aplicativos de realidade misturada. Se você for um desenvolvedor de realidade misturada, [consulte especificações de PC de desenvolvimento recomendadas](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development).


## <a name="mixed-reality-portal-app"></a>Aplicativo do portal da realidade mista

O portal de realidade misturada é a melhor maneira de garantir que seu PC esteja pronto para executar a realidade mista do Windows. 

<a href="https://www.microsoft.com/store/productid/9ng1h8b3zc7m"><img alt="Download Mixed Reality Portal" src="images/WMR-PC-Check-app.png"/></a>

Depois de executar o aplicativo, você receberá uma das seguintes mensagens:
* **Você está pronto para começar.** Seu PC tem o que é necessário para executar a realidade mista do Windows.
* **Dá suporte a alguns recursos.** Este computador pode executar a realidade mista do Windows, mas alguns recursos podem ser limitados.
* **Não é possível executar a realidade misturada.** Este computador não atende aos requisitos mínimos necessários para executar a realidade mista do Windows.

Em seguida, você obterá uma análise do seu PC em relação ao hardware, aos drivers e ao sistema operacional necessários.
![Captura de tela da verificação de PC do Windows Mixed Reality](images/screenshot-mr-pc-check.jpg) 

<table>
<tr>
<th>ícone</th><th>O que significa</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">Seu PC passa o item necessário.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Pode haver problemas com seu PC para o requisito fornecido. Se você tiver problemas, talvez seja necessário solucionar problemas ou atualizar seu PC.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">Seu computador não atende aos requisitos do item especificado.</td>
</tr>
</table>

 [Obter ajuda com resultados do portal de realidade misturada](https://support.microsoft.com/en-us/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality)

## <a name="compatibility-guidelines"></a>Diretrizes de compatibilidade
> [!IMPORTANT]
> Atualizaremos, fazendo adições e podem ser revisando essas diretrizes de compatibilidade de PCs com a realidade mista do Windows. Consulte regularmente para obter as diretrizes e os requisitos mais recentes.

**Especificações compatíveis com o HP reverbs**<br>
Devido à resolução mais alta, os seguintes requisitos se aplicam às linhas de produtos HP reverbs G1 & G2 para garantir o ideal de 90 Hz, experiência de resolução completa: 

<ul>
<li> Intel Core i5, i7, Intel xenônio E3-1240 V5, equivalente ou melhor. AMD Ryzen 5 equivalente ou melhor. </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente ou melhor </li> 
<li> Memória: 8 GB de RAM ou mais </li> 
<li> 1x porta de vídeo 1,3 </li> 
<li> 1x USB 3,0 tipo-C com entrega de energia (ou adaptador de energia incluído)</li>
<li> Windows 10 pode 2019 atualização ou posterior </li>
</ul>

**Todos os outros headsets compatíveis com WMR** <br>
Para todos os outros HMDs, consulte os seguintes requisitos: 

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality ultra PCs</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Computadores Windows Mixed Reality</th>
</tr><tr>
    <td style="vertical-align: middle">Sistema operacional</td><td colspan="2" style="vertical-align: middle; text-align: center;">RS3 (Windows 10 outono Creators Update) ou posterior-Home, pro, Business, Education.<br/>    (<b>Observação</b>: sem suporte em N versões ou Windows 10 pro no modo S)</td>
</tr><tr>
    <td style="vertical-align: middle">Processador</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4ª geração), Quad-Core (ou melhor) <br>AMD Ryzen 5 1400 de 3,4 GHz (Desktop), Quad-Core (ou melhor)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200u (7ª geração móvel), dual-core com a tecnologia Intel Hyper-Threading habilitada (ou melhor) <br>AMD Ryzen 5 1400 de 3,4 GHz (Desktop), Quad-Core (ou melhor)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB de DDR3 (ou melhor)</td>
    <td style="vertical-align: middle; text-align: center;">canal duplo DDR3 de 8 GB (ou melhor)</td>
</tr><tr>
    <td style="vertical-align: middle">Espaço livre em disco</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Pelo menos 10 GB</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Pelo menos 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">Placa gráfica</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul> 
            <li>NVIDIA GTX 1060 (ou superior) GPU discreta compatível com DX12</li>
            <li>GPU discreta compatível com DX12 AMD RX 470/570 (ou superior) </li>
            </ul>     
            <b>Observação:</b> A GPU deve ser hospedada em um slot de link PCIe 3,0 X4 + </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>GPU integrada Intel HD Graphics 620 (ou superior) com capacidade para DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(verifique se o modelo é maior)</a></li>
        <li>GPU discreta NVIDIA MX150 (ou superior)</li>
        <li>GPU discreta NVIDIA GeForce GTX 1050</li>
        <li>GPU discreta de NVIDIA 965M</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>Observação:</b> Não há suporte para GPUs Intel mais antigas, como gráficos de HD 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx e 6xxx.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Driver de gráficos</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Display Driver Model (WDDM) 2,2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Porta de exibição de gráficos</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2,0 ou DisplayPort 1,2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1,4 ou DisplayPort 1,2</td>
</tr><tr>
    <td style="vertical-align: middle">Monitor</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Vídeo conectado externo ou integrado VGA (800x600) (ou melhor)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Conectividade USB</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">Tipo USB 3,0-A </td>
</tr><tr>
    <td style="vertical-align: middle">Conectividade Bluetooth (para <a href="controllers-in-wmr.md">controladores de animação</a>)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4,0</td>
</tr><tr>
    <td style="vertical-align: middle">Taxa de quadros de headset esperada</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Energia</td>
    <td style="vertical-align: middle; text-align: center;">Portas USB 3,0 (tipo A)</td>
    <td style="vertical-align: middle; text-align: center;">Portas USB 3,0 (tipo A)</td>
</tr>
</table>



**Informações adicionais:**
* Laptops maiores com telas de, pelo menos, 15 "fazem o melhor.
* Para obter a melhor experiência, recomendamos um processador Intel® Core de 8 gen™ ou 7ª Gen Intel® Core™ i5.
* As configurações de gráficos híbridos são compatíveis apenas com o Windows Mixed Reality ultra. O adaptador gráfico discreto em qualquer configuração híbrida deve atender a todos os requisitos listados nas diretrizes de realidade mista do Windows para adaptadores de gráficos discretos.
* Se você tiver uma placa gráfica discreta que deve executar o Windows Mixed Reality ultra, mas estiver padronizando para uma taxa de atualização de 60 Hz (60 quadros por segundo), use um DisplayPort de tamanho completo para adaptador HDMI 2,0 para conectar seu headset e habilitar uma taxa de atualização de 90 Hz.
* Headsets diferentes podem exigir portas de hardware diferentes, portanto, verifique se o computador tem as portas corretas ou os [adaptadores necessários](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) para se conectar ao headset.

>[!NOTE]
>Hardware de gráficos discretos e integrados que não atendem às especificações confirmadas mínimas não foram testados, confirmados ou otimizados para a realidade mista do Windows e podem não funcionar corretamente ou de nenhuma forma.

## <a name="windows-mixed-reality-and-surface"></a>Superfície e realidade do Windows Mixed

Para a melhor experiência de realidade mista do Windows em um dispositivo de superfície, recomendamos o SurfaceBook 2 (15 ") configurado com o NVIDIA GeForce GTX 1060 GB e 16 GB de RAM.  Essa configuração dá suporte a todos os recursos do Windows Mixed Reality @ 90 Hz e foi testada e com notificação para o Windows Mixed Reality ultra.  O livro de superfície 2 (13 "), o Surface Studio, o Surface laptop e o Surface pro (2017) oferecerão suporte a alguns recursos de realidade mista do Windows quando configurados com uma CPU Intel Core i5 (ou melhor) e pelo menos 8 GB de RAM.

**Requisitos:**
* Produtos de superfície exigem atualizações de driver para serem compatíveis com a realidade mista do Windows. Esses drivers podem ser instalados em sua superfície acessando **configurações > atualização e segurança > verificar** se há atualizações.
* Produtos de superfície exigem um [adaptador](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) da porta de vídeo (Mini DisplayPort ou USB-C, dependendo do PC de superfície) até o HDMI 2,0 para headsets de realidade misturada do Windows. A versão mais recente da superfície Mini-DisplayPort ao adaptador HDMI AV é compatível com o HDMI 2,0 (a versão mais antiga não é). Da mesma forma, o <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">adaptador de superfície USB-C para HDMI</a> também é compatível com HDMI 2,0.

>[!WARNING]
>Nem todos os adaptadores Mini DisplayPort ou USB-C para HDMI são compatíveis com HDMI 2,0. Considere a verificação da compatibilidade explícita "HDMI 2,0" ou de "4K" em qualquer adaptador.

Mais informações sobre a compatibilidade de superfície com a realidade mista do Windows estão disponíveis na tabela a seguir:

<table>
    <tr>
        <th> Dispositivo de superfície </th><th> Suporte ao recurso de realidade mista do Windows? </th><th> Configuração recomendada </th><th> Observações</th>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface pro (original)/Surface Pro 2 </td><td style="vertical-align: middle"> Nenhum </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Pro 3 </td><td style="vertical-align: middle"> Nenhum </td><td> </td><td></td>
    </tr>
(com o Windows 10 Pro instalado) <tr>
        <td style="vertical-align: middle"> Surface Pro 4 </td><td style="vertical-align: middle"> Nenhum </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface 3 </td><td style="vertical-align: middle"> Nenhum </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Book </td><td style="vertical-align: middle"> Nenhum </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Livro de superfície com base de desempenho </td><td style="vertical-align: middle"> Nenhum </td><td> </td><td></td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Go </td><td style="vertical-align: middle"> Nenhum </td><td> </td><td></td>
    </tr>
<tr>
        <td style="vertical-align: middle"> Livro de superfície 2 (15 &quot; ) </td><td style="vertical-align: middle"> Completo </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1060/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Recomendado</b>: para a melhor experiência de realidade mista do Windows em um dispositivo de superfície, recomendamos o SurfaceBook 2 15 "configurado com o NVIDIA GeForce GTX 1060 GB e 16 GB de RAM.  Essa configuração é testada e crachá como o Windows Mixed Reality ultra, portanto, dará suporte a todos os recursos do Windows Mixed Reality e permitirá que você aproveite a mais ampla matriz de aplicativos e jogos compatíveis.</li>
                <li>A GPU discreta NVIDIA GeForce GTX 1060 fornecerá uma experiência com o Windows Mixed Reality ultra @ 90-Hz</li><br/>                <li>Para obter o melhor desempenho, use os drivers gráficos NVIDIA lançados para o livro de superfície 2. Drivers mais recentes podem estar disponíveis no site do NVIDIA&#39;s, mas não são testados.</li><br/>                <li>Requer <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">a superfície USB-C para o adaptador HDMI</a> (outros adaptadores podem funcionar, mas não são testados)</li>
                <li><b>Observação no encaixe de superfície</b>: o uso de encaixe de superfície com o livro de superfície 2 não é oficialmente suportado com a realidade mista do Windows, devido às limitações da fonte de alimentação do Dock Station.</li><br/>                <li><b>Observação sobre o Windows 10 versão 1803</b>: se você&#39;executando novamente o Windows 10 versão 1803, certifique-se de&#39;novamente o Build do sistema operacional 17134,137 ou mais recente (instalado pelo KB4284848) para garantir que você tenha as correções de desempenho mais recentes. Para obter mais informações, consulte as notas de versão do <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Livro de superfície 2 (13,5 &quot; ) </td><td style="vertical-align: middle"> Parcial </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GTX 1050/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Observação</b>: o livro de superfície 2 (13 ") não é crachá para a realidade mista do Windows, mas dará suporte a alguns recursos do Windows Mixed Reality, permitindo que você use um número limitado de aplicativos e jogos compatíveis.  O desempenho dependerá de sua configuração.</li>
                <li>As configurações com uma GPU integrada Intel Core i5/Intel HD Graphics 620 fornecerão uma experiência mista do Windows de 60 a Hz</li>
                <li>As configurações com uma GPU discreta do Intel Core i7/NVIDIA GeForce GTX 1050 fornecerão uma experiência Windows Mixed Realm a 90 Hz</li>                       <li>Para obter o melhor desempenho, use os drivers gráficos NVIDIA lançados para o livro de superfície 2. Drivers mais recentes podem estar disponíveis no site do NVIDIA&#39;s, mas não são testados.</li>
                <li>Requer <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">a superfície USB-C para o adaptador HDMI</a> (outros adaptadores podem funcionar, mas não são testados)</li>
                <li><b>Observação no encaixe de superfície</b>: o uso de encaixe de superfície com o livro de superfície 2 não é oficialmente suportado com a realidade mista do Windows, devido às limitações da fonte de alimentação do Dock Station.</li>
                <li><b>Observação sobre o Windows 10 versão 1803</b>: se você&#39;executando novamente o Windows 10 versão 1803, certifique-se de&#39;novamente o Build do sistema operacional 17134,137 ou mais recente (instalado pelo KB4284848) para garantir que você tenha as correções de desempenho mais recentes. Para obter mais informações, consulte as notas de versão do <a href="https://support.microsoft.com/en-us/help/4284848/windows-10-update-kb4284848">KB4284848</a>.</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface Studio </td><td style="vertical-align: middle"> Parcial </td><td style="vertical-align: middle"> Intel Core i7/NVIDIA GeForce GTX 980m/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Observação</b>: o Surface Studio não é crachá para a realidade mista do Windows, mas dará suporte a alguns recursos do Windows Mixed Reality, permitindo que você use um número limitado de aplicativos e jogos compatíveis.  O desempenho dependerá de sua configuração.</li>
                <li>As configurações com NVIDIA GeForce GTX 965 m fornecerão uma experiência de realidade mista do Windows @ 60 Hz.</li>
                <li>As configurações com NVIDIA GeForce GTX 980 m fornecerão uma experiência de realidade mista do Windows @ 90 Hz.</li>
                <li>Mini DisplayPort da superfície para adaptador HDMI 2,0 (outros adaptadores podem funcionar, mas não são testados)</li>
                <li>O headset da realidade mista do Windows deve estar conectado à porta USB com o símbolo "+"</li>
            </ul>
        </td>
    </tr>
    <tr>
        <td style="vertical-align: middle"> Surface pro (2017) </td><td style="vertical-align: middle"> Parcial </td><td style="vertical-align: middle"> Intel Core i7/Intel® íris™ mais gráficos 640/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Observação</b>: o Surface Pro (2017) não é crachá para a realidade mista do Windows, mas dará suporte a alguns recursos de realidade mista do Windows, permitindo que você use um número limitado de aplicativos e jogos compatíveis.  O desempenho dependerá de sua configuração.</li>
                <li><b>Não há suporte para</b> as configurações com uma GPU integrada Intel Core m3/Intel HD Graphics 615</li>
                <li>As configurações com uma GPU integrada Intel Core i5/Intel HD Graphics 620 fornecerão uma experiência mista do Windows de 60 a Hz</li>
                <li>As configurações com um Intel Core i7/Intel® íris™ Plus Graphics 640 GPU integrada fornecerão uma experiência Windows Mixed realm de 60 a Hz</li><br/><li>Requer o Mini DisplayPort da superfície para o adaptador HDMI 2,0 (outros adaptadores podem funcionar, mas não são testados)</li>
                <li>Requer o <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">controle deslizante de desempenho</a> definido como "melhor desempenho" durante o uso</li>
            </ul>
        </td>
    </tr><br/>    <tr>
        <td style="vertical-align: middle"> Surface Laptop </td><td style="vertical-align: middle"> Parcial </td><td style="vertical-align: middle"> Intel Core i7/Intel® íris™ mais gráficos 640/16 GB de RAM </td>
        <td>
            <ul>
                <li><b>Observação</b>: o laptop da superfície não é crachá para a realidade mista do Windows, mas dará suporte a alguns recursos do Windows Mixed Reality, permitindo que você use um número limitado de aplicativos e jogos compatíveis.  O desempenho dependerá de sua configuração.</li>
                <li><b>Não há suporte para</b> as configurações com uma GPU integrada Intel Core m3/Intel HD Graphics 615</li>
                <li>As configurações com uma GPU integrada Intel Core i5/Intel HD Graphics 620 fornecerão uma experiência mista do Windows de 60 a Hz</li>
                <li>As configurações com um Intel Core i7/Intel® íris™ Plus Graphics 640 GPU integrada fornecerão uma experiência Windows Mixed realm de 60 a Hz</li><br/><li>Requer o Mini DisplayPort da superfície para o adaptador HDMI 2,0 (outros adaptadores podem funcionar, mas não são testados)</li>
                <li>Requer o <a href="https://support.microsoft.com/en-us/help/4023450/surface-surface-battery-and-power">controle deslizante de desempenho</a> definido como "melhor desempenho" durante o uso</li>
            </ul>
        </td>
    </tr>
</table>

## <a name="see-also"></a>Consulte também
* [Pergunte à comunidade](https://answers.microsoft.com)
* [Entre em contato conosco para obter suporte](https://support.microsoft.com/contactus/)
* [Adaptadores recomendados para PCs com capacidade do Windows Mixed Reality](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
