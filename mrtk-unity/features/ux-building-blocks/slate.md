---
title: Slate
description: Documentação no Slate no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, Slate,
ms.openlocfilehash: 6bc1f18c71367ce05aadae0ff3f8aa51fd17d10c943022525fc5043d8d7989a2
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115224004"
---
# <a name="slate"></a>Slate

![Slate](../images/slate/MRTK_Slate_Main.png)

O pré-fabricado Slate oferece um controle de estilo de janela fino para exibir conteúdo 2D, por exemplo, texto sem formatação ou artigos, incluindo mídia. Ele oferece uma barra de título que é possível, bem como *seguir* e *fechar* a funcionalidade. A janela de conteúdo pode ser rolada por meio de entrada de mão articulada.

## <a name="how-to-use-a-slate-control"></a>Como usar um controle Slate

Um controle Slate é composto pelos seguintes elementos:

* **TitleBar**: a barra de título inteira na parte superior da Slate.
* **Título**: a área de título no lado esquerdo da barra de título.
* **Botões**: a área do botão no lado direito da barra de título.
* **Placa** traseira: o lado de trás do Tablet.
* **ContentQuad**: o conteúdo é atribuído como material. O exemplo usa um material de exemplo ' PanContent '.

<img src="../images/slate/MRTK_SlateStructure.jpg" width="650" alt="Slate Structure in the Unity editor">

## <a name="bounds-control"></a>Controle de limites

Um controle Slate contém um script de controle de limites para dimensionamento e rotação. Para obter mais informações sobre controle de limites, consulte a página de [controle limites](bounds-control.md) .

<img src="../images/slate/MRTK_Slate_BB.jpg" width="650" alt="Slate BB">

## <a name="buttons"></a>Botões

Um Slate padrão oferece dois botões como padrão no canto superior direito da barra de título:

* **Siga-me**: alterna os componentes do resolvedor orbital para que o objeto Slate siga o usuário.
* **Fechar**: desabilita o objeto Slate.

<img src="../images/slate/MRTK_Slate_Buttons.jpg" width="650" alt="Slate Button">

## <a name="scripts"></a>Scripts

Em geral, o `NearInteractionTouchable.cs` script deve ser anexado a qualquer objeto destinado a receber eventos de toque do `IMixedRealityTouchHandler` .

<img src="../images/slate/MRTK_Slate_Scripts.png" alt="Slate Structure">

* `HandInteractionPan.cs` Esse script lida com a entrada de mão articulada para tocar e mover o conteúdo no *ContentQuad* do Tablet.

* `HandInteractionPanZoom.cs`: Além da interação de panorâmica, esse script dá suporte a zoom de duas mãos.

<img src="../images/slate/MRTK_Slate_PanZoom.png" width="500" alt="Slate Pan Zooming">
