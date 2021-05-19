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
# <a name="hand-joint-chaser-example"></a><span data-ttu-id="f81bf-104">Exemplo de Chase conjunta de mão</span><span class="sxs-lookup"><span data-stu-id="f81bf-104">Hand joint chaser example</span></span>

<span data-ttu-id="f81bf-105">![Mãos de junção conjuntas ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) Este exemplo de cena demonstra como usar o Solver para anexar objetos às junções de mão.</span><span class="sxs-lookup"><span data-stu-id="f81bf-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="f81bf-106">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="f81bf-106">Example scene</span></span>

<span data-ttu-id="f81bf-107">Você pode encontrar a cena **HandJointChaserExample** de exemplo de cena na `Assets/MRTK/Examples` pasta em `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="f81bf-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="f81bf-108">Manipulador de solveres</span><span class="sxs-lookup"><span data-stu-id="f81bf-108">Solver handler</span></span>

<span data-ttu-id="f81bf-109">Clique em **objeto rastreado para referência** e selecione **mão conjunta à esquerda** ou à **direita**.</span><span class="sxs-lookup"><span data-stu-id="f81bf-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="f81bf-110">Você poderá ver a lista suspensa em conjunto com o **controle de mão** .</span><span class="sxs-lookup"><span data-stu-id="f81bf-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="f81bf-111">Na lista suspensa, você pode selecionar conjunto específico a ser acompanhado. Esta cena de exemplo usa o solucionador de exibição radial para fazer com que um objeto siga o objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="f81bf-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="f81bf-112">Consulte a página do [Solver](../ux-building-blocks/solvers/solver.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="f81bf-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Solucionador de junção conjunta](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
