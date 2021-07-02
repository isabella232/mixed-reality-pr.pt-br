---
title: Busca conjunta de mão
description: Busca conjunta manual no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 0beac2dae5aa12cf07f193dab9a6db7bc7ddf2e5
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113175361"
---
# <a name="hand-joint-chaser"></a><span data-ttu-id="fd1d8-104">Busca conjunta de mão</span><span class="sxs-lookup"><span data-stu-id="fd1d8-104">Hand joint chaser</span></span>

<span data-ttu-id="fd1d8-105">![Buscas conjuntas de mão Esta cena ](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) de exemplo demonstra como usar o Solucionador para anexar objetos às junções de mão.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-105">![Hand joint chasers](../images/hand-joint-chaser/MRTK_HandJointChaser_Main.jpg) This example scene demonstrates how to use Solver to attach objects to the hand joints.</span></span>

## <a name="example-scene"></a><span data-ttu-id="fd1d8-106">Cena de exemplo</span><span class="sxs-lookup"><span data-stu-id="fd1d8-106">Example scene</span></span>

<span data-ttu-id="fd1d8-107">Você pode encontrar a cena de exemplo **HandJointChaserExample** cena na `Assets/MRTK/Examples` pasta em `Demos/Input/Scenes/` .</span><span class="sxs-lookup"><span data-stu-id="fd1d8-107">You can find the example scene **HandJointChaserExample** scene in the `Assets/MRTK/Examples` folder under `Demos/Input/Scenes/`.</span></span>

## <a name="solver-handler"></a><span data-ttu-id="fd1d8-108">Manipulador do solucionador</span><span class="sxs-lookup"><span data-stu-id="fd1d8-108">Solver handler</span></span>

<span data-ttu-id="fd1d8-109">Clique **em Objeto Rastreado para Referência** e selecione **Junção de Mão Esquerda** ou **Junção de Mão Direita.**</span><span class="sxs-lookup"><span data-stu-id="fd1d8-109">Click **Tracked Object To Reference** and select **Hand Joint Left** or **Hand Joint Right**.</span></span> <span data-ttu-id="fd1d8-110">Você poderá ver o **drop-down Da Junta de Mão** Rastreada.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-110">You will be able to see **Tracked Hand Joint** drop down.</span></span> <span data-ttu-id="fd1d8-111">Na lista lista listada, você pode selecionar uma junção específica para acompanhar. Esta cena de exemplo usa o Solucionador de Exibição Radial para fazer com que um objeto siga o objeto de destino.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-111">From the drop down list, you can select specific joint to track. This example scene uses Radial View Solver to make an object follow the target object.</span></span> <span data-ttu-id="fd1d8-112">Consulte [a página Solucionador](../ux-building-blocks/solvers/solver.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="fd1d8-112">See [Solver](../ux-building-blocks/solvers/solver.md) page for more details.</span></span>

![Solucionador de conjunto de mãos](../images/hand-joint-chaser/MRTK_Solver_HandJoint.jpg)
