---
title: Perguntas frequentes de exibição do headset
description: Solução de problemas avançada do Windows Mixed realm para problemas de exibição de fone de ouvido que vão além da nossa documentação de suporte padrão do consumidor.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte
appliesto:
- Windows 10
ms.openlocfilehash: a3e30f8706228e64b118ee399f4129d186d1fd94
ms.sourcegitcommit: 24d96bf3bb9a3143445e018195edae99d91684c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683202"
---
# <a name="headset-display-faqs"></a>Perguntas frequentes de exibição do headset

## <a name="my-headset-displays-are-black"></a>Minhas telas de headset são pretas.

* Verifique o desempenho e a estabilidade do seu PC:
    * Use o Gerenciador de tarefas para ver se algum processo está maximizandondo a CPU, a GPU e/ou as unidades de disco do seu PC.
    * Verifique os logs de "aplicativo" e "sistema" em **Visualizador de Eventos > logs do Windows** para ver se você tem um aplicativo com frequência que está falhando e gerando relatórios de relatório de erros do Windows (WER).
    * Verifique Windows Update para certificar-se de que sua versão do Windows está atualizada. Talvez seja necessário selecionar "verificar atualizações" várias vezes.
* Verificar a estabilidade do aplicativo e do jogo:
    * Verifique se o seu PC atende aos requisitos mínimos do sistema para executar qualquer aplicativo ou jogo que não esteja executando corretamente.    
    * Verifique se a versão do driver de GPU é recente e verifique se há novos problemas de desempenho e compatibilidade e regressões sobre novos drivers.
    * Se você estiver usando aplicativos e jogos do SteamVR, verifique se o SteamVR e o Windows Mixed Reality for SteamVR Components estão atualizados.
* Verifique a compatibilidade do adaptador HDMI:
    * Verifique se o cabo HDMI está conectado a todo o caminho.
    * Se você estiver usando um adaptador HDMI (por exemplo, um Mini DisplayPort para adaptador HDMI), verifique se ele é compatível com a realidade mista do Windows. O adaptador deve oferecer suporte a HDMI 2,0 e há muitos adaptadores mais antigos que dão suporte apenas a 1080p. Consulte [adaptadores recomendados para a realidade mista do Windows](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
    * A ordem de plugue pode ser importante. Conecte o adaptador HDMI ao seu computador antes de conectar o headset ao adaptador, especialmente se você estiver usando um USB-C para adaptador HDMI. 
    * Tente remover os cabos de extensão se você os estiver usando.
* Verifique a placa gráfica e a compatibilidade do driver:
    * Experimente a porta HDMI do seu PC com um monitor de PC. Alguns PCs podem ter mais de uma porta HDMI, e nem todas podem estar ativas.
    * Se o seu PC tiver uma iGPU (unidade de processamento gráfico) integrada e uma dGPU (unidade de processamento gráfico discreto), verifique se você está conectado à porta HDMI de dGPU.<br> ![Portas HDMI](images/HP_HDMI_Ports_s.png)
    * Verifique a versão do driver de GPU. Verifique se ele é recente, mas também preste atenção a quaisquer novos problemas de desempenho e compatibilidade e regressões em novos drivers.
    * Se você estiver usando realidade mista em um laptop e tiver instalado um driver de gráficos mais recente no site do fabricante da placa de gráficos, tente fazer o downgrade para o driver de placa gráfica mais recente fornecido no site do fabricante do seu PC ou em Windows Update.
    * Se você tiver vários monitores de PC conectados ao seu PC, tente desconectar temporariamente todos, exceto um monitor de PC.
    * Se você tiver definido uma taxa de atualização personalizada para o monitor do seu PC, tente reverter temporariamente para uma taxa de atualização padrão, como 60Hz.
    * Se você alterou recentemente a placa gráfica sem reinstalar o Windows, verifique se o monitor Headset ainda tem o driver correto instalado. Com o fone de ouvido conectado, confirme que "a realidade mista" está listado no nó monitores em Device Manager.
    * Se o seu PC tiver uma placa gráfica Nvidia, verifique se o software de visão 3D da NVIDIA está desabilitado.
    * Em algumas placas gráficas (especialmente cartões mais antigos), a porta HDMI pode não oferecer suporte a HDMI 2,0 ou pode não ser totalmente compatível com a realidade mista do Windows. Tente usar o DisplayPort da placa gráfica com um [adaptador de displayport 1,2 para HDMI 2,0](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
    * Os PCs HP Omen com o número de produto HP 1RJ99EA # ABU têm portas HDMI incompatíveis com a realidade mista do Windows (Abra o "Assistente de suporte HP" e o número será listado na parte inferior do aplicativo).
    * Se o seu PC tiver uma placa gráfica AMD série R9 e você estiver usando um headset de realidade mista Samsung, atualize o firmware do headset para a versão 1.0.8 ou mais recente para usar a porta HDMI da placa gráfica com o headset.
    * Se você estiver usando um livro de superfície 2, verifique se está usando a [superfície USB-C para o adaptador HDMI](https://docs.microsoft.com/windows/mixed-reality/enthusiast-guide/recommended-adapters-for-windows-mixed-reality-capable-pcs).
* Verifique se há um problema de hardware de headset de realidade misturada:
    * Para confirmar ou eliminar problemas de hardware com o headset, conecte o headset de realidade misturada a outro PC. 
    * Verifique a compatibilidade do PC e os problemas de instalação primeiro, pois os sintomas são muito semelhantes.
* Verifique se o cabo USB está conectado a uma porta USB 3,0 ou mais rápida. As portas USB 3,0 têm SS (super velocidade) ao lado delas e geralmente são azuis coloridas.        

Essas informações também são exibidas em um [fluxograma de solução de problemas](headset-display-chart.md).

## <a name="my-headset-display-occasionally-turns-black-after-some-use"></a>Minha exibição do headset ocasionalmente fica preta após algum uso.

* Tente desabilitar qualquer recurso de suspensão ou de economia de USB em seu computador. Por exemplo, em **configurações > sistema > Power & Sleep > a [suspensão seletiva USB](https://docs.microsoft.com/windows-hardware/drivers/usbcon/usb-selective-suspend)** , a configuração "permitir que o computador desligue este dispositivo para economizar energia" em Device Manager e quaisquer configurações de economia de energia USB no firmware do seu PC.
* Desconecte temporariamente quaisquer outros dispositivos USB e periféricos conectados ao seu PC.
* Verifique se a versão do driver de GPU é recente e verifique se há novos problemas de desempenho e compatibilidade e regressões sobre novos drivers.

## <a name="one-of-the-displays-on-my-headset-is-black"></a>Um dos monitores no meu Headset é preto.

* Se você estiver usando um adaptador HDMI, verifique se ele oferece suporte a HDMI 2,0.
* Remova todos os cabos de extensão de USB e HDMI que você possa estar usando.
* Verifique se o driver de gráficos está atualizado.
* Experimente o headset de realidade misturada em outro PC.

## <a name="my-headset-displays-turn-blue-and-then-mixed-reality-portal-reinitializes"></a>Meu Headset exibe azul e, em seguida, o portal da realidade misturada é reinicializado.

Isso normalmente indica um problema de confiabilidade ocasional do controlador USB em seu PC:
* Tente outra porta USB. Seu computador pode ter vários controladores USB 3,0.
* Remova todos os cabos de extensão (se aplicável).
* Desconecte todos os outros dispositivos USB do seu PC.
* Conecte um hub USB 3,0 com alimentação externa ao seu PC e conecte o headset ao Hub.
* Se você estiver usando um PC desktop, considere comprar uma placa USB 3,0 PCIe para adicionar outro controlador USB ao seu PC.

## <a name="my-headset-causes-my-pc-to-hang-or-show-a-black-screen-while-starting-up"></a>Meu Headset faz com que meu PC trave ou mostre uma tela preta durante a inicialização.

Em alguns PCs, deixar o headset conectado antes de ligar ou durante a reinicialização do computador pode interferir no processo de inicialização. Seu PC pode selecionar o headset exibido como o "monitor principal" para mostrar o progresso da inicialização do PC, não iniciar corretamente ou "travar" e/ou produzir um código de erro de bipe. O comportamento depende da marca e do modelo do PC e/ou da marca e do modelo da placa gráfica. Para corrigir isso:
* Conecte seu headset a uma porta diferente na placa gráfica (talvez seja necessário usar um adaptador para usar as outras portas).
* Verifique se o firmware BIOS/UEFI do computador está atualizado (mas Atualize apenas o firmware BIOS/UEFI do seu PC se você estiver familiarizado com isso).

## <a name="my-pc-or-headset-displays-flicker-flash-or-remain-black-when-using-a-surface-pc"></a>Meu PC ou headset exibe cintilação, flash ou permanece preto ao usar um PC de superfície.

* Verifique se você está usando um adaptador HDMI que dá suporte a HDMI 2,0. Muitos adaptadores HDMI mais antigos dão suporte apenas à resolução de 1080p, o que é insuficiente para headsets de realidade misturada.
* Verifique se o driver de gráficos está atualizado. Verifique Windows Update e o site do fabricante do PC para obter um driver de gráficos atualizado.
* Alguns dispositivos de superfície são incompatíveis com a realidade mista do Windows. Saiba mais sobre [compatibilidade e requisitos da superfície](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md#windows-mixed-reality-and-surface).

## <a name="my-headset-display-doesnt-work-after-i-shut-down-and-do-a-fast-startup"></a>Minha exibição de headset não funciona depois de desligar e fazer uma inicialização rápida.

Desconecte o cabo HDMI e o cabo USB do headset e, em seguida, conecte-os novamente.

## <a name="my-headset-displays-are-very-choppy-but-mixed-reality-portals-preview-window-appears-fine"></a>Minhas exibições de headset estão muito ruins, mas a janela de visualização do portal de realidade misturada aparece bem.

* Verifique se os recursos do sistema do PC (CPU, memória e disco rígido) estão disponíveis e não consumidos por outro aplicativo ou processo.
* Atualize o driver de gráficos.

## <a name="im-getting-a-the-install-class-is-not-present-or-is-invalid-error-in-device-manager"></a>Estou recebendo um erro "a classe de instalação não está presente ou é inválido" em Device Manager.

Se você vir "sensores do HoloLens" com um ponto de exclamação amarelo em Device Manager, selecione o dispositivo para obter detalhes adicionais. Se você vir uma mensagem dizendo "os drivers para este dispositivo não estão instalados. (Código 28)--a classe de instalação não está presente ou é inválida ", isso normalmente ocorre porque seu computador está executando o [Windows 10 N](https://support.microsoft.com/en-us/help/4039813/media-feature-pack-for-windows-10-n-october-2017). Observe que N edições do Windows 10 não oferecem suporte à realidade mista do Windows, e você precisará instalar uma versão não-N do Windows 10.

## <a name="my-wmr-environment-is-jittery-or-stutters-when-i-move-my-head-and-displays-double-vision"></a>Meu ambiente do WMR é de tremulação ou de falhas quando eu movo o meu cabeçalho e exibe a visão dupla.

Em um laptop com gráficos integrados e uma GPU NVIDIA, um erro ocorre depois de um período de tempo que parece fazer com que um quadro anterior seja exibido após o próximo quadro, resultando em uma visão dupla do mais rápido que você move a sua cabeça em uma guinada, uma inclinação ou uma movimentação de rolagem. O problema parece estar em drivers após o driver de gráficos NVIDIA 436,48.  A instalação desse driver corrigirá o problema até que o NVIDIA resolva o problema nos drivers atualizados. Para uma instalação direta do driver de gráficos NVIDIA 436,48, visite [NVIDIA](https://www.nvidia.com/Download/driverResults.aspx/152007/en-us).

## <a name="im-uncomfortable-in-my-headset"></a>Estou desconfortável em meu headset.
Para obter informações gerais sobre o conforto na realidade misturada do Windows, consulte [integridade de fone de ouvido de imersão, segurança e conforto do Windows Mixed Reality](wmr-health-safety-comfort.md). Para obter detalhes sobre o fone de ouvido específico, verifique com o fabricante do headset.

## <a name="how-can-i-get-a-clearer-view-in-my-headset"></a>Como posso obter uma exibição mais clara em meu Headset?
Tente ajustar o ajuste do seu headset. Mova-o para cima e para baixo, ou para a esquerda e para a direita, em sua face e ajuste as pulseiras para que fique perfeitamente.

Se o headset tiver um botão para ajustar a calibragem, ajuste suas configurações de calibragem. Se não estiver, vá para **configurações > realidade misturada > qualidade visual** e ajuste a calibragem lá. Para obter mais informações sobre a calibragem para seu dispositivo específico, verifique com o fabricante do headset.

## <a name="i-frequently-see-a-black-border-around-the-view-in-the-headset-sometimes-its-like-im-looking-down-a-tunnel"></a>Eu vejo com frequência uma borda preta em torno da exibição no headset. Às vezes, é como estou procurando um túnel.

Isso significa que o aplicativo não pode pressionar a taxa de quadros em seu computador e o sistema está usando quadros antigos para renderizar a exibição no headset. Como os aplicativos só renderizam a parte do mundo que você está vendo, se eles não atingirem suas taxas de quadros de forma consistente, o sistema tentará renderizar o mundo a partir de um ponto de vista anterior e preencherá os detalhes ausentes com preto. Se isso ocorrer com frequência:
1. Fechar ou encerrar todos os programas desnecessários para liberar memória e CPU.
2. Reduza as configurações de detalhes em seu aplicativo.
3. Vá para **configurações > realidade misturada > tela de headset** para reduzir a quantidade de detalhes mostrada na página inicial do Windows Mixed Reality.

## <a name="the-view-in-the-headset-is-jittering-and-stuttering-a-lot"></a>O modo de exibição do headset está se estremindo e se esficando muito.

O sistema pode não ser capaz de renderizar o conteúdo para o headset ou o sistema de controle pode estar tendo problemas. Verifique o seguinte:
1. Abra o Gerenciador de tarefas para certificar-se de que seu computador tem recursos de computação suficientes. Você deve ter 80% de CPU livre, 400 MB de RAM e e/s de disco devem estar abaixo de 80%.
2. Verifique se você tem os drivers gráficos mais recentes para seu hardware. Consulte a [seção driver de gráficos](before-you-start.md#make-sure-you-have-a-compatible-graphics-driver).
3. Verifique se a sala tem luz suficiente.
4. Desconecte o dispositivo, feche a realidade mista do Windows e conecte-o novamente.
5. Reinicie o computador.
6. Se o problema persistir, entre em contato com o atendimento [ao cliente](https://support.microsoft.com/).
