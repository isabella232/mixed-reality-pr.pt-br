---
title: Exemplos de interação com a mão
description: Exemplos de interação com a mão no MRTK
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, Desenvolvimento, MRTK, Interações com a Mão, Controle de Limites, Botões Pressionáveis,
ms.openlocfilehash: 7926c8bdd525af24a26e2f4c87257dca7628956a
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177445"
---
# <a name="hand-interaction-examples"></a><span data-ttu-id="a2767-104">Exemplos de interação com a mão</span><span class="sxs-lookup"><span data-stu-id="a2767-104">Hand interaction examples</span></span>

![Exemplos de interação com a mão 1](../images/hand-interaction-examples/MRTK_HandInteractionExamples.png)

<span data-ttu-id="a2767-106">A **cena de exemplo HandInteractionExamples** contém vários tipos de interações e controles de interface do usuário que realçam a entrada de mão articulada.</span><span class="sxs-lookup"><span data-stu-id="a2767-106">The **HandInteractionExamples** example scene contains various types of interactions and UI controls that highlight articulated hand input.</span></span> <span data-ttu-id="a2767-107">Com a simulação de entrada do MRTK, você pode experimentar interações de acompanhamento manual no editor do Unity.</span><span class="sxs-lookup"><span data-stu-id="a2767-107">With MRTK's input simulation, you can experience hand-tracking interactions in Unity editor.</span></span> 

<span data-ttu-id="a2767-108">**A cena HandInteractionExamples** está incluída no pacote Exemplos do MRTK.</span><span class="sxs-lookup"><span data-stu-id="a2767-108">**HandInteractionExamples** scene is included in the MRTK's Examples package.</span></span> <span data-ttu-id="a2767-109">Você pode baixar e importar o **pacote de exemplos Toolkit Realidade Misturada** por meio da [Ferramenta de Recursos de Realidade Misturada](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span><span class="sxs-lookup"><span data-stu-id="a2767-109">You can download and import **Mixed Reality Toolkit Examples** package through [Mixed Reality Feature Tool](/windows/mixed-reality/develop/unity/welcome-to-mr-feature-tool)</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_MRFT.png" width="550" alt="Example Package 1"><br/>

<span data-ttu-id="a2767-110">No Unity, use o menu Janela > Gerenciador de Pacotes > no Project > Personalizado e selecione **Realidade Misturada Toolkit Exemplos**.</span><span class="sxs-lookup"><span data-stu-id="a2767-110">In Unity, use the menu Window > Package Manager > In Project > Custom and select **Mixed Reality Toolkit Examples**.</span></span> <span data-ttu-id="a2767-111">Clique **no botão Importar Project** ao lado de Demonstrações – **HandTracking.**</span><span class="sxs-lookup"><span data-stu-id="a2767-111">Click **Import into Project** button next to **Demos - HandTracking**.</span></span> <span data-ttu-id="a2767-112">Você poderá encontrar a cena **HandInteractionExamples** na pasta Ativos > Exemplos.</span><span class="sxs-lookup"><span data-stu-id="a2767-112">You will be able to find **HandInteractionExamples** scene under Assets > Samples folder.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_2.png" width="300" alt="Example Package 2"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_3.png" width="650" alt="Example Package 3"><br/>

<img src="../images/hand-interaction-examples/MRTK_Examples_Package_4.png" width="650" alt="Example Package 4"><br/>

* <span data-ttu-id="a2767-113">Se você não usar a Ferramenta de Recursos de Realidade Misturada, poderá baixar e importar diretamente **Microsoft.MixedReality.Toolkit. Unity.Examples.unitypackage** da página [GitHub versão do MRTK](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span><span class="sxs-lookup"><span data-stu-id="a2767-113">If you don't use Mixed Reality Feature Tool, you can directly download and import **Microsoft.MixedReality.Toolkit.Unity.Examples.unitypackage** from [MRTK GitHub's release page](https://github.com/microsoft/MixedRealityToolkit-Unity/releases)</span></span>

> [!NOTE]
> <span data-ttu-id="a2767-114">Esta cena de exemplo usa *TextMesh Pro*.</span><span class="sxs-lookup"><span data-stu-id="a2767-114">This example scene uses *TextMesh Pro*.</span></span> <span data-ttu-id="a2767-115">Para abrir a cena, clique *em 'Importar TMP Essentials'* quando o respectivo prompt for mostrado durante a importação da cena.</span><span class="sxs-lookup"><span data-stu-id="a2767-115">To open the scene, click *'Import TMP Essentials'* when the respective prompt is shown during the import of the scene.</span></span> <span data-ttu-id="a2767-116">Em seguida, o Unity importa o TextMesh Pro pacotes.</span><span class="sxs-lookup"><span data-stu-id="a2767-116">Unity will then import TextMesh Pro packages.</span></span>

<img src="../images/hand-interaction-examples/MRTK_Examples_TMP2.png" width="450" alt="Example TMP2">



<span data-ttu-id="a2767-117">Você pode experimentar esses componentes **na cena HandInteractionExamples**</span><span class="sxs-lookup"><span data-stu-id="a2767-117">You can experience these components in **HandInteractionExamples** scene</span></span>

- [<span data-ttu-id="a2767-118">Botão de pressão</span><span class="sxs-lookup"><span data-stu-id="a2767-118">Pressable button</span></span>](../ux-building-blocks/button.md)
- [<span data-ttu-id="a2767-119">Controle de limites</span><span class="sxs-lookup"><span data-stu-id="a2767-119">Bounds control</span></span>](../ux-building-blocks/bounds-control.md)
- [<span data-ttu-id="a2767-120">Manipulador de objetos</span><span class="sxs-lookup"><span data-stu-id="a2767-120">Object manipulator</span></span>](../ux-building-blocks/object-manipulator.md)
- [<span data-ttu-id="a2767-121">Slate</span><span class="sxs-lookup"><span data-stu-id="a2767-121">Slate</span></span>](../ux-building-blocks/slate.md)
- [<span data-ttu-id="a2767-122">Controle deslizante</span><span class="sxs-lookup"><span data-stu-id="a2767-122">Slider</span></span>](../ux-building-blocks/sliders.md)
- [<span data-ttu-id="a2767-123">Teclado do sistema</span><span class="sxs-lookup"><span data-stu-id="a2767-123">System keyboard</span></span>](../ux-building-blocks/system-keyboard.md)
