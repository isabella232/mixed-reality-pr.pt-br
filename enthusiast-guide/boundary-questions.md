---
title: Perguntas frequentes sobre limite
description: Solução de problemas avançada do Windows Mixed realm para perguntas sobre limites que vão além da nossa documentação de suporte de consumidor padrão.
author: hferrone
ms.author: v-hferrone
ms.date: 09/15/2020
ms.topic: article
keywords: Realidade mista do Windows, realidade misturada, realidade virtual, VR, Sr, solução de problemas, erros, ajuda, suporte, limite
appliesto:
- Windows 10
ms.openlocfilehash: 8dba6ebb5f74b229cea4ea2d5e1ac0a5e70a3f57
ms.sourcegitcommit: 1b90f27af091dffd4fba63d69a89873aa0f75079
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97725277"
---
# <a name="boundary-faqs"></a>Perguntas frequentes sobre limite

## <a name="whats-a-boundary-and-why-should-i-create-one"></a>O que é um limite e por que devo criar um?

Um limite define a área que você pode percorrer enquanto estiver aproveitando o headset da realidade mista do Windows. É importante criar um limite para ajudá-lo a evitar os obstáculos que você não pode ver enquanto estiver em headset. O limite é semelhante a um esboço branco dentro da realidade misturada e aparece quando você chega perto dele. Quando você vê isso, reduza os movimentos e evite cruzar o limite ou estendê-los para além dele.

A área dentro do limite deve ser livre de mobília, acessórios de luz de baixa interrupções, ventiladores de teto e assim por diante, para que você não se aprofunde nem percorrendo nada. [Saiba mais sobre integridade e segurança no Windows Mixed Reality](wmr-health-safety-comfort.md).

## <a name="how-do-i-create-a-boundary"></a>Como fazer criar um limite?

Quando você configura o headset pela primeira vez, o aplicativo de instalação (portal de realidade mista) o guiará pelas etapas para criar um limite. Mas você pode criar um a qualquer momento:

1. Selecione **iniciar > portal de realidade misturada** na sua área de trabalho.
2. Abra o "menu".
3. Selecione "configurar limite de sala" para criar um novo limite.

Se outra pessoa usar o headset, verifique se ele entendeu o limite e como usá-lo. Se você mover o headset para um novo local, precisará configurar um novo limite para o espaço.

## <a name="i-get-an-error-message-when-i-try-to-create-a-boundary"></a>Recebo uma mensagem de erro quando tento criar um limite

* Não fique muito perto de uma parede ou de outra obstrução ao criar um limite.
* Certifique-se de manter o headset na altura de estou e rosto o computador enquanto rastreia o limite.
* Verifique se o sensor não está bloqueado e se há luz suficiente.
* O espaço que você está rastreando deve ser maior que 3 metros quadrados.
* O espaço não deve ser muito grande ou muito complicado. Fique em uma forma geométrica simples com torceções e ativações.
* Não entre em seu próprio caminho enquanto estiver rastreando.
* Se você ficar preso em um canto, comece novamente.

## <a name="the-system-cannot-find-the-boundary-and-im-being-presented-with-setup-ui"></a>O sistema não consegue encontrar o limite e estou sendo apresentado à interface do usuário da instalação

Isso significa que o sistema de controle não conseguiu reconhecer seu ambiente. Se você estiver em um novo ambiente, deverá configurar o [limite](set-up-windows-mixed-reality.md#set-up-your-room-boundary).
Se você já usou o dispositivo neste ambiente e configurou um limite:

* Verifique se a sala tem luz suficiente.
* Verifique se você gastou o dispositivo e procurou a sala. O dispositivo deve observar seu ambiente para saber onde ele está. Ele não encontrará seus limites se estiver sentado em uma mesa.
* Desconecte o dispositivo, feche a realidade mista do Windows e conecte-o novamente.
* Se algo no ambiente tiver sido alterado, o dispositivo poderá não reconhecê-lo mais. Configure um novo limite.

Se essas etapas não resolverem o problema, exclua os dados do ambiente e configure o limite novamente.

## <a name="the-system-is-presenting-me-with-ui-that-asks-me-to-choose-setup-for-all-experiences-or-seatedstanding-and-i-see-my-bounds"></a>O sistema está apresentando a interface do usuário que me pede para escolher a configuração de todas as experiências ou colocadas em posição/pé, e eu vejo meus limites

O dispositivo está demorando muito para localizar os limites. Você pode ignorar essa mensagem escolhendo a opção para usar um limite e você será levado para sua página inicial do Windows Mixed Realm com seus limites presentes.

## <a name="i-often-see-a-message-saying-ive-lost-my-bounds"></a>Eu sempre vejo uma mensagem dizendo "Eu perdi meus limites"

O sistema de controle está tendo um controle de tempo rígido e identificando seu ambiente. Nesse estado, o dispositivo não pode mais exibir seus limites. O headset muda para 3DOF para evitar que você se aprofunde nas coisas do mundo real até localizar seus limites novamente. Tente as seguintes etapas para corrigir o problema:

1. Certifique-se de que a sala tenha luz suficiente.
2. Execute a instalação novamente se você redecorau ou remodelou a sala recentemente.
3. Desconecte o dispositivo, feche a realidade mista do Windows e conecte-o novamente.
4. Limpe os dados do ambiente e configure o dispositivo novamente.
5. Se a mensagem persistir, contate o atendimento ao cliente.

## <a name="a-message-says-my-boundary-cant-be-found-what-should-i-do"></a>Uma mensagem diz que o meu limite não foi encontrado. O que devo fazer?

A realidade mista do Windows pode ter problemas para identificar o limite existente. Você pode criar um novo limite ou pode usar seu dispositivo no modo "encaixado e posicionado".

## <a name="a-message-says-lost-tracking-or-we-dont-have-a-boundary-for-this-space"></a>Uma mensagem diz "controle perdido" ou "não temos um limite para este espaço"

Crie um novo limite:

1. Selecione **iniciar > portal de realidade misturada**.
2. Abra o "menu".
3. Selecione "configurar limite de sala".

## <a name="the-boundary-is-always-visible-how-can-i-make-it-go-away"></a>O limite é sempre visível. Como posso fazê-lo desaparecer?

O limite aparece quando você está perto dele. Se o seu limite incluir seções com uma forma estreita ou irregular, você poderá acabar ficando perto dela. O limite pode parecer com mais frequência do que o desejado. Tente criar o limite novamente usando uma forma maior e mais regular para corrigir o problema:

1. Selecione **iniciar > portal de realidade misturada**.
2. Abra o "menu".
3. Selecione "configurar limite de sala".

## <a name="can-i-turn-off-the-boundary-temporarily"></a>Posso desativar o limite temporariamente?

* Selecione **iniciar > portal de realidade misturada**.
* Abra o "menu".
* Ativar "limite" para "desativado". Lembre-se de permanecer em um único lugar enquanto o limite está desativado.

## <a name="how-do-i-choose-between-seated-and-standing-and-all-experiences"></a>Como fazer escolher entre "sentado e em pé" e "todas as experiências"?

Se você escolher "colocado e posicionado" durante a configuração do headset ou posterior, você usará o headset sem um limite. Você precisará manter-se em um ponto ao usar o headset para evitar obstáculos físicos e ultrapassar os riscos. Você pode sentar ou se repousar, mas não pode se movimentar. Tenha em mente que obstáculos podem ser uma sobrecarga e em seu lugar.

Alguns aplicativos podem ser projetados para funcionar com um limite. Eles podem não funcionar ou fornecer a mesma experiência se você usá-los sem um limite.

Se você escolher "todas as experiências", configurará um limite e poderá usar aplicativos e experiências que funcionam com e sem um limite.

## <a name="see-also"></a>Consulte também

* [Pergunte à comunidade](https://answers.microsoft.com)
* [Entre em contato conosco para obter suporte](https://support.microsoft.com/contactus/)