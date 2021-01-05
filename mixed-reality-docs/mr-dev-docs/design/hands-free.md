---
title: Mãos livres
description: Saiba mais sobre as dificuldades que os usuários podem enfrentar com uma interface de mãos e controladores e sobre várias alternativas sem intervenção.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade misturada, mãos gratuitas, olhar, direcionamento de olhar, interação, design, headset de realidade misturada, headset de realidade mista do Windows, headset de realidade virtual, HoloLens, MRTK, kit de ferramentas de realidade misturada, entrada de voz, usabilidade
ms.openlocfilehash: 2864e58fdd8a29ae8f981b42f50735eb13a50869
ms.sourcegitcommit: d340303cda71c31e6c3320231473d623c0930d33
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/01/2021
ms.locfileid: "97847681"
---
# <a name="hands-free"></a>Mãos livres

## <a name="scenarios"></a>Cenários

Conforme descrito na [visão geral do modelo de interação](interaction-fundamentals.md), depois de identificar os usuários e suas metas, pergunte-se quais desafios ambientais ou de situação eles podem enfrentar enquanto trabalham para realizar suas tarefas. Por exemplo, muitos usuários precisam usar suas mãos para realizar suas metas reais e terão dificuldade para interagir com uma interface baseada em controladores e de mão.

Alguns cenários específicos incluem: 
* Ser guiado para realizar uma tarefa enquanto o usuário está com as mãos ocupadas
* Consulta de materiais enquanto as mãos do usuário estão ocupadas
* Descanso das mãos em caso de fadiga
* Uso de luvas que não podem ser rastreadas
* Usuário carregando algo com as mãos
* Inconveniente social ao usar gestos de grande mão
* Espaços apertados

## <a name="hands-free-modalities"></a>Modalidades sem intervenção

### <a name="voice-input"></a>[Entrada de voz](voice-input.md)

Usar sua voz para comando e controlar uma interface oferece uma maneira conveniente de operar sem intervenção e usar atalhos para ignorar várias etapas, se desejar. Com a entrada de voz, o usuário pode ler o nome de qualquer botão para ativá-lo _("vê-lo, dizer")_ e conversar com um agente digital que pode realizar tarefas para você.

### <a name="gaze-and-dwell"></a>[Focar e esperar](gaze-and-dwell.md)

Em algumas situações práticas, usar sua voz não é ideal ou até mesmo possível. Ambientes de fábrica altos, privacidade ou normas sociais podem ser restrições. O modelo olhar + de duração permite que o usuário navegue por um aplicativo sem nenhuma entrada extra além do seu olho ou olhar de cabeça: o usuário simplesmente mantém nuvens (com seus cabeças ou olhos) no destino e permanece lá por um momento para ativá-lo. Para saber mais sobre as considerações de design individuais para olhar + acessation, confira os [olhos-olhar +](gaze-and-dwell-eyes.md) acessation e [Head-olhar +](gaze-and-dwell-head.md)acessation.

## <a name="transitioning-in-and-out-of-hands-free"></a>Transição para dentro e para fora de mãos gratuitas

Para esses cenários, liberar suas mãos de interagir com hologramas para comando e navegação pode variar de ser um requisito absoluto para operar o aplicativo, de ponta a ponta, a uma conveniência adicional de que o usuário pode fazer a transição para dentro e para fora a qualquer momento. 

Se o aplicativo exigir que ele sempre seja usado sem intervenções, seja usando a pesquisa, comandos de voz personalizados ou o comando de voz simples, "Select", certifique-se de fazer as acomodações apropriadas em sua interface do usuário. 

Se o seu usuário de destino precisar mudar de mãos para as mãos gratuitas a seu critério, é importante levar em conta os princípios a seguir.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Suponha que o usuário já esteja no modo que deseja alternar para
Por exemplo, se o usuário estiver no chão de fábrica, observando uma referência de vídeo em seu HoloLens e decidir pegar uma chave inglesa para começar a trabalhar, ela provavelmente começaria a trabalhar em mãos sem precisar colocar a chave de fenda para pressionar um botão. Ela pode invocar uma sessão de voz com um comando de voz, a pesquisa em uma interface do usuário já visível para iniciar a pesquisa ou dizer a palavra "Select".

O usuário pode: 
* Mude para o hands sem intervenção
* Mude para as mãos com suas mãos
* Alternar para o controlador usando um controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Criar maneiras redundantes de alternar entre modos

Embora o primeiro princípio seja sobre o acesso, o segundo é sobre a disponibilidade. Não deve haver apenas uma única maneira de fazer a transição para dentro e para fora de um modo. 

Alguns exemplos seriam: 
* Um botão para iniciar as interações de voz
* Um comando de voz para o qual fazer a transição, usando Head-olhar e a pesquisa

### <a name="add-a-dash-of-drama"></a>Adicionar um traço de baixo-claro

Uma opção de modo é um grande problema. É importante que, quando essas transições acontecem, eles sejam um interruptor explícito, até mesmo um drástico, para permitir que o usuário saiba o que aconteceu. 

## <a name="usability-checklist"></a>Lista de verificação de usabilidade

**O usuário pode fazer tudo e tudo sem intervenção, de ponta a ponta?**
* Todos os interagir devem estar acessíveis sem intervenções
* Certifique-se de que há uma substituição para todos os gestos personalizados, como redimensionamento, posicionamento, toque, toques e assim por diante.
* Certifique-se de que o usuário tenha o controle confiante de presença, posicionamento e verbosidade da interface de usuário sempre
    * Obtendo a interface do usuário fora do caminho
    * Endereçando a interface do usuário que está fora do campo de visão (FOV)
    * Quanto vejo, onde, quando

**A mecânica da interação está sendo ensinada e reforçada com a capacidades correta?**

O usuário entende...
* ... Em que modo eles estão?
* ... O que eles podem fazer neste modo?
* ... O que é o estado atual?
* ... Como eles podem fazer a transição?
    
**A interface do usuário é otimizada para mãos gratuitas?**   

* Exemplo: a capacidades de pesquisa não é interna a padrões 2D típicos
* Exemplo: o direcionamento de voz é melhor com o realce de objeto
* Exemplo: as interações de voz são melhores com legendas que precisam ser ativadas

## <a name="see-also"></a>Consulte também

* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
