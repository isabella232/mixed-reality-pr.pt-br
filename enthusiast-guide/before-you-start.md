---
title: Antes de começar
description: Como garantir que seu PC seja compatível com o e pronto para o Windows Mixed Reality.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, compatível, compatibilidade, introdução, instalação, PC, requisitos do sistema
appliesto:
- Windows 10
ms.openlocfilehash: f4743b6548def227675944fcd742b1596963cb3c
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725487"
---
# <a name="before-you-start"></a>Antes de começar

## <a name="what-youll-need-to-run-windows-mixed-reality"></a>O que você precisará para executar a realidade mista do Windows

* Uma [exibição montada do HMD (Windows Mixed Reality)](https://www.microsoft.com/en-us/windows/windows-mixed-reality-devices).
* Um novo [PC do Windows Mixed Reality Ready](https://support.microsoft.com/en-us/help/4039260/windows-10-mixed-reality-pc-hardware-guidelines) ou um PC compatível com o Windows Mixed Reality que executa o Windows 10 versão 1709 ou posterior.
* Uma conexão com a Internet
* Adaptadores de vídeo, USB e Bluetooth (se não forem criados em headset ou computador)
* Os controladores de movimento, um controlador Xbox ou um mouse e um teclado
* Fones de ouvido com um microfone (se seu HMD não os tiver interno)
* Um espaço grande e aberto

## <a name="make-sure-your-pc-is-compatible-with-windows-mixed-reality"></a>Verifique se seu PC é compatível com a realidade mista do Windows

Verifique os [requisitos mínimos de hardware do PC do Windows Mixed Reality](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) ou execute o [portal do Windows Mixed Reality](install-windows-mixed-reality.md#launch-mixed-reality-portal) em seu PC para verificar a compatibilidade com o Windows Mixed Reality.

Leia sobre [problemas de compatibilidade do PC](https://support.microsoft.com/help/4045777/windows-10-get-help-with-pc-compatibility-in-windows-mixed-reality) para obter mais detalhes.

## <a name="make-sure-you-have-the-windows-10-version-1709-or-newer-installed"></a>Verifique se você tem o Windows 10 versão 1709 ou mais recente instalado

Você deve estar executando o Windows 10 versão 1903 ou mais recente para usar a realidade mista do Windows. As versões compatíveis do Windows 10 incluem:

* Windows 10 versão 1903
* Windows 10 versão 1909
* Windows 10 versão 2004
* Windows 10 versão 20H2

Para ver qual versão do Windows 10 seu dispositivo está executando no momento, selecione o botão **Iniciar** e, em seguida, selecione **configurações > > do sistema**.

Para garantir que o Windows 10 esteja atualizado em seu computador, selecione o botão **Iniciar** e, em seguida, selecione **configurações > atualização & segurança > Windows Update**.  Selecione **Verificar se há atualizações**. Se houver atualizações disponíveis, instale-as.

Confira [manter seu computador atualizado](https://support.microsoft.com/help/12373/windows-update-faq) para obter mais informações.

## <a name="make-sure-your-pc-is-connected-to-the-internet"></a>Verifique se o computador está conectado à Internet

Verifique se seu computador está conectado à Internet e baixe drivers e qualquer software adicional para colocar a realidade mista do Windows em funcionamento.

## <a name="make-sure-you-have-a-compatible-graphics-driver"></a>Verifique se você tem um driver gráfico compatível

Seu computador precisa de um driver de gráficos WDDM 2,2 ou posterior para concluir a configuração do Windows Mixed Reality. Se ele ainda não tiver um driver gráfico compatível, experimente estas fontes:

* Verifique as atualizações de driver críticas mais recentes usando Windows Update (**iniciar > configurações do Windows > atualização e segurança > verificar** se há atualizações)
* Verifique as atualizações de driver opcionais mais recentes:
    1. Clique com o botão direito do mouse em **iniciar > Device Manager**.
    2. Expanda **adaptadores de vídeo**.
    3. Clique com o botão direito do mouse na placa gráfica e escolha **Atualizar driver > Pesquisar automaticamente para software de driver atualizado**.
* Verifique o fabricante do seu PC no site (OEM).
* Verifique o fabricante do site da placa gráfica em seu PC (por exemplo, AMD, Intel ou NVIDIA).

## <a name="make-sure-that-you-have-any-required-adapters"></a>Verifique se você tem todos os adaptadores necessários

Seu PC compatível com realidade mista do Windows pode não ter o HDMI completo e as portas USB 3,0 necessárias para conectar o headset de imersão. Você também pode precisar de um adaptador Bluetooth para atender aos requisitos do portal de realidade mista do Windows.  Se esse for o caso, você precisará de adaptadores para conectar seus controladores de headset e de movimento. Certifique-se de examinar a lista de [tipos de adaptador e recomendações sobre modelos de adaptadores específicos](recommended-adapters-for-windows-mixed-reality-capable-pcs.md).

## <a name="make-sure-that-you-have-input-devices"></a>Verifique se você tem dispositivos de entrada

A realidade mista do Windows foi projetada para funcionar melhor com os controladores de movimento de realidade mista do Windows, que fornecem interações naturais e precisas, sem a necessidade de instalar o hardware em suas paredes. Mas você também pode usar um controlador Xbox ou um mouse e um teclado.

## <a name="make-sure-that-you-have-a-large-open-space"></a>Verifique se você tem um espaço grande aberto

Se você quiser se movimentar enquanto usa a realidade mista do Windows, precisará ter um espaço grande aberto.  Durante a instalação, será solicitado que você escolha entre "colocado e em pé" ou "todas as experiências". Escolha "todas as experiências" e configure um limite se desejar se movimentar. Examine as [diretrizes de integridade, segurança e conforto do headset](wmr-health-safety-comfort.md) para entender os requisitos de espaço.

### <a name="seated-and-standing-no-boundary"></a>Sentado e em posição (sem limite)

Se você selecionar "colocado e posicionado", você usará o headset sem um limite. Isso significa que você precisará permanecer em um ponto ao usar o headset para evitar obstáculos físicos e ultrapassar os riscos. Você pode sentar ou se destacar, mas não deve se mover. Alguns aplicativos podem ser projetados para funcionar com um limite, portanto, eles podem não funcionar ou fornecer a mesma experiência se você usá-los sem um.

### <a name="all-experiences-boundary"></a>Todas as experiências (limite)

Se você escolher "todas as experiências", configurará um limite e poderá se movimentar em experiências de aplicativos que funcionam com um limite e aqueles que não exigem um. Prepare seu espaço certificando-se de que não haja obstáculos, riscos ou itens frágeis na área que você usará-incluindo acima da sua cabeça. Não configure na parte superior de uma escada ou em um ventilador de teto extra-baixo. Remova breakables e obstáculos da área e certifique-se de que todos que usam o headset Leia e entenda as [diretrizes de segurança](https://support.microsoft.com/en-us/help/4039969/windows-10-mixed-reality-immersive-headset-health-safety-comfort).

## <a name="see-also"></a>Consulte também

* [Conecte seu HMD](plug-in-your-headset.md)
* [Requisitos mínimos de hardware do PC](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md)
* [Adaptadores recomendados](recommended-adapters-for-windows-mixed-reality-capable-pcs.md)