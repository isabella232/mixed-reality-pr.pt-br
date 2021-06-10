---
title: Exemplos de interação à mão
description: Exemplos de interação manual no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK, interações de mão, controle de limites, botões prensados,
ms.openlocfilehash: 229933dfd2414e485da6c1a77a2ffb08c9982249
ms.sourcegitcommit: 2f69fb62eb81f91e655d7b55306b0550a1162496
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/10/2021
ms.locfileid: "111908406"
---
# <a name="hand-interaction-examples-scene"></a><span data-ttu-id="c2d32-104">Exemplos de interação de mão cena</span><span class="sxs-lookup"><span data-stu-id="c2d32-104">Hand interaction examples scene</span></span>

![Exemplos de interação manual 1](../images/hand-interaction-examples/MRTK_HandInteractionExamples.png)

<span data-ttu-id="c2d32-106">A cena de exemplo **HandInteractionExamples** contém vários tipos de interações e controles de interface do usuário que realçam a entrada de mão articulada.</span><span class="sxs-lookup"><span data-stu-id="c2d32-106">The **HandInteractionExamples** example scene contains various types of interactions and UI controls that highlight articulated hand input.</span></span> <span data-ttu-id="c2d32-107">Com a simulação de entrada do MRTK, você pode experimentar interações de acompanhamento manual no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="c2d32-107">With MRTK's input simulation, you can experience hand-tracking interactions in Unity editor.</span></span> 

<span data-ttu-id="c2d32-108">A cena **HandInteractionExamples** está incluída no pacote de exemplos do MRTK.</span><span class="sxs-lookup"><span data-stu-id="c2d32-108">**HandInteractionExamples** scene is included in the MRTK's Examples package.</span></span> <span data-ttu-id="c2d32-109">Você pode baixar e importar **exemplos do kit de ferramentas de realidade misturados** pacote por meio da [ferramenta de recurso de realidade mista](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="c2d32-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="c2d32-110">No Unity, use a janela de menu > o Gerenciador de pacotes > no projeto > personalizado e selecione **exemplos de kit de ferramentas de realidade misturada**.</span><span class="sxs-lookup"><span data-stu-id="c2d32-110">In Unity, use the menu Window > Package Manager > In Project > Custom and select **Mixed Reality Toolkit Examples**.</span></span> <span data-ttu-id="c2d32-111">Clique **no botão importar no projeto** ao lado de **demos-HandTracking**.</span><span class="sxs-lookup"><span data-stu-id="c2d32-111">Click **Import into Project** button next to **Demos - HandTracking**.</span></span> <span data-ttu-id="c2d32-112">Você poderá encontrar a cena do **HandInteractionExamples** em ativos > pasta de exemplos.</span><span class="sxs-lookup"><span data-stu-id="c2d32-112">You will be able to find **HandInteractionExamples** scene under Assets > Samples folder.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

* <span data-ttu-id="c2d32-113">Se você não usar a ferramenta de recurso de realidade misturada, poderá baixar e importar diretamente **o Microsoft. MixedReality. Toolkit. Unity. examples. unitypackage** da [página de lançamento do MRTK GitHub](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="c2d32-113">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

> [!NOTE]
> <span data-ttu-id="c2d32-114">Esta cena de exemplo usa *Textmesh pro*.</span><span class="sxs-lookup"><span data-stu-id="c2d32-114">This example scene uses *TextMesh Pro*.</span></span> <span data-ttu-id="c2d32-115">Para abrir a cena, clique em *' importar os fundamentos do tmp '* quando o respectivo prompt for mostrado durante a importação da cena.</span><span class="sxs-lookup"><span data-stu-id="c2d32-115">To open the scene, click *'Import TMP Essentials'* when the respective prompt is shown during the import of the scene.</span></span> <span data-ttu-id="c2d32-116">Em seguida, o Unity importará os pacotes do textmesh pro.</span><span class="sxs-lookup"><span data-stu-id="c2d32-116">Unity will then import TextMesh Pro packages.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_TMP2.png" width="450" alt="Example TMP2">



<span data-ttu-id="c2d32-117">Você pode experimentar esses componentes na cena do **HandInteractionExamples**</span><span class="sxs-lookup"><span data-stu-id="c2d32-117">You can experience these components in **HandInteractionExamples** scene</span></span>

- [<span data-ttu-id="c2d32-118">Botão de pressão</span><span class="sxs-lookup"><span data-stu-id="c2d32-118">Pressable button</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="c2d32-119">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="c2d32-119">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="c2d32-120">Manipulador de objeto</span><span class="sxs-lookup"><span data-stu-id="c2d32-120">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)
- [<span data-ttu-id="c2d32-121">Slate</span><span class="sxs-lookup"><span data-stu-id="c2d32-121">Slate</span></span>](../ux-building-blocks/slate.md)
- [<span data-ttu-id="c2d32-122">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="c2d32-122">Slider</span></span>](../ux-building-blocks/sliders.md)
- [<span data-ttu-id="c2d32-123">Teclado do sistema</span><span class="sxs-lookup"><span data-stu-id="c2d32-123">System keyboard</span></span>](../ux-building-blocks/system-keyboard.md)
