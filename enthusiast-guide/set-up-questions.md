---
title: Perguntas frequentes sobre instalação
description: Solução de problemas avançada do Windows Mixed Reality para questões de configuração que vão além da nossa documentação de suporte de consumidor padrão.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, MR, solução de problemas, erros, ajuda, suporte, instalação, Windows Mixed Reality Home, portal do Windows Mixed Reality
appliesto:
- Windows 10
ms.openlocfilehash: 2e079cae16a20a4e0a2e6c967ecedef1950ded57
ms.sourcegitcommit: 09599b4034be825e4536eeb9566968afd021d5f3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2020
ms.locfileid: "91675518"
---
# <a name="setup-faqs"></a>Perguntas frequentes sobre instalação 

## <a name="the-mixed-reality-portal-doesnt-open-when-i-plug-in-my-headset"></a>O portal de realidade misturada não abre quando eu conecto meu headset.

O portal de realidade misturada, o aplicativo que o conduz pela instalação do Windows Mixed Reality, foi projetado para ser aberto automaticamente quando você conectar um headset compatível. Se ele não abrir, vá para iniciar e digite "portal da realidade mista" na caixa de pesquisa para abrir o aplicativo. Se você não encontrar o portal de realidade misturada, isso pode significar que você precisa [atualizar para a versão mais recente do Windows](https://support.microsoft.com/en-us/help/12373/windows-update-faq).

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Como fazer escolher entre "sentado e em pé" e "todas as experiências"?

Se você escolher "colocado e posicionado", durante a configuração do headset ou posterior, você usará o headset sem um limite. Você pode sentar ou se repousar, mas, caso contrário, precisará permanecer em um lugar, pois você não terá nenhum limite para ajudá-lo a evitar obstáculos físicos. Alguns aplicativos podem ser projetados para funcionar com um limite, portanto, talvez você não possa usá-los ou talvez não tenha a mesma experiência se usá-los sem limites. Consulte ["o que é um limite e por que devo criar um?"](boundary-questions.md#whats-a-boundary-and-why-should-i-create-one).

Se você escolher "todas as experiências", configurará um limite e poderá usar aplicativos e experiências que funcionam com um limite, bem como aqueles que não exigem um. 

## <a name="learn-mixed-reality-didnt-run-on-first-launch-and-i-went-right-to-windows-mixed-reality-home"></a>Aprender a realidade misturada não foi executada na primeira inicialização, e eu fui direto para a página inicial do Windows Mixed Reality.

Você pode executar novamente a experiência de aprendizado seguindo as [etapas de nova execução](learn-mixed-reality.md#how-do-i-re-run-the-learning-experience). 

## <a name="my-controllers-arent-showing-in-my-windows-mixed-reality-home"></a>Meus controladores não estão sendo exibidos na minha página inicial do Windows Mixed Reality.

Verifique se os controladores têm baterias completas e se estão emparelhados corretamente usando o Bluetooth. Tente ligar os controladores e desligar usando o botão Windows. Se você ainda não consegue ver seus controladores, tente desemparelhar e reparar cada controlador novamente: 
* Se o headset tiver um rádio interno, use o aplicativo complementar que veio com o headset para desemparelhar e, em seguida, emparelhe os controladores novamente (o portal de realidade misturada pode ajudá-lo a encontrar o aplicativo complementar correto). 
* Se os controladores estiverem emparelhados com o PC, vá para **dispositivos > configurações de > Bluetooth** para desemparelhar e emparelhar os controladores novamente. 

## <a name="the-floor-of-my-windows-mixed-reality-home-doesnt-appear-to-be-at-the-correct-height"></a>O andar da minha página inicial do Windows Mixed Reality não parece estar na altura correta.

Selecione **iniciar > ajuste de piso** , que será iniciado quando você colocar o aplicativo no mundo, para fazer alterações ao usar o headset. Neste aplicativo, você será direcionado para usar o Touch Pad (controlador de movimento) ou o gamepad (painel de direção) para ajustar a altura do piso. Quando o piso estiver correto, use o botão Windows para retornar à sua página inicial.

## <a name="i-cant-show-a-preview-of-what-im-seeing-in-my-headset-on-my-desktop"></a>Não consigo mostrar uma visualização do que estou vendo em meu Headset na área de trabalho.

O portal de realidade mista do Windows tem um botão de **execução** na parte inferior da tela que permite visualizar o que você está vendo em seu headset na tela da área de trabalho. Por motivos de desempenho, esse recurso só está disponível em PCs em execução no Windows Mixed Reality ultra (90Hz).

## <a name="i-got-a-something-went-wrong-error-message-or-im-having-problems-in-the-mixed-reality-portal"></a>Recebi uma mensagem de erro "algo deu errado" ou estou tendo problemas no portal de realidade misturada
Para obter mais informações sobre um código de erro específico, veja [aqui](error-codes.md). Você também pode tentar:

Reinicie a realidade mista do Windows:
1. Desconecte ambos os cabos de headset do seu PC.
2. Reinicie o computador.
3. Reconecte seu headset.

Verifique se seu PC reconhece o headset:
1. Selecione Iniciar.
2. Digite "Device Manager" na caixa de pesquisa e selecione-o na lista. 
3. Expanda "dispositivos de realidade misturada" e veja se o headset está listado. 

Se não estiver listado:
1. Conecte o headset em portas diferentes no computador, se disponível.
2. Verifique as atualizações de software mais recentes do Windows Update.
3. Desinstalar e reinstalar o Windows Mixed Reality:
    1. Desconecte ambos os cabos de headset do seu PC.
    2. Selecione **configurações > realidade misturada > desinstalar** .
    3. Se os controladores de movimento estiverem emparelhados com o seu PC, selecione **configurações > dispositivos > Bluetooth & outros dispositivos** para desemparelhar. Selecione cada controlador e "remover dispositivo". Se os controladores estiverem emparelhados com o headset, você poderá ignorar esta etapa.
    4. Conecte seu headset ao seu PC para reinstalar a realidade mista do Windows.

## <a name="i-cant-direct-input-controllers-gamepad-mousekeyboard-into-windows-mixed-reality"></a>Não consigo direcionar a entrada (controladores, gamepad, mouse/teclado) para a realidade mista do Windows.

Quando você coloca em seu headset, a entrada deve ser automaticamente alternada para sua experiência de realidade misturada por meio do sensor de presença do headset. Uma barra azul deve aparecer na área de trabalho:

![Área de trabalho do Windows com entrada sendo direcionada para headset](images/1050px-windowsy.png)

Se a entrada não for alternada automaticamente, você poderá ter desabilitado a alternância de entrada automática em **configurações > realidade misturada > exibição do headset > troca de entrada** . Você sempre pode digitar a **tecla Windows + Y** no teclado para alternar manualmente a entrada para o headset ou voltar para a área de trabalho.

## <a name="during-mixed-reality-start-up-im-stuck-at-turn-your-head-side-to-side-and-then-at-the-floor"></a>Durante a realidade misturada, estou preso em "Transforme seu lado à frente e, em seguida, no andar".

Esta etapa permite que o headset reconheça seu espaço e restaure qualquer piso e limite virtuais existentes. Quando você coloca em seu headset, esse processo de verificação pode levar até 10 segundos. Após a conclusão, você estará na página inicial do Windows Mixed Reality ou será solicitado a configurar seu limite novamente.

Se o processo de verificação demorar mais de 10 segundos, pode haver um problema com o sensor de proximidade no headset:
1. Verifique se o adesivo foi removido do sensor de proximidade. O sensor de proximidade está localizado dentro do headset, aproximadamente onde o centro de seu nervosismo seria.
2. Verifique se o sensor de proximidade está alternando a entrada para o headset: com o dedo, cubra e descubra o sensor de proximidade algumas vezes para verificar se a entrada está mudando para o headset. Você deve ver a faixa de **tecla do Windows + Y** na parte superior do seu computador. Você pode alternar manualmente a entrada para o headset a qualquer momento digitando a **tecla Windows + Y** no teclado.

## <a name="my-xbox-controller-isnt-working-with-windows-mixed-reality"></a>Meu controlador Xbox não está funcionando com a realidade mista do Windows.

* Verifique se o controlador está ligado, totalmente cobrado e conectado ao PC.
* Substitua as baterias do controlador.
* Se você estiver usando um controlador Bluetooth, vá para **configurações > dispositivos > Bluetooth & outros dispositivos** em seu PC e verifique se ele está emparelhado (ele deve estar listado na página).
