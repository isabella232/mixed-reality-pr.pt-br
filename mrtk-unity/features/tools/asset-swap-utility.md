---
title: Utilitário de permuta de ativos
description: Documentação sobre o uso do utilitário de permuta de ativos no MRTK para Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, realidade misturada, desenvolvimento, MRTK
ms.openlocfilehash: c277cadffb356b93ffc359233b0b8307f43e8d57
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110144131"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="f8e91-104">Utilitário de permuta de ativos</span><span class="sxs-lookup"><span data-stu-id="f8e91-104">Asset swap utility</span></span>

<span data-ttu-id="f8e91-105">Localizar e substituir é onipresente ao trabalhar em ferramentas de criação de conteúdo e texto.</span><span class="sxs-lookup"><span data-stu-id="f8e91-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="f8e91-106">Quando você precisa trocar muitos ativos em uma cena de Unity, é aí que o [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) e o editor podem dar uma mão.</span><span class="sxs-lookup"><span data-stu-id="f8e91-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="f8e91-107">O utilitário está incluído no `Microsoft.MixedReality.Toolkit.Unity.Tools` pacote.</span><span class="sxs-lookup"><span data-stu-id="f8e91-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="f8e91-108">O `AssetSwapUtility` salva todas as ações localizar e substituir como um ScriptableObject para que ela seja trivalda para alternar ou salvar "temas" de troca para uso futuro.</span><span class="sxs-lookup"><span data-stu-id="f8e91-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="f8e91-109">Troca de ativos</span><span class="sxs-lookup"><span data-stu-id="f8e91-109">Swapping assets</span></span>

<span data-ttu-id="f8e91-110">A troca de ativos é fácil depois de você ter criado um `AssetSwapCollection` .</span><span class="sxs-lookup"><span data-stu-id="f8e91-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="f8e91-111">Vamos demonstrar o uso alternando dois cubos vermelhos com dois antiazuls em uma cena.</span><span class="sxs-lookup"><span data-stu-id="f8e91-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="f8e91-112">Primeiro, adicione dois cubos vermelhos à sua cena que usam o cubo do Unity padrão e o `MRTK_Standard_Red` material.</span><span class="sxs-lookup"><span data-stu-id="f8e91-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="f8e91-113">Para criar um `AssetSwapCollection` , navegue até **Mixed Reality Toolkit > Utilities > criar coleção de permuta de ativos**.</span><span class="sxs-lookup"><span data-stu-id="f8e91-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="f8e91-114">Com o `AssetSwapCollection` preenchimento selecionado, as propriedades são mostradas na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="f8e91-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Coleção de permuta de ativos no editor do Unity](images/asset-swap-img-01.png)

<span data-ttu-id="f8e91-116">Em seguida, selecione "azul" aqui na lista suspensa "tema selecionado" e pressione "aplicar".</span><span class="sxs-lookup"><span data-stu-id="f8e91-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="f8e91-117">Todos os cubos vermelhos em sua cena devem ser substituídos por meio azul aqui.</span><span class="sxs-lookup"><span data-stu-id="f8e91-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Coleção de permuta de ativos no editor do Unity com o tema selecionado realçado](images/asset-swap-img-02.png)

<span data-ttu-id="f8e91-119">Neste exemplo, realizamos uma substituição de cena completa, mas você pode substituir partes da sua cena alterando o "modo de seleção".</span><span class="sxs-lookup"><span data-stu-id="f8e91-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="f8e91-120">Você também pode alternar de volta para cubos vermelhos selecionando "cubos vermelhos" na lista suspensa "tema selecionado" e pressionando "aplicar" novamente.</span><span class="sxs-lookup"><span data-stu-id="f8e91-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="f8e91-121">É possível trocar qualquer tipo de ativo, como arquivos de áudio, fontes, pré-fabs, etc. O `AssetSwapUtility` executará algumas verificações de sanidade para garantir que você está trocando para tipos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="f8e91-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>