---
title: Acompanhamento da junta da mão
description: Conjunto de totais conjunta no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f9db1c4a2ca1959a35c541e87c9a4a01bc41637e
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144620"
---
# <a name="hand-joint-chaser-example"></a>Exemplo de Chase conjunta de mão

![Mãos de junção conjuntas ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) Este exemplo de cena demonstra como usar o Solver para anexar objetos às junções de mão.

## <a name="example-scene"></a>Cena de exemplo

Você pode encontrar a cena **HandJointChaserExample** de exemplo de cena na `Assets/MRTK/Examples` pasta em `Demos/Input/Scenes/` .

## <a name="solver-handler"></a>Manipulador de solveres

Clique em **objeto rastreado para referência** e selecione **mão conjunta à esquerda** ou à **direita**. Você poderá ver a lista suspensa em conjunto com o **controle de mão** . Na lista suspensa, você pode selecionar conjunto específico a ser acompanhado. Esta cena de exemplo usa o solucionador de exibição radial para fazer com que um objeto siga o objeto de destino. Consulte a página do [Solver](../ux-building-blocks/solvers/solver.md) para obter mais detalhes.

![Solucionador de junção conjunta](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
