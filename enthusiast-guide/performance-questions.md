---
title: Perguntas frequentes sobre o desempenho
description: Desempenho do Windows Mixed Realm insolução de problemas que vão além da nossa documentação de suporte do consumidor padrão.
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte, desempenho
appliesto:
- Windows 10
ms.openlocfilehash: d6b37f8f6c964222b90fff57f0ba994c14fcaeab
ms.sourcegitcommit: 2da7e181e4e23eed31b59f0332c3ba8b3f594cd0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2020
ms.locfileid: "93131960"
---
# <a name="performance-faqs"></a>Perguntas frequentes sobre o desempenho

## <a name="is-my-windows-mixed-reality-headset-rendering-at-60hz-or-90hz-framerate"></a>Meu processamento de headset de realidade mista do Windows é a renderização de fone de ouvido de 60 ou 90Hz

Se você tiver uma GPU discreta com portas HDMI 2,0 e uma CPU com quatro ou mais núcleos físicos, deverá obter 90 Hz. Para confirmar, verifique a guia **desempenho do portal do dispositivo >** .

Observação: se sua GPU tiver apenas uma saída HDMI 1,4, você poderá usar um DisplayPort para [adaptador HDMI 2,0](recommended-adapters-for-windows-mixed-reality-capable-pcs.md) como solução alternativa.

Observação: as configurações de qualidade visual em "exibição do headset" afetam apenas a renderização da experiência inicial do Windows Mixed Reality.

## <a name="my-pc-is-running-slowly"></a>Meu PC está sendo executado lentamente

O sistema pode estar lento por vários motivos e, na maioria dos casos, apenas alguns segundos. Se você tiver esse problema por longos períodos de tempo:

1. Feche todos os aplicativos não utilizados na área de trabalho.
2. Verifique se o seu laptop está conectado a uma fonte de alimentação.
3. Verifique se o PC não está aquecendo.
4. Reduza a qualidade visual na sua página inicial do Windows Mixed Reality.
5. Verifique se você tem os [drivers gráficos](other-questions.md#my-graphics-driver-isnt-supported-im-getting-graphics-driver-failure-errors) mais recentes para seu computador.

## <a name="my-pc-is-warming-up-as-i-run-the-mixed-reality-experiences-how-do-i-keep-it-cool"></a>Meu PC está se aquecendo enquanto eu executo as experiências de realidade misturada. Como fazer mantê-lo interessante

1. Verifique se a bateria é cobrada e se a fonte de alimentação está conectada.
2. Verifique se os fãs do PC não estão bloqueados.
3. Use o PC em um ambiente relativamente interessante.
4. Verifique se não há fontes de calor (por exemplo, as aberturas do sol ou do calor) apontadas para o PC.

## <a name="my-visuals-are-choppy-load-slowly-or-dont-look-good"></a>Meus elementos visuais estão instável, carregam lentamente ou não parecem bons

* Verifique se o headset está conectado à placa gráfica correta no seu computador. Alguns PCs têm placas gráficas integradas e discretas. O cartão discreto geralmente oferecerá o melhor desempenho. [Saiba mais sobre hardware de PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md).
* Feche os aplicativos não utilizados na sua área de trabalho.
* Verifique se o fone de ouvido se ajusta perfeitamente (Mova-o para baixo e para cima, ou para a esquerda e para a direita, para ajustar).
* Ajuste as configurações visuais do headset em **configurações > realidade misturada > tela de headset** . Quando "qualidade visual" é definido como "automático", a experiência de realidade mista para seu PC será escolhida automaticamente. Para obter mais detalhes sobre o Visual, defina "qualidade visual" como "alta". Se os visuais estiverem ruins, selecione uma configuração mais baixa.
* Ajuste o botão de calibragem de Headset para garantir que as lentes sejam definidas com a distância correta entre o Pupils (chamado de IPD). Se você não souber seu IPD, um optometrist deverá ser capaz de medir para você ou usar um site projetado para medir o IPD. Se o headset não tiver um botão de calibragem, selecione **configurações > realidade misturada > tela de headset** e ajuste o "controle de calibragem".
* Se você estiver usando um USB-C ou um DisplayPort para adaptador HDMI, tente um diferente. Consulte [adaptadores recomendados.](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)
* Desconecte os monitores adicionais que podem estar conectados à placa gráfica do seu PC.
* Experimente alguns aplicativos diferentes de realidade misturada da Windows Store – alguns podem funcionar melhor com a configuração do computador.
