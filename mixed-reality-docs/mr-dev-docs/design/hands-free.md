---
title: Mãos livres
description: Saiba mais sobre as dificuldades que os usuários podem enfrentar com uma interface de mãos e controladores e sobre várias alternativas de mãos livres.
author: hferrone
ms.author: v-hferrone
ms.date: 04/20/2019
ms.topic: article
keywords: Realidade Misturada, mãos livres, olhar, direcionamento de olhar, interação, design, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Toolkit realidade misturada, entrada de voz, usabilidade
ms.openlocfilehash: 725d8886d21b42ee4643680c0dc91c1d29c25f8409b0ed0828256564dde7545c
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115213530"
---
# <a name="hands-free"></a>Mãos livres

## <a name="scenarios"></a>Cenários

Conforme descrito na visão geral do modelo de [interação,](interaction-fundamentals.md)depois de identificar seus usuários e suas metas, pergunte a si mesmo quais desafios ambientais ou de situação eles podem enfrentar enquanto trabalham para realizar suas tarefas. Por exemplo, muitos usuários precisam usar as mãos para atingir suas metas do mundo real e terão dificuldade para interagir com uma interface baseada em mãos e controladores.

Alguns cenários específicos incluem: 
* Ser guiado para realizar uma tarefa enquanto o usuário está com as mãos ocupadas
* Consulta de materiais enquanto as mãos do usuário estão ocupadas
* Descanso das mãos em caso de fadiga
* Uso de luvas que não podem ser rastreadas
* Usuário carregando algo com as mãos
* Desariedade social ao usar gestos de mão grande
* Espaços apertados

## <a name="hands-free-modalities"></a>Modais de mãos livres

### <a name="voice-input"></a>[Entrada de voz](voice-input.md)

Usar sua voz para controlar e controlar uma interface oferece uma maneira conveniente de operar de mãos livres e usar atalhos para ignorar várias etapas, se você quiser. Com a entrada de voz, o usuário pode ler o nome de qualquer botão em voz alta para ativá-lo _("vê-lo,_ diga-o") e conversar com um agente digital que possa realizar tarefas para você.

### <a name="gaze-and-dwell"></a>[Focar e esperar](gaze-and-dwell.md)

Em algumas situações de mãos livres, usar sua voz não é ideal nem mesmo possível. Ambientes de fábrica altos, privacidade ou normas sociais podem ser restrições. O modelo de olhar + esperar permite que o usuário navegue por um aplicativo sem nenhuma entrada extra além do olhar ou do olhar da cabeça: o usuário simplesmente fica olhando (com a cabeça ou os olhos) no destino e permanece lá por um momento para ativá-lo. Para saber mais sobre as considerações de design individuais para o olhar + manter a [cabeça,](gaze-and-dwell-head.md)confira o olhar com o olhar [+](gaze-and-dwell-eyes.md) a cabeça e o olhar com a cabeça + a cabeça .

## <a name="transitioning-in-and-out-of-hands-free"></a>Fazer a transição para dentro e para fora de mãos livres

Para esses cenários, liberar as mãos da interação com hologramas para comando e navegação pode variar de ser um requisito absoluto até a operação do aplicativo, de ponta a ponta, até uma conveniência adicionada de que o usuário pode fazer a transição para dentro e para fora a qualquer momento. 

Se o aplicativo exigir que ele sempre seja usado de mãos livres, seja usando o recurso, comandos de voz personalizados ou o comando de voz única, "select", certifique-se de fazer as acomodações apropriadas em sua interface do usuário. 

Se o usuário de destino precisar mudar de mãos para mãos livres a seu critério, é importante levar em conta os princípios a seguir.

### <a name="assume-the-user-is-already-in-the-mode-that-they-want-to-switch-to"></a>Suponha que o usuário já está no modo para o que deseja alternar
Por exemplo, se o usuário estiver no chão de fábrica, assistindo a uma referência de vídeo em seu HoloLens e decidir pegar uma chave inglesa para começar a trabalhar, provavelmente ela começaria a trabalhar de mãos livres sem precisar colocar a chave inglesa para pressionar um botão. Ela pode invocar uma sessão de voz com um comando de voz, ficar em uma interface do usuário já visível para começar a vida ou dizer a palavra "selecionar".

O usuário pode: 
* Alternar para mãos livres enquanto estiver com as mãos livres
* Alternar para as mãos com as mãos
* Alternar para o controlador usando um controlador 

### <a name="create-redundant-ways-to-switch-modes"></a>Criar maneiras redundantes de alternar modos

Embora o primeiro princípio seja sobre acesso, o segundo é sobre disponibilidade. Não deve haver apenas uma única maneira de fazer a transição para dentro e para fora de um modo. 

Alguns exemplos seriam: 
* Um botão para iniciar interações de voz
* Um comando de voz para fazer a transição, usando o olhar com a cabeça e a união

### <a name="add-a-dash-of-drama"></a>Adicionar um traço de filme

Uma opção de modo é uma grande coisa. É importante que, quando essas transições ocorrem, elas sejam explícitas, até mesmo uma mudança drástica, para permitir que o usuário saiba o que aconteceu. 

## <a name="usability-checklist"></a>Lista de verificação de usabilidade

**O usuário pode fazer tudo e qualquer coisa de ponta a ponta, de ponta a ponta?**
* Cada interação deve ser acessível de mãos livres
* Verifique se há uma substituição para todos os gestos personalizados, como re tamanho, colocação, deslizar o dedo, toques e assim por diante.
* Verifique se o usuário tem controle confiável da presença, do posicionamento e do detalhes da interface do usuário sempre
    * Como sair da interface do usuário
    * Endereçamento da interface do usuário que está fora do campo de exibição (FOV)
    * Quanto vejo, onde, quando

**A mecânica da interação está sendo ensinada e reforçada com as acessível corretas?**

O usuário entende ...
* ... Em qual modo eles estão?
* ... O que eles podem fazer nesse modo?
* ... Qual é o estado atual?
* ... Como eles podem fazer a transição?
    
**A interface do usuário é otimizada para mãos livres?**   

* Exemplo: as acessível de tempo de vida não são criadas para padrões 2D típicos
* Exemplo: o direcionamento de voz é melhor com realçamento de objeto
* Exemplo: as interações de voz são melhores com legendas que precisam ser ativas

## <a name="see-also"></a>Confira também

* [Acompanhamento ocular no HoloLens 2](eye-tracking.md)
* [Focar e confirmar](gaze-and-commit.md)
* [Focar e esperar](gaze-and-dwell.md)
* [Mãos – Manipulação direta](direct-manipulation.md)
* [Mãos – Gestos](gaze-and-commit.md#composite-gestures)
* [Mãos – Apontar e confirmar](point-and-commit.md)
* [Interações instinctuais](interaction-fundamentals.md)
* [Entrada de voz](voice-input.md)
