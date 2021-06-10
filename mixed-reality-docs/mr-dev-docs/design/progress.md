---
title: Exibindo o progresso
description: Saiba como os controles de progresso fornece comentários ao usuário de que uma operação de execução longa está em andamento em seus aplicativos de realidade misturada.
author: cre8ivepark
ms.author: dongpark
ms.date: 03/21/2018
ms.topic: article
keywords: Windows Mixed Reality, design, controles, interface do usuário, experiência do usuário, indicador de progresso, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: 01f032efb887ecfc6f8d66683fb954cd0574a4f3
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600545"
---
# <a name="progress-indicator"></a>Indicador de progresso

<br>

<img src="images/MRTK_ProgressIndicator.gif" alt="Progress ring example in HoloLens" width="940px">

Um controle de progresso fornece comentários de que uma operação de execução longa está em andamento. Quando um indicador de progresso está visível, os usuários podem ver o tempo de espera e não podem interagir com o aplicativo.

<br>

---

## <a name="types-of-progress"></a>Tipo de progresso

É importante fornecer ao usuário informações sobre o que está acontecendo. Na realidade misturada, os usuários podem ser facilmente desacodados pelo ambiente físico ou objetos se seu aplicativo não tiver bons comentários visuais. Para situações que levam alguns segundos, como quando os dados estão sendo carregados ou uma cena está sendo atualizada, é uma boa ideia mostrar um indicador visual. Há duas opções para mostrar ao usuário que uma operação está em andamento – uma barra **progresso** ou um **anel progresso.**

:::row:::
    :::column:::
        ### <a name="progress-barbr"></a>Barra de progresso<br>
        Uma barra Progresso mostra o percentual concluído de uma tarefa. Ele deve ser usado durante uma operação cuja duração é conhecida (determinada), mas seu progresso não deve bloquear a interação do usuário com o aplicativo.<br>
        <br>
        *Imagem: exemplo de barra de progresso no HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Exemplo de barra de progresso no HoloLens](images/640px-progressbar.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-ringbr"></a>Anel de progresso<br>
        Um anel Progress só tem um estado indeterminado e deve ser usado quando a interação do usuário é bloqueada até que a operação seja concluída.<br>
        <br>
        *Imagem: exemplo de anel de progresso no HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Exemplo de anel de progresso no dispositivo HoloLens](images/640px-progressring.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

:::row:::
    :::column:::
        ### <a name="progress-with-a-custom-objectbr"></a>Progresso com um objeto personalizado<br>
        Você pode adicionar à personalidade e à identidade da marca do aplicativo personalização do controle Progresso com seus próprios objetos 2D/3D personalizados.<br>
        <br>
        *Imagem: Progresso com exemplo de malha personalizada no HoloLens*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Progresso com exemplo de malha personalizada no HoloLens](images/640px-progresscustom.jpg)<br>
    :::column-end:::
:::row-end:::

<br>

---

## <a name="best-practices"></a>Práticas recomendadas

* Adoce [](billboarding-and-tag-along.md) fortemente a marcação ou a marcação à exibição de Progresso, pois o usuário pode facilmente mover a cabeça para o espaço vazio e perder o contexto. Seu aplicativo pode parecer que ele teve um problema se o usuário não conseguir ver nada. A marcação e a marcação são criadas no pré-fab Progresso.
* É sempre bom fornecer informações de status sobre o que está acontecendo com o usuário. O prefab Progresso fornece vários estilos visuais, incluindo o progresso do tipo de anel padrão do Windows para fornecer status. Você também pode usar uma malha personalizada com uma animação se quiser que o estilo do seu progresso se alinhe à marca do aplicativo.

<br>

---

## <a name="progress-indicator-in-mrtk-mixed-reality-toolkit-for-unity"></a>Indicador de progresso no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity

* [MRTK – Pré-requisitos do indicador de progresso](https://github.com/microsoft/MixedRealityToolkit-Unity/tree/main/Assets/MRTK/SDK/Features/UX/Prefabs/ProgressIndicators)
* [MRTK – Serviço de transição de cena](/windows/mixed-reality/mrtk-unity/features/extensions/scene-transition-service)


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