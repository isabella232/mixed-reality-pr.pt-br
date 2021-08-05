---
title: Acompanhamento da articulação da mão
description: Conjunto de totais conjunta no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 376dcd0e1ff01d6e9020aedf35ed2bb2b7b39fa8a119d125aa8c3a96bf0024fe
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115189550"
---
# <a name="hand-joint-chaser"></a>Acompanhamento da articulação da mão

![Mãos de junção conjuntas ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) Este exemplo de cena demonstra como usar o Solver para anexar objetos às junções de mão.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar a cena **HandJointChaserExample** de exemplo de cena na `Assets/MRTK/Examples` pasta em `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Manipulador de solveres

Clique em **objeto rastreado para referência** e selecione **mão conjunta à esquerda** ou à **direita**. Você poderá ver a lista suspensa em conjunto com o **controle de mão** . Na lista suspensa, você pode selecionar conjunto específico a ser acompanhado. Esta cena de exemplo usa o solucionador de exibição radial para fazer com que um objeto siga o objeto de destino. Consulte a página do [Solver](../ux-building-blocks/solvers/solver.md) para obter mais detalhes.

![Solucionador de junção conjunta](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
