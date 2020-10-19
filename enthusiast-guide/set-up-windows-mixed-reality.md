---
title: Configurar o Windows Mixed Reality
description: Como configurar seus controladores de movimento, fala e áudio do Windows Mixed Reality e definir o limite da sala para um espaço de reprodução seguro.
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, introdução, instalação, controlador de movimento, controlador, fala, áudio, encaixado, posição, limites, drivers gráficos, Microsoft Edge, Chromium
ms.openlocfilehash: 71775ba03cb143b83f1a4514f62f20df903df96d
ms.sourcegitcommit: 5eb27475f8616c9d4f95b4b386a5bd0d22f41125
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2020
ms.locfileid: "92174461"
---
# <a name="set-up-windows-mixed-reality"></a>Configurar o Windows Mixed Reality

## <a name="get-ready"></a>Prepare-se

Para executar a realidade mista do Windows, você precisará de:

* Um headset de imersão de realidade mista compatível. [Saiba mais](https://www.microsoft.com/mixed-reality/windows-mixed-reality?rtc=1)
* Um [PC pronto para a realidade mista do Windows](windows-mixed-reality-minimum-pc-hardware-compatibility-guidelines.md) com as portas corretas para o headset
* [Controladores](controllers-in-wmr.md)de movimento, um controlador Xbox ou um mouse e um teclado
* Fones de ouvido com um MIC (se o headset não os tiver interno)
* Um espaço grande e aberto

## <a name="get-set"></a>Obter conjunto

Prepare seu espaço (incluindo o espaço de sobrecarga). Verifique se não há obstáculos, riscos ou itens frágeis na área que você usará. Não configure na parte superior de uma escada ou em um ventilador de teto extra-baixo. Remova breakables e obstáculos da área e certifique-se de que você e qualquer pessoa que usa seu headset Leia e entenda as [diretrizes de segurança](https://support.microsoft.com/help/4039969).

## <a name="go"></a>Vá!

Quando seu espaço estiver pronto, conecte seu headset, mas não o coloque de imediato — primeiro, precisaremos fazer alguma configuração em seu PC. Executaremos uma verificação de PC, baixaremos alguns softwares, conectaremos seus controladores e criaremos um [limite](boundary-questions.md) para ajudá-lo a evitar obstáculos.

Em seguida, vem a parte divertida — Coloque em seu headset e insira o mundo misto. A Cortana estará aguardando para você realizar um tour. Divirta-se!

## <a name="get-familiar-with-your-motion-controllers"></a>Familiarize-se com seus controladores de movimento

Se o seu headset tiver um rádio interno, os controladores que acompanham o headset serão emparelhados com ele na fábrica. Quando você liga pela primeira vez seus novos controladores e headsets, eles já estarão emparelhados.

Se você tiver um headset sem um rádio interno, precisará configurar seus controladores de movimento emparelhando-os para o seu PC (a maioria dos fones de ouvido fabricados depois de 2018 tem rádio interno).

Se você estiver planejando apenas usar um gamepad ou teclado e mouse do Xbox, não será necessário emparelhar seus controladores.  Se você já planeja usar controladores, provavelmente deve emparelhar.

**Observação**: os controladores de movimento do Windows Mixed Reality requerem o Bluetooth 4,0. Se seu computador não tiver um Bluetooth interno, você precisará conectar um adaptador USB Bluetooth que dá suporte a Bluetooth 4,0 para habilitar seus controladores de movimento. Se você estiver usando o rádio interno em seu headset, não precisará de um adaptador Bluetooth.

![Familiarize-se com seus controladores de movimento](images/get_to_know_controllers.png)

Se você precisar emparelhar seus controladores de movimento, leia o artigo [controladores no Windows Mixed Reality](controllers-in-wmr.md) .

## <a name="set-up-your-room-boundary"></a>Configurar o limite de sala

Escolha uma escala de sala ou experiência de escala de escrivaninha:

**Opção 1: me configurar para todas as experiências (também conhecida como escala de espaço)** permitirá que você percorra a sala e seja a experiência de realidade misturada mais imersiva. É recomendável que você apague pelo menos 5 pés x 7 pés (1,5 metros x 2 metros) de espaço para realidade misturada.

**Opção 2: me configurar para a experiência encaixada e em pé (também conhecida como escala de escrivaninha)** funcionará em sua mesa. É uma boa opção se você não tiver muito espaço em seu espaço. Isso também significa que você usará o headset sem um limite. Você precisará permanecer em um só lugar, pois não terá nenhum limite para ajudá-lo a evitar obstáculos físicos. Além disso, alguns aplicativos e jogos podem ser projetados para serem usados com um limite, portanto, eles podem não funcionar conforme o esperado.

![Escolher uma instalação](images/1050px-chooseasetup.png)

### <a name="if-you-choose-set-me-up-for-all-experiences"></a>Se você escolher "configurar para todas as experiências"

Em breve, sua sala se tornará um mundo virtual em que você pode percorrer e interagir! Inscreva-se e libere espaço em seu espaço para executar realidade misturada (por exemplo, desmarcar algum espaço físico e mover sua cadeira para o lado da sala). É recomendável que você apague pelo menos 5 pés x 7 pés (1,5 metros x 2 metros) de espaço para realidade misturada.

![Verifique se seu espaço está claro](images/1050px-createaboundary.png)

Verifique se seu espaço está claro.

![Centralize seu headset](images/1050px-createaboundary-2.png)

Centralize seu headset.

![Rastrear seu limite](images/1050px-createaboundary-3.png)

Rastreie seu limite.

![Mantenha-se apontado para o PC](images/1050px-createaboundary-4.png)

Mantenha seu headset apontado para o seu PC.

![Aqui está seu limite](images/1050px-createaboundary-5.png)

Aqui está seu limite.

### <a name="if-you-choose-set-me-up-for-seated-and-standing"></a>Se você escolher "Set me up for encaixada e em pé"

Não há etapas adicionais necessárias se você escolher essa opção.

## <a name="what-is-the-maximum-size-of-the-boundary"></a>Qual é o tamanho máximo do limite?

O tamanho de limite máximo com suporte no momento na realidade mista do Windows é 18x18ft (5.7 x 5.7 m) ou 13ft (4m) RADIUS do centro.  O tamanho do limite é dependente do ponto de ancoragem e da distância do ponto de ancoragem que você pode mover antes de arriscar a estabilidade do limite.  A realidade mista do Windows foi criada em uma abstração de estágio na plataforma, o estágio sendo o espaço que você movimenta e esse estágio depende de uma única âncora (que quase todos os aplicativos também pressupõem – é assim que Naopak e Oculus funcionam também, pois têm apenas um único sistema de coordenadas).  O motivo pelo qual isso é importante é que, com o acompanhamento interno, à medida que você se afasta de um ponto de ancoragem, o controle do headset é confiável para manter o limite estável.  Onde o limite destina-se a evitar obstáculos físicos, ele se torna cada vez mais um problema do centro que você vai.  Dois fatores entraram na decisão sobre o tamanho máximo do limite; a distância máxima na qual o Windows Mixed Reality headsets pode fornecer a melhor experiência de dimensionamento de sala com um limite e o comprimento do cabo do headset, que para a maioria dos headsets de realidade misturada do Windows é 10ft (3M). 

## <a name="set-up-speech"></a>Configurar a fala

Você pode habilitar os comandos da Cortana dentro de realidade misturada. Isso permite que você use comandos de fala dentro de realidade misturada para teleport, abra aplicativos e faça outras coisas. Você aprenderá mais sobre isso no capítulo [Aprenda a realidade misturada](learn-mixed-reality.md) .

![A realidade misturada é melhor com a fala](images/1050px-betterwithspeech.png)

## <a name="set-up-your-audio-headset"></a>Configurar o headset de áudio

A menos que você tenha comprado um Odyssey HMD da Samsung (que tenha integrado fones de ouvido e uma matriz dupla de microfone integrada), será necessário obter um headset de áudio (que tem microfone e fones de ouvido) e conectá-lo à tomada de áudio de 3,5 mm do headset. A tomada de áudio de 3,5 mm para o headset irá, dependendo do modelo do headset, estar localizada na parte inferior do visor do headset ou no final de um cabo de áudio curto saindo do visor do headset.

## <a name="adjusting-your-headsets-display-settings"></a>Ajustando as configurações de exibição do headset

A realidade mista do Windows escolhe automaticamente as configurações de exibição que equilibram a qualidade e o desempenho, com base na configuração de hardware do seu PC. Para ajustar essas configurações, vá para **configurações > realidade misturada > tela de headset**.

### <a name="visuals"></a>Visuais

Essa configuração controla a qualidade visual da sua página inicial de realidade misturada. O padrão é "Automatic".

### <a name="resolution"></a>Resolução

A resolução nativa do headset é mostrada aqui.

Se você conectar um headset com monitores de resolução mais alta (por exemplo, headsets com 4320x2160 exibe) ao seu PC, você verá uma configuração para ajustar a resolução de exibição de realidade misturada.

* Essa configuração fornece a opção para que a pilha de composição da realidade mista do Windows seja processada nativamente (por exemplo, em 4320x2160) ou para que a pilha de composição seja renderizada em uma resolução mais baixa e upscale (por exemplo, render em 2880x1440 e upscale para 4320x2160.
* A configuração padrão é renderizar nativamente (por exemplo, a opção **4320 x 2160 (melhor qualidade** ) para fornecer a melhor qualidade visual possível do headset.
* Se o seu PC não atender aos requisitos mínimos de hardware de gráficos para o headset com exibições de resolução mais alta e/ou se você estiver vendo problemas de desempenho de gráficos, poderá tentar usar a opção de up- **dimensionamento automático (melhor desempenho)** .

Essa configuração está disponível no Windows 10, versão 1903 ou mais recente.

### <a name="calibration"></a>Calibragem

Essa configuração é para ajustar a calibragem de IPD para headsets com suporte a IPD de software.

### <a name="experience-options"></a>Opções de experiência

Essa configuração avançada substitui a experiência de taxa de atualização de exibição do headset padrão.

* **Automático (padrão)**: selecione automaticamente a experiência 60 ou 90Hz com base na configuração de hardware do seu PC.
* **60 Hz**
* **90Hz**

>[!Note]
>A configuração de taxa de atualização automática para HP reverb G2 é 90Hz

Certos recursos do Windows Mixed Reality, incluindo a visualização do portal de realidade misturada e uma exibição de fone de ouvido maior FOV, estão disponíveis apenas com a experiência do 90Hz.

### <a name="input-switching"></a>Alternância de entrada

Essa configuração controla o comportamento da realidade mista do Windows em resposta ao sensor de presença do headset:

* **Alternar automaticamente usando o sensor de presença de headset** (padrão): o Windows direcionará automaticamente a entrada (teclado, mouse...) para a realidade mista do Windows sempre que você estiver gastando o headset. Você pode substituir isso a qualquer momento com Win + Y.
* **Alternar manualmente usando a tecla de logotipo do Windows + Y**: o Windows não usará o sensor de presença do headset para detectar quando você estiver utilizando o headset. Você precisará usar o Win + Y para mudar sua entrada entre a área de trabalho do seu PC e a realidade mista do Windows.

Essa configuração está disponível no Windows 10, versão 1903 ou mais recente.

## <a name="installing-microsoft-edge"></a>Instalando o Microsoft Edge 

Para usar o novo Microsoft Edge baseado em Chromium no Windows Mixed Reality Home, atualize para o Windows 10 versão 1903 ou posterior para obter suporte nativo de aplicativos Win32 (como o novo Microsoft Edge) no Windows Mixed Reality Home. Verifique Windows Update ou [Instale manualmente a versão mais recente do Windows 10](https://www.microsoft.com/software-download/windows10).

>[!IMPORTANT]
>O novo Microsoft Edge é iniciado com suporte para WebXR, o novo padrão para a criação de experiências de imersão da Web para headsets de VR. Você não poderá mais reproduzir experiências de WebVR no Microsoft Edge se instalar o novo Microsoft Edge.

### <a name="issues-with-the-new-microsoft-edge-in-windows-mixed-reality"></a>Problemas com o novo Microsoft Edge no Windows Mixed Reality

**Problemas conhecidos resolvidos pela atualização cumulativa 2020-01 para o Windows 10 versão 1903 (ou posterior)**

- Iniciar qualquer aplicativo Win32, incluindo o novo Microsoft Edge, faz com que a tela do headset congele brevemente.
- O bloco Microsoft Edge desaparece do menu Iniciar do Windows Mixed Reality (você pode encontrá-lo na pasta "aplicativos clássicos").
- As janelas do Microsoft Edge anterior ainda são colocadas em todo o início da realidade misturada, mas não podem ser usadas. A tentativa de ativar essas janelas inicia a borda dentro do aplicativo da área de trabalho.
- A seleção de um hiperlink na página inicial da realidade misturada inicia um navegador da Web na área de trabalho em vez da casa mistura de realidade.
- O aplicativo de demonstração do WebVR está presente na casa da realidade misturada, apesar de WebVR não ter mais suporte.
- Aprimoramentos gerais na inicialização e visuais do teclado.

**Problemas conhecidos adicionais**

- Os sites abertos no Windows Mixed Realm serão perdidos quando o portal da realidade misturada for fechado, embora as janelas do Microsoft Edge permaneçam onde foram colocadas na casa misturada da realidade.
- O áudio do Microsoft Edge Windows não está espacial.
- Corrigido na extensão do visualizador 360 versão 2.3.8: abrir um vídeo 360 do YouTube no Windows Mixed Reality pode resultar na distorção do vídeo no headset. Reiniciar a borda deve atualizar invisivelmente a extensão do visualizador 360 para resolver esse problema. Você pode confirmar qual versão da extensão você tem digitando `edge://system/` na barra de endereços e selecionando o botão "expandir" ao lado de "extensões".
- Durante as sessões de realidade mista do Windows, os monitores virtuais serão exibidos como monitores físicos genéricos em **configurações > sistema > exibição**.

## <a name="launching-mixed-reality-after-the-first-time"></a>Iniciando realidade misturada após a primeira vez

Entrar na realidade misturada uma segunda vez é tão fácil quanto colocar o fone de ouvido novamente enquanto estiver conectado ao seu PC. Você também pode iniciar o aplicativo do portal da realidade misturada manualmente abrindo-o no menu iniciar. A entrada e o áudio serão roteados automaticamente para o headset quando você o colocar, ou você poderá dispará-lo manualmente pressionando o **Windows + Y** no teclado.

## <a name="see-also"></a>Confira também

* [Pergunte à comunidade](https://answers.microsoft.com)
* [Entre em contato conosco para obter suporte](https://support.microsoft.com/contactus/)
* [Como solucionar problemas de instalação](installation_errors.md)
* [Solução de problemas de instalação](set-up-questions.md)
* [Aprender Realidade Misturada](learn-mixed-reality.md)
* [Como funcionam os controladores de movimento](controllers-in-wmr.md)
* [Como funciona o acompanhamento interno](tracking-system.md)
