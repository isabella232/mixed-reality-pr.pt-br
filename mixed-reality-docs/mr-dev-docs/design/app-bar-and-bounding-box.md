---
title: Caixa delimitadora e barra de aplicativos
description: A barra aplicativo é um menu de nível de objeto que contém uma série de botões exibidos na borda inferior dos limites de um holograma.
author: radicalad
ms.author: adlinv
ms.date: 06/07/2019
ms.topic: article
keywords: Windows Mixed Reality, barra de aplicativos, caixa delimitada, headset de realidade misturada, headset de realidade misturada do Windows, headset de realidade virtual, HoloLens, MRTK, Kit de Ferramentas de Realidade Misturada
ms.openlocfilehash: 750fb238e5b7f22998a86f71607498c8f6982076
ms.sourcegitcommit: 9ae76b339968f035c703d9c1fe57ddecb33198e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2021
ms.locfileid: "110600515"
---
# <a name="bounding-box-and-app-bar"></a>Caixa delimitadora e barra de aplicativos
![Delimitação é a interface padrão para manipulação de objetos na Realidade Misturada.](images/UX_Hero_BoundingBox.jpg)<br>
<br>

## <a name="what-is-the-bounding-box"></a>O que é a caixa Delimitando?

Delimitação é a interface padrão para manipulação de objetos na Realidade Misturada. Esse recurso fornece ao usuário uma indicação visual de que o objeto está atualmente ajustável. No HoloLens 2, a caixa delimitada funciona com manipulação direta da mão e responde à proximidade do dedo do usuário. Ele mostra comentários visuais para ajudar o usuário a perceber a distância do objeto.

:::row:::
    :::column:::
        ### <a name="scaling-an-objectbr"></a>Dimensionamento de um objeto<br>
        Os cantos da caixa delimitada dizem ao usuário que o objeto pode ser dimensionado. Os alças seguem um padrão amplamente compreendido para ajustar a escala. Essa indicação visual mostra aos usuários a área total do objeto , mesmo que ele não seja visível fora de um modo de ajuste. Sem esse recurso, um objeto encaixado em outro objeto ou superfície pode parecer se comportar como se houvesse espaço ao redor dele que não deveria estar lá.<br>
        <br>
        *Loop de vídeo: Dimensionamento de um objeto por meio de caixa delimitada*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Ponto de vista do HoloLens de dimensionamento de um objeto por meio de caixa delimitada](images/HoloLens2_BoundingBox.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="rotating-an-objectbr"></a>Girar um objeto<br>
        As acessível retangulares verticais nas bordas da caixa delimitada são indicadores de rotação. Isso fornece ao usuário um ajuste mais fino sobre seus hologramas colocados. Eles não só podem ajustar e dimensionar, mas agora girar também.<br>
        <br>
        *Loop de vídeo: girar um objeto por meio de uma caixa delimitada*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Ponto de vista do HoloLens da rotação de um objeto por meio de caixa delimitada](images/HoloLens2_BoundingBox_Rotate.gif)<br>
    :::column-end:::
:::row-end:::

<br>

:::row:::
    :::column:::
        ### <a name="visual-feedback-on-hand-proximity-on-hololens-2br"></a>Comentários visuais sobre proximidade manual no HoloLens 2<br>
        No HoloLens 2, há uma indicação visual extra, que pode ajudar a percepção de profundidade do usuário. Um anel próximo à ponta do dedo aparece e é escalado para baixo à medida que a ponta do dedo se aproxima do objeto. O anel eventualmente convergirá para um ponto quando o estado pressionado for atingido. Essa governança visual ajuda o usuário a entender a distância do objeto.<br>
        <br>
        *Loop de vídeo: exemplo de comentários visuais com base na proximidade de uma caixa delimitada*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Comentários visuais sobre proximidade da mão](images/HoloLens2_Proximity.gif)<br>
    :::column-end:::
:::row-end:::

<br>

**Para o desenvolvimento de aplicativos do Unity, consulte Caixa delimitativa no Kit de Ferramentas de [Realidade Misturada –Unity.](https://microsoft.github.io/MixedRealityToolkit-Unity/Documentation/README_BoundingBox.html)**

<br>

---

## <a name="what-is-the-app-bar"></a>O que é a barra de aplicativos?

A barra aplicativo é um menu de nível de objeto, que contém uma série de botões exibidos na borda inferior dos limites de um holograma. Esse padrão é normalmente usado para permitir que os usuários removam e ajustem hologramas. A barra aplicativo foi projetada principalmente como uma maneira de gerenciar objetos colocados no ambiente de um usuário. Juntamente com a caixa delimitada, um usuário tem controle total sobre onde e como os objetos são orientados na realidade misturada.

:::row:::
    :::column:::
        ### <a name="the-app-bar-follows-the-userbr"></a>A barra aplicativo segue o usuário<br>
        Como esse padrão é usado com objetos que estão bloqueados pelo mundo, à medida que um usuário se move ao redor do objeto, a barra de aplicativos sempre será exibida no lado dos objetos mais próximos do usuário. Embora tecnicamente não seja o mesmo, esse recurso efetivamente atinge o mesmo resultado. Impedir que a posição de um usuário oclua ou bloqueie a funcionalidade que, de outra forma, estaria disponível em um local diferente em seu ambiente. <br>
        <br>
        *Loop de vídeo: passeando em torno de um holograma, a barra de aplicativos segue*
    :::column-end:::
        :::column:::
        ![space](images/spacer-20x582.png)<br>
       ![Passeando em torno de um holograma. A barra Aplicativo segue.](images/HoloLens2_AppBarFollowing.gif)<br>
    :::column-end:::
:::row-end:::

<br>


## <a name="bounding-box-in-mrtk-mixed-reality-toolkit-for-unity"></a>Caixa delimitativa no MRTK (Kit de Ferramentas de Realidade Misturada) para Unity
**[O MRTK](https://github.com/Microsoft/MixedRealityToolkit-Unity)** fornece scripts e pré-fabs para a caixa Delimitadores e a barra de aplicativos. Você pode adicionar uma caixa Delimitando atribuindo o script BoundingBox.cs a qualquer objeto.

* [MRTK – Caixa delimitada](/windows/mixed-reality/mrtk-unity/features/ux-building-blocks/bounding-box)


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