---
title: Windows Mixed Reality Diretrizes de compatibilidade do PC
description: Gráfico de visão geral que descreve os requisitos mínimos de sistema do PC para compatibilidade com o Windows Mixed Reality.
author: qianw211
ms.author: v-qianwen
ms.date: 09/22/2021
ms.topic: article
keywords: Windows Mixed Reality, realidade mista, realidade Virtual, VR, sr, Ultra, compatível, compatibilidade, requisitos do sistema, PC
appliesto:
- Windows 10 and Windows 11
ms.openlocfilehash: af3228e76bc9ce54ef877b67e8e85a3bde25e140
ms.sourcegitcommit: c159bdcf2ada1f45606b10d41ea3adf95109c979
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2021
ms.locfileid: "129436725"
---
# <a name="windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines"></a>diretrizes mínimas de compatibilidade de hardware do PC Windows Mixed Reality

![Imagem do Hero de compatibilidade de PC](images/pc-comp-hero.png)

## <a name="features-and-experiences"></a>Recursos e experiências

o Windows 10 e o Windows 11 capacitam o Windows Mixed Reality em vários headsets em um conjunto diversificado de hardware de PC.  O poder do seu PC determinará quais experiências você pode ter.
Com os PCs de ponta mais altos, você obtém alguns recursos e recursos adicionais:

* Visuais mais nítidos e uma taxa de atualização mais alta.
* Mais aplicativos e experiências, incluindo os jogos com uso intensivo de gráficos.
* Uma janela ' ' espelho ' ' na área de trabalho que mostra o que você vê em realidade misturada.
* Registre e compartilhe vídeos e fotos de suas experiências de realidade misturada.

## <a name="minimum-pc-hardware-guidelines"></a>Diretrizes mínimas de hardware para PC

veja se seu computador pode executar Windows Mixed Reality examinando as diretrizes de hardware abaixo e executando o aplicativo de [Portal de realidade misturada](https://www.microsoft.com/store/apps/9NG1H8B3ZC7M) .

Lembre-se de que seu desempenho irá variar dependendo da configuração exata. você também precisará certificar-se de que seu PC tem as [portas corretas](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) para o Windows Mixed Reality headset de imersão que você está usando.

>[!NOTE]
>As diretrizes para PCs de desenvolvimento são maiores do que aquelas para PCs de consumidores que executam aplicativos de realidade misturada. Se você for um desenvolvedor de realidade misturada, [consulte especificações de PC de desenvolvimento recomendadas](https://developer.microsoft.com/en-us/windows/mixed-reality/install_the_tools#immersive_headset_development).

## <a name="mixed-reality-portal-app"></a>Aplicativo do portal da realidade mista

O [portal de realidade misturada](https://www.microsoft.com/store/productid/9ng1h8b3zc7m) é a melhor maneira de garantir que seu PC esteja pronto para execução Windows Mixed Reality.

Depois de executar o aplicativo, você receberá uma das seguintes mensagens:

* **Você está pronto para começar.**  Seu PC está pronto para executar jogos e experiências de realidade misturada.
* **Dá suporte a alguns recursos.** Seu PC pode executar algumas experiências de realidade misturada.
* **Não é possível executar a realidade misturada.** Este computador não atende aos requisitos mínimos necessários para executar o Windows Mixed Reality.

Em seguida, você obterá uma análise do seu PC em relação ao hardware, aos drivers e ao sistema operacional necessários.
![captura de tela da verificação do Windows Mixed Reality PC](images/screenshot-mr-pc-check.jpg)

| Ícone | O que significa |
| --- | --- |
| <img alt="Succeeded" width="30" height="30" src="images/glyph-succeeded.png" /> | Seu PC passa o item necessário. |
| <img alt="Warning" width="30" height="30" src="images/glyph-warning.png" /> | Pode haver problemas com seu PC para o requisito fornecido. Se você tiver problemas, talvez seja necessário solucionar problemas ou atualizar seu PC. 
| <img alt="Error" width="30" height="30" src="images/glyph-error.png" /> | Seu computador não atende aos requisitos do item especificado. |

 [Obter ajuda com resultados do portal de realidade misturada](get-help-with-pc-compatibility.md)

## <a name="compatibility-guidelines"></a>Diretrizes de compatibilidade

> [!IMPORTANT]
> atualizaremos, fazendo adições e podem ser revisando essas Windows Mixed Reality diretrizes de compatibilidade do computador. Consulte regularmente para obter as diretrizes e os requisitos mais recentes.

### <a name="high-resolution-headset-requirements"></a>Requisitos de headset de alta resolução

Devido à resolução mais alta, os requisitos a seguir se aplicam às linhas de produtos da HP de reverbo G1, G2 e Omnicept para garantir o ideal de 90 Hz, experiência de resolução completa:

- Intel Core i5, i7, Intel Xeon E3-1240 V5, equivalente ou melhor. AMD Ryzen 5 equivalente ou melhor.  
- NVIDIA GeForce GTX 1080, AMD Radeon RX 5700, equivalente ou melhor  
- Memória: 8 GB de RAM ou mais  
- 1x porta de vídeo 1,3  
- 1x USB 3,0 tipo-C com entrega de energia (ou adaptador de energia incluído) 
- Windows 10 Atualização 2019 de maio ou posterior  
 
**Todos os outros headsets compatíveis com WMR** <br>
Para todos os outros HMDs, consulte os seguintes requisitos:

| | Windows Mixed Reality PCs 90Hz | Windows Mixed Reality 60 PCs |
| --- | --- | --- |
| Sistema operacional | Windows 10 Fall Creators Update (RS3) ou posterior-página inicial, Pro, negócios, educação. <br/>    (<b>observação</b>: sem suporte em N versões ou Windows 10 Pro no modo S) |
| Processador | Intel Core i5 4590 (4ª geração), Quad-Core (ou melhor) <br> AMD Ryzen 5 1400 de 3,4 GHz (Desktop), Quad-Core (ou melhor) | Intel Core i5 7200u (7ª geração móvel), dual-core com a tecnologia Intel Hyper-Threading habilitada (ou melhor) <br> AMD Ryzen 5 1400 de 3,4 GHz (Desktop), Quad-Core (ou melhor) |
| RAM | 8 GB de DDR3 (ou melhor) | canal duplo DDR3 de 8 GB (ou melhor) |
| Espaço livre em disco | Pelo menos 10 GB | Pelo menos 10 GB |
| Placa gráfica| <ul> <li>NVIDIA GTX 1060 (ou superior) GPU discreta compatível com DX12 </li> <li>GPU discreta compatível com DX12 AMD RX 470/570 (ou superior) </li> </ul> <br> <b>Observação:</b> A GPU deve ser hospedada em um slot de link PCIe 3,0 X4 + |  <ul>  <li>GPU integrada Intel HD Graphics 620 (ou superior) com capacidade para DX12 <a href="https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units">(verifique se o modelo é maior)</a></li> <li>GPU discreta NVIDIA MX150 (ou superior)</li> <li>GPU discreta NVIDIA GeForce GTX 1050</li> <li>GPU discreta de NVIDIA 965M</li> <li>AMD Radeon RX 460/560</li> </ul> <b>Observação:</b> Não há suporte para GPUs Intel mais antigas, como gráficos de HD 4xx, 5xx, 2xxx, 3xxx, 4xxx, 5xxx e 6xxx. |
| Driver de gráficos | Windows WDDM (modelo de driver de vídeo) 2,2 |  |
| [Porta de exibição de gráficos](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | HDMI 2,0 ou DisplayPort 1,2 | HDMI 1,4 ou DisplayPort 1,2 |
| Exibir | Vídeo conectado externo ou integrado VGA (800x600) (ou melhor) | 
| [Conectividade USB](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) | USB 3.0 | |
| conectividade de Bluetooth (para [controladores de animação](controllers-in-wmr.md) | Bluetooth 4,0 | |
| Taxa de quadros de headset esperada | 90 Hz | 60 Hz |
| Energia | Portas USB 3,0 | Portas USB 3,0 |

**Informações adicionais:**

* Laptops maiores com telas de, pelo menos, 15 "fazem o melhor.
* as configurações de gráficos híbridos são compatíveis apenas com Windows Mixed Reality 90Hz. o adaptador gráfico discreto em qualquer configuração híbrida deve atender a todos os requisitos listados nas diretrizes de Windows Mixed Reality para adaptadores de gráficos discretos.
* se você tiver uma placa gráfica discreta que deve ser executada Windows Mixed Reality 90Hz, mas estiver padronizando para uma taxa de atualização de 60 (60 quadros por segundo), use um DisplayPort de tamanho completo para adaptador HDMI 2,0 para conectar seu headset e habilitar uma taxa de atualização de 90Hz.
* Headsets diferentes podem exigir portas de hardware diferentes, portanto, verifique se o computador tem as portas corretas ou os [adaptadores necessários](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) para se conectar ao headset.

>[!NOTE]
>Hardware gráfico discreto e integrado que não atendem às especificações mínimas confirmadas não foram testados, confirmados ou otimizados para Windows Mixed Reality e podem não funcionar corretamente ou de forma alguma.

## <a name="windows-mixed-reality-and-surface"></a>Windows Mixed Reality e Surface

Para a melhor Windows Mixed Reality em um dispositivo Surface, recomendamos o SurfaceBook (15") mais recente configurado com pelo menos o NVIDIA GeForce GTX 1060 GB e 16 GB de RAM.  Essa configuração dá suporte a Windows Mixed Reality recursos e foi testada para Windows Mixed Reality.  O Surface Book mais recente (13,5"), Surface Studio, Surface Laptop e Surface Pro (2017) dará suporte a alguns recursos do Windows Mixed Reality quando configurados com uma CPU Intel Core i5 (ou melhor) e pelo menos 8 GB de RAM.

**Requisitos:**

* Os produtos surface exigem que as atualizações de driver sejam compatíveis com Windows Mixed Reality. Esses drivers podem ser instalados no Surface Configurações > atualização e > **verificar se há atualizações.**
* Os produtos [](Recommended-adapters-for-Windows-Mixed-Reality-Capable-PCs.md) surface exigem um adaptador da porta de vídeo (Mini DisplayPort ou USB-C, dependendo do Surface PC) para HDMI 2.0 para headsets Windows Mixed Reality vídeo. A versão mais recente do Surface Mini-DisplayPort adaptador AV do HDMI é compatível com o HDMI 2.0 (a versão mais antiga não é). Da mesma forma, o <a href="https://www.microsoft.com/en-us/store/d/surface-usb-c-to-hdmi-adapter/94chb2m80s54/4gj5">Adaptador USB-C</a> do Surface para HDMI também é compatível com o HDMI 2.0.

## <a name="see-also"></a>Confira também

* [Pergunte à comunidade](https://answers.microsoft.com)
* [Entre em contato conosco para ter suporte](https://support.microsoft.com/contactus/)
* [Adaptadores recomendados para Windows Mixed Reality PCs com capacidade](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
