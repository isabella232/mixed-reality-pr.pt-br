---
title: Menu lateral
description: Os menus de mão permitem que os usuários aumentem rapidamente a interface do usuário anexada à mão para funções usadas com frequência.
author: nbarragan23
ms.author: nobarr
ms.date: 08/27/2019
ms.topic: article
keywords: hand, menu, button, quick access, layout, mixed reality headset, windows mixed reality headset, virtual reality headset, HoloLens, MRTK, Mixed Reality Toolkit
ms.openlocfilehash: f007ada2d7a594f141d30a3619d4d80ac74621d8
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600325"
---
# <a name="hand-menu"></a>Menu lateral

![Local do lado do Ulnar](images/UX_Hero_HandMenu.jpg)

O menu de mão é um dos padrões de experiência do usuário mais exclusivos no HoloLens 2. Ele permite que você aumente rapidamente a interface do usuário anexada à mão. Como ele pode ser acessado a qualquer momento e pode ser mostrado e ocultado facilmente, é ótimo para ações rápidas.

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAg]

Você encontrará nossas práticas recomendadas para trabalhar com menus de mão na lista abaixo. Você também pode encontrar uma cena de exemplo que demonstra o menu de mão no [MRTK](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu).

<br>

---

## <a name="best-practices"></a>Práticas recomendadas

**Manter o número de botões pequenos** 

Devido à distância próxima entre um menu bloqueado à mão e os olhos e a tendência de os usuários se concentrarem em uma área visual relativamente pequena a qualquer momento (o cone atenuário da visão é de aproximadamente 10 graus), recomendamos manter o número de botões pequenos. Com base em nossa exploração, uma coluna com três botões funciona bem mantendo todo o conteúdo dentro do FOV (campo de exibição), mesmo quando um usuário move as mãos para o centro do FOV. 

**Usar o menu de mão para ação rápida** 

A acionamento de um arm e a manutenção da posição podem causar facilmente a queda de braço. Use um método bloqueado manualmente para o menu que exige uma interação curta. Se o menu for complexo e exigir tempos de interação estendidos, considere usar world-locked ou body-locked. 

**Botão/Ângulo do painel**

Os menus devem ser posicionados no meio da cabeça e no lado oposto da cabeça: isso permite que uma movimentação natural da mão interaja com o menu com a mão oposta e evita posições de mão inconvenientes ou inconvenientes ao tocar em botões. 

**Considere dar suporte a uma operação de mãos ou mãos livres**

Não suponha que ambas as mãos do usuário estão sempre disponíveis. Considere uma ampla variedade de contextos quando uma ou ambas as mãos não estão disponíveis e certifique-se de que suas contas de design para essas situações. Para dar suporte a um menu com uma mão, você pode tentar fazer a transição do posicionamento do menu de bloqueado manualmente para o world-locked quando a mão se inverter (ficar inocável). Para cenários de mãos livres, considere usar um comando de voz para invocar o menu de mão.

**Evite adicionar botões próximos ao pulso (botão página início do sistema)**

Se os botões do menu de mão são colocados muito próximos ao botão página início, ele pode disparar acidentalmente ao interagir com o menu de mão.

<br>

## <a name="hand-menu-with-large-and-complex-ui-controls"></a>Menu manual com controles de interface do usuário grandes e complexos

<img src="images/HandMenu_SizeExample.png" alt="HoloLens perspective of a menu system that always faces the user" width="940px">
É recomendável limitar o número de botões ou controles de interface do usuário em menus anexados manualmente. Isso porque a interação estendida com um grande número de elementos da interface do usuário pode causar a queda do braço. Se sua experiência exigir um menu grande, forneça uma maneira fácil para o usuário bloquear o menu. Uma técnica que recomendamos é bloquear o mundo e, em seguida, usar o menu quando a mão cair ou se inverter do usuário. Uma segunda técnica é permitir que o usuário pegue diretamente o menu com a outra mão. Quando o usuário libera o menu, o menu deve bloquear o mundo. Dessa forma, um usuário pode interagir com vários elementos da interface do usuário de maneira confortável e confiante durante um longo período de tempo. 

Quando o menu estiver bloqueado pelo mundo, forneça uma maneira de mover o menu e feche o menu quando ele não for mais necessário. Tornar o menu móvel fornecendo alças nos lados ou na parte superior do menu. Adicione um botão Fechar para permitir que o menu seja fechado. Permita que o menu seja reattado à mão quando a mão do usuário estiver de frente para o usuário. Também recomendamos exigir que os usuários se alocarem para evitar ativações falsas (veja abaixo).

**Menu grande que mostra um problema de usabilidade**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AOPx]

**Menu bloqueado pelo mundo no menu suspenso**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AGZi]

**Captura manual & pull para bloquear o menu**

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4AJAf]

## <a name="how-to-prevent-false-activation"></a>Como evitar a ativação falsa

Se você usar apenas a mão como um evento para disparar o menu de mão, ele poderá aparecer acidentalmente quando você não precisar dele (falso positivo), porque as pessoas movem as mãos intencionalmente (para comunicação e manipulação de objetos) e não intencionalmente. Para reduzir as ativações falsas, adicione uma etapa extra além do evento de ativação para invocar o menu da mão (como dedos totalmente abertos ou o usuário olhando intencionalmente à mão).

**Exigir uma mão simples**

Ao exigir uma mão aberta simples, você pode impedir a ativação falsa que pode ocorrer à medida que o usuário manipula objetos ou gestos ao se comunicar em um ambiente. 

**Exigir o olhar**

Ao exigir que o usuário se atenule à mão (com o olhar com o olhar ou o olhar com a cabeça), ele impede as ativações falsas porque o usuário precisa direcionar sua atenção para a mão como uma etapa de ativação secundária (com um limite de distância fixo usado para permitir o conforto do usuário).  

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Asn4]

---

## <a name="hand-menu-placement-best-practices"></a>Práticas recomendadas de posicionamento do menu de mão

Na anatomia humana, o cérebro ulnar é um cérebro que é executado próximo à ulna. A ulna é um longo dedo encontrado no forearm que se alonga do rosto até o menor dedo.

Abaixo estão dois posicionamentos recomendados com base em nossas explorações:

:::row:::
    :::column:::
        ![Localização da mão lateral ulnar dentro da mão](images/UlnarSideHandMenu.gif)<br>
        **A. Ulnar dentro da mão**<br>
        Essa posição é confiável porque as mãos não se sobrepõem umas às outras. Isso é essencial para detecção e acompanhamento precisos da mão.
    :::column-end:::
    :::column:::
        ![Local do lado do Ulnar acima](images/UlnarAboveHandMenu.gif)<br>
        **B. Ulnar acima**<br>
        Esse local é confortável para os usuários porque eles não precisam auximo muito o braço para interagir com o menu de mão. É recomendável colocar os menus **13 cm** acima da mão e alinhar os botões dentro da mão ulnar. [Leia mais sobre o tamanho ideal do botão](interactable-object.md)<br>
        <br>
        Por motivos técnicos, recomendamos esse local com uma implementação necessária: o desenvolvedor precisará congelar o menu quando a mão oposta do usuário ficar próxima de interagir com ele. Isso evitará a tremtividade da sobreposição de mãos e também permitirá um direcionamento mais rápido dos botões.<br>
        <br>
        As câmeras do HoloLens 2 identificam as mãos com precisão quando estão separadas umas das outras. As mãos sobrepostas podem fazer com que os menus de mão se movam para fora do local de âncora.<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="menu-positions-that-arent-recommended"></a>Posições de menu que não são recomendadas

Fizemos uma pesquisa de usuário com diferentes layouts e locais de menus, os seguintes locais de menu **NÃO** são recomendados, encontre os contras de cada estudo abaixo:

:::row:::
    :::column:::
        ![Acima do arm](images/AboveArm.gif)<br>
        **Acima do arm**<br>
        1 – Difícil manter um bom acompanhamento de mão<br>
        2 – Causa a fatiga do usuário devido à posição anormal
    :::column-end:::
    :::column:::
        ![Acima dos dedos](images/AboveFingers.gif)<br>
        **Acima dos dedos**<br>
        1 - Estouro da mão devido à segurando a mão por um longo tempo<br>
        2 – Problemas de acompanhamento da mão no índice e nos dedos médios
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Acima da mão central](images/handCenter.gif)<br>
        **Acima da mão central**<br>
        1 - Problemas de acompanhamento de mão devido à sobreposição de mãos<br>
        2 - Estouro da mão devido à mão segurando as mãos por muito tempo para interagir com menus
    :::column-end:::
    :::column:::
        ![Ponta do dedo ](images/TopFingerTip.gif) **superior do dedo superior**<br>
        1 - Problemas de acompanhamento de mão<br>
        2 - Ressatirção da mão ao segurar a mão acima da postura normal<br>
        3 – Problemas ao pressionar botões com outros dedos por acidente devido ao espaço limitado entre os dedos
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ![Parte traseira do Arm](images/BackOfTheArm.gif)<br>
        **Parte traseira do arm**<br>
        1 – Pode disparar o botão Página Principal por acidente<br>
        2 - Não é uma posição natural ou confortável
    :::column-end:::
    :::column:::
    :::column-end:::
:::row-end:::

<br>

---

## <a name="hand-menu-in-mrtk-mixed-reality-toolkit-for-unity"></a>Menu de mão no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity

**[O MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e cenas de exemplo para o menu de mão. O script do solucionador HandConstraintPalmUp permite anexar quaisquer objetos às mãos com várias opções configuráveis. Os exemplos de menu de mão do MRTK incluem opções úteis, como a mão simples e o requisito de olhar para evitar a ativação falsa.

* [Documentações do menu Mão](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/hand-menu)
* [Cena de exemplo do menu mão](https://github.com/microsoft/MixedRealityToolkit-Unity/blob/main/Assets/MRTK/Examples/Demos/HandTracking/Scenes/HandMenuExamples.unity)

Você pode experimentar exemplos de menu manual no HoloLens 2 com o aplicativo Hub de Exemplos do MRTK.

* [Cena do menu Mão no Hub de Exemplos do MRTK](https://www.microsoft.com/p/mrtk-examples-hub/9mv8c39l2sj4?activetab=pivot:overviewtab)

<br>

---

## <a name="see-also"></a>Confira também

* [Cursores](cursors.md)
* [Raio de mão](point-and-commit.md)
* [Botão](button.md)
* [Objeto interativo](interactable-object.md)
* [Caixa delimitadora e barra de aplicativos](app-bar-and-bounding-box.md)
* [Manipulação](direct-manipulation.md)
* [Menu lateral](hand-menu.md)
* [Menu próximo](near-menu.md)
* [Coleção de objetos](object-collection.md)
* [Comando de voz](voice-input.md)
* [Teclado](keyboard.md)
* [Dica de ferramenta](tooltip.md)
* [Slate](slate.md)
* [Controle deslizante](slider.md)
* [Sombreador](shader.md)
* [Mural e tag-along](billboarding-and-tag-along.md)
* [Exibindo o progresso](progress.md)
* [Magnetismo de superfície](surface-magnetism.md)