---
title: Windows Mixed Reality Diretrizes de compatibilidade do computador
description: Gráfico de visão geral que apresenta os requisitos mínimos do sistema de PC para compatibilidade com Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/16/2020
ms.topic: article
keywords: Windows Mixed Reality, Realidade Misturada, Realidade Virtual, VR, MR, Ultra, compatível, compatibilidade, requisitos do sistema, PC
appliesto:
- Windows 10
ms.openlocfilehash: b7c2b4b84440e7cdd22c2c0cd7d5f9830d55625f
ms.sourcegitcommit: 9831b89a1641ba1b5df14419ee2a4f29d3fa2d64
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2021
ms.locfileid: "114757024"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>Windows Mixed Reality diretrizes mínimas de compatibilidade de hardware do pc

![Imagem hero de compatibilidade do computador](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>Recursos e experiências

Windows 10 o Windows Mixed Reality em uma variedade de headsets em um conjunto diversificado de hardware de computador.  O poder do computador determinará quais experiências você pode ter.
Com PCs de extremidade superior, você pode obter alguns recursos e funcionalidades adicionais:

* Visuais mais nítidos e uma taxa de atualização mais alta.
* Mais aplicativos e experiências, incluindo os jogos com maior uso intensivo de gráficos.
* Uma janela ''espelho'' na área de trabalho que mostra o que você vê na realidade misturada.
* Grave e compartilhe vídeos e fotos de suas experiências de realidade misturada.

## <a name="minimum-pc-hardware-guidelines"></a>Diretrizes mínimas de hardware para PC

Veja se o computador pode executar Windows Mixed Reality, revendo as diretrizes de hardware abaixo e executando o [Portal de Realidade Misturada](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) aplicativo.

Lembre-se de que o desempenho variará dependendo da configuração exata. Você também precisará garantir que o [](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) computador tenha as portas certas para o headset Windows Mixed Reality imersivo que você está usando.

>[!NOTE]
>As diretrizes para PCs de desenvolvimento são maiores do que aquelas para os PCs dos consumidores que executam aplicativos de realidade misturada. Se você for um desenvolvedor de realidade misturada, [confira especificações recomendadas do PC de desenvolvimento.](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development)

## <a name="mixed-reality-portal-app"></a>Portal de Realidade Misturada aplicativo

[Portal de Realidade Misturada](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) é a melhor maneira de garantir que o computador esteja pronto para ser executado Windows Mixed Reality.

Depois de executar o aplicativo, você obterá uma das seguintes mensagens:

* **Você pode ir.**  Seu computador está pronto para executar experiências e jogos de realidade misturada.
* **Dá suporte a alguns recursos.** Seu computador pode executar algumas experiências de realidade misturada.
* **Não é possível executar a realidade misturada.** Esse computador não atendem aos requisitos mínimos necessários para executar Windows Mixed Reality.

Em seguida, você obterá uma análise do computador em relação ao hardware, drivers e sistema operacional necessários.
![Captura de tela da Windows Mixed Reality pc](images/screenshot-mr-pc-check.jpg)

<table>
<tr>
<th>ícone</th><th>O que significa</th>
</tr><tr>
<td> <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /></td><td style="vertical-align: middle">O computador passa o item necessário.</td>
</tr><tr>
<td> <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /></td><td style="vertical-align: middle">Pode haver problemas com seu computador para o requisito determinado. Se você encontrar problemas, talvez seja necessário solucionar problemas ou atualizar seu computador.</td>
</tr><tr>
<td> <img alt="Error" width="30" height="30" src="images/glyph-error.png" /></td><td style="vertical-align: middle">O computador não atendem aos requisitos do item especificado.</td>
</tr>
</table>

 [Obter ajuda com Portal de Realidade Misturada resultados](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Diretrizes de compatibilidade

> [!IMPORTANT]
> Vamos atualizar, fazer adições e talvez revisando essas diretrizes de compatibilidade Windows Mixed Reality PC. Verifique regularmente as diretrizes e os requisitos mais recentes.

### <a name="high-resolution-headset-requirements"></a>Requisitos de headset de alta resolução

Devido à resolução mais alta, os seguintes requisitos se aplicam às linhas de produto HP Reverb G1, G2 e Omnicept para garantir uma experiência ideal de resolução completa de 90 Hz:

<ul>
<li> Intel Core i5, i7, Intel Xeon E3-1240 v5, equivalente ou melhor. AMD Ryzen 5 equivalente ou melhor. </li>
<li> NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente ou melhor </li>
<li> Memória: 8 GB de RAM ou mais </li>
<li> 1x Porta de Exibição 1.3 </li>
<li> 1x USB 3.0 Type-C com entrega de energia (ou adaptador de energia incluído)</li>
<li> Windows 10 Atualização de maio de 2019 ou posterior </li>
</ul>

**Todos os outros headsets compatíveis com WMR** <br>
Para todos os outros HMDs, consulte os seguintes requisitos:

<table>
<tr>
    <th style="width:10%"></th><th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality PCs de 90Hz</th>
    <th style="vertical-align: middle; text-align: center; width:30%">Windows Mixed Reality PCs de 60Hz</th>
</tr><tr>
    <td style="vertical-align: middle">Sistema operacional</td><td colspan="2" style="vertical-align: middle; text-align: center;">Windows 10 Fall Creators Update (RS3) ou posterior – Home, Pro, Business, Education.<br/>    (<b>Observação:</b>não há suporte para N versões ou Windows 10 Pro no modo S)</td>
</tr><tr>
    <td style="vertical-align: middle">Processador</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 4590 (4ª geração), quad-core (ou melhor) <br>AMD Ryzen 5 1400 3.4Ghz (desktop), quad-core (ou melhor)</td>
    <td style="vertical-align: middle; text-align: center;">Intel Core i5 7200U (7ª geração móvel), núcleo duplo com a Tecnologia intel Hyper-Threading habilitada (ou melhor) <br>AMD Ryzen 5 1400 3.4Ghz (desktop), quad-core (ou melhor)</td>
</tr><tr>
    <td style="vertical-align: middle">RAM</td>
    <td style="vertical-align: middle; text-align: center;">8 GB DDR3 (ou melhor)</td>
    <td style="vertical-align: middle; text-align: center;">Canal duplo DDR3 de 8 GB (ou melhor)</td>
</tr><tr>
    <td style="vertical-align: middle">Espaço livre em disco</td>
    <td style="vertical-align: middle; text-align: center;">Pelo menos 10 GB</td>
    <td style="vertical-align: middle; text-align: center;">Pelo menos 10 GB</td>
</tr><tr>
    <td style="vertical-align: middle">Placa gráfica</td>
    <td style="vertical-align: middle; text-align: middle;">
            <ul>
            <li>NVIDIA GTX 1060 (ou superior) GPU discreta com capacidade para DX12</li>
            <li>GPU discreta com capacidade para DX12 amd RX 470/570 (ou superior) </li>
            </ul>
            <b>Observação:</b> A GPU deve ser hospedada em um slot de link PCIe 3.0 x4+ </td>
    <td style="vertical-align: middle; text-align: middle;">
            <li>GPU integrada integrada do Intel HD Graphics 620 (ou superior) com capacidade para DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(verifique se o modelo é maior)</a></li>
        <li>GPU discreta NVIDIA MX150 (ou superior)</li>
        <li>GPU discreta do Nvidia GeForce GTX 1050</li>
        <li>GPU discreta do Nvidia 965M</li>
        <li>AMD Radeon RX 460/560</li>
        </ul>
        <b>Observação:</b> Não há suporte para GPUs Intel mais antigas, como HD Graphics 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx e 6xxx.
    </td>
</tr><tr>
    <td style="vertical-align: middle">Driver de elementos gráficos</td>
    <td colspan="3" td style="vertical-align: middle; text-align: center;">Windows Modelo de driver de exibição (WDDM) 2.2</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Porta de exibição de gráficos</a></td>
    <td style="vertical-align: middle; text-align: center;">HDMI 2.0 ou DisplayPort 1.2</td>
    <td style="vertical-align: middle; text-align: center;">HDMI 1.4 ou DisplayPort 1.2</td>
</tr><tr>
    <td style="vertical-align: middle">Monitor</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Exibição VGA externa ou integrada conectada (800x600) (ou melhor)</td>
</tr><tr>
    <td style="vertical-align: middle"><a href="Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md">Conectividade USB</a></td>
    <td colspan="2" style="vertical-align: middle; text-align: center;">USB 3.0 </td>
</tr><tr>
    <td style="vertical-align: middle">Bluetooth conectividade (para <a href="controllers-in-wmr.md">controladores de movimento</a>)</td>
    <td colspan="3" style="vertical-align: middle; text-align: center;">Bluetooth 4.0</td>
</tr><tr>
    <td style="vertical-align: middle">Taxa de quadros do headset esperada</td>
    <td style="vertical-align: middle; text-align: center;">90 Hz</td>
    <td style="vertical-align: middle; text-align: center;">60 Hz</td>
</tr>
<tr>
    <td style="vertical-align: middle">Energia</td>
    <td style="vertical-align: middle; text-align: center;">Portas USB 3.0</td>
    <td style="vertical-align: middle; text-align: center;">Portas USB 3.0</td>
</tr>
</table>

**Informações adicionais:**

* Laptops maiores com telas de pelo menos 15" fazem o melhor.
* As configurações de elementos gráficos híbridos são compatíveis apenas com Windows Mixed Reality 90Hz. O adaptador gráfico discreto em qualquer configuração híbrida deve atender a todos os requisitos listados nas diretrizes Windows Mixed Reality para adaptadores gráficos discretos.
* Se você tiver uma placa gráfica discreta que deve executar o Windows Mixed Reality 90Hz, mas estiver definindo como padrão uma taxa de atualização de 60Hz (60 quadros por segundo), use um adaptador DisplayPort de tamanho completo para HDMI 2.0 para conectar o headset e habilitar uma taxa de atualização de 90Hz.
* Headsets diferentes podem exigir portas de hardware diferentes, portanto, certifique-se de que o computador tenha as portas corretas ou adaptadores [necessários](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) para se conectar ao headset.

>[!NOTE]
>hardware de gráficos discretos e integrados que não atendem às especificações confirmadas mínimas não foram testados, confirmados ou otimizados para Windows Mixed Reality e podem não funcionar corretamente ou de nenhuma forma.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality e superfície

para obter a melhor experiência de Windows Mixed Reality em um dispositivo de superfície, recomendamos o SurfaceBook (15 ") mais recente configurado com pelo menos o NVIDIA GeForce GTX 1060 GB e 16 GB de RAM.  essa configuração dá suporte a todos os recursos de Windows Mixed Reality e foi testada para Windows Mixed Reality.  a Surface Book mais recente (13,5 "), Surface Studio, Surface Laptop e Surface Pro (2017) dará suporte a alguns recursos de Windows Mixed Reality quando configurados com uma CPU Intel Core i5 (ou melhor) e pelo menos 8 GB de RAM.

**Requisitos:**

* Produtos de superfície exigem atualizações de driver para serem compatíveis com Windows Mixed Reality. esses drivers podem ser instalados em sua superfície acessando **Configurações > atualização e segurança > verificar** se há atualizações.
* produtos de superfície exigem um [adaptador](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) da porta de vídeo (Mini DisplayPort ou USB-C, dependendo do PC de superfície) até o HDMI 2,0 para Windows Mixed Reality headsets. A versão mais recente da superfície Mini-DisplayPort ao adaptador HDMI AV é compatível com o HDMI 2,0 (a versão mais antiga não é). Da mesma forma, o <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">adaptador de superfície USB-C para HDMI</a> também é compatível com HDMI 2,0.

## <a name="see-also"></a>Confira também

* [Pergunte à comunidade](https://answers.microsoft.com)
* [Entre em contato conosco para obter suporte](https://support.microsoft.com/contactus/)
* [adaptadores recomendados para Windows Mixed Reality PCs compatíveis](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
