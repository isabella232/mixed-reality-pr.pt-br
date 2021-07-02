---
title: Utilitário de permuta de ativos
description: Documentação sobre como usar o utilitário de troca de ativos no MRTK para Unity.
author: hferrone
ms.author: v-hferrone
ms.date: 03/9/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade Misturada, desenvolvimento, MRTK
ms.openlocfilehash: 50ef252913575988b5f377dd9ff92f9e9ade3a72
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113176165"
---
# <a name="asset-swap-utility"></a><span data-ttu-id="9d898-104">Utilitário de permuta de ativos</span><span class="sxs-lookup"><span data-stu-id="9d898-104">Asset swap utility</span></span>

<span data-ttu-id="9d898-105">Encontrar e substituir é onipresente ao trabalhar em ferramentas de criação de texto e conteúdo.</span><span class="sxs-lookup"><span data-stu-id="9d898-105">Find and replace is ubiquitous when working in text and content creation tools.</span></span> <span data-ttu-id="9d898-106">Quando você precisa trocar muitos ativos em uma cena do Unity, é aí que o [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) e o editor podem ajudar.</span><span class="sxs-lookup"><span data-stu-id="9d898-106">When you need to swap many assets within a Unity scene this is where the [AssetSwapUtility](xref:Microsoft.MixedReality.Toolkit.Utilities.Editor.AssetSwapUtility) [ScriptableObject](https://docs.unity3d.com/Manual/class-ScriptableObject.html) and editor can lend a hand.</span></span> <span data-ttu-id="9d898-107">O utilitário está incluído no `Microsoft.MixedReality.Toolkit.Unity.Tools` pacote.</span><span class="sxs-lookup"><span data-stu-id="9d898-107">The utility is included with the `Microsoft.MixedReality.Toolkit.Unity.Tools` package.</span></span>

<span data-ttu-id="9d898-108">O salva todas as ações de encontrar e substituir como um ScriptableObject para que seja trival para alternar entre si ou salvar "temas" de permuta para `AssetSwapUtility` uso futuro.</span><span class="sxs-lookup"><span data-stu-id="9d898-108">The `AssetSwapUtility` saves all find and replace actions as a ScriptableObject so that it is trival to swap back and forth or save swap "themes" for future use.</span></span>

## <a name="swapping-assets"></a><span data-ttu-id="9d898-109">Troca de ativos</span><span class="sxs-lookup"><span data-stu-id="9d898-109">Swapping assets</span></span>

<span data-ttu-id="9d898-110">A troca de ativos é fácil depois que você cria um `AssetSwapCollection` .</span><span class="sxs-lookup"><span data-stu-id="9d898-110">Swapping assets is easy once you have created a `AssetSwapCollection`.</span></span> <span data-ttu-id="9d898-111">Vamos demonstrar o uso trocando dois cubos vermelhos por duas esferas azuis em uma cena.</span><span class="sxs-lookup"><span data-stu-id="9d898-111">Let's demonstrate use by swapping two red cubes with two blue spheres in a scene.</span></span> <span data-ttu-id="9d898-112">Primeiro, adicione dois cubos vermelhos à cena que usam o cubo padrão do Unity e o `MRTK_Standard_Red` material.</span><span class="sxs-lookup"><span data-stu-id="9d898-112">First add two red cubes to your scene that use the default Unity cube and the `MRTK_Standard_Red` material.</span></span>

<span data-ttu-id="9d898-113">Para criar um `AssetSwapCollection` , navegue até Realidade **Misturada Toolkit > Utilitários > Criar Coleção de Troca de Ativos**.</span><span class="sxs-lookup"><span data-stu-id="9d898-113">To create an `AssetSwapCollection`, navigate to **Mixed Reality Toolkit > Utilities > Create Asset Swap Collection**.</span></span> <span data-ttu-id="9d898-114">Com o `AssetSwapCollection` selecionado, preencha as propriedades conforme visto na imagem abaixo:</span><span class="sxs-lookup"><span data-stu-id="9d898-114">With the `AssetSwapCollection` selected fill out the properties as seen in the below image:</span></span>

![Coleção de permuta de ativos no editor do Unity](images/asset-swap-img-01.png)

<span data-ttu-id="9d898-116">Em seguida, selecione "Blue Spheres" na lista suspenso "Tema Selecionado" e clique em "Aplicar".</span><span class="sxs-lookup"><span data-stu-id="9d898-116">Next select "Blue Spheres" from the "Selected Theme" dropdown and hit "Apply."</span></span> <span data-ttu-id="9d898-117">Todos os cubos vermelhos em sua cena devem ser substituídos por esferas azuis.</span><span class="sxs-lookup"><span data-stu-id="9d898-117">All red cubes within your scene should be replaced with blue spheres.</span></span>

![Coleção de permuta de ativos no editor do Unity com o tema selecionado realçada](images/asset-swap-img-02.png)

<span data-ttu-id="9d898-119">Neste exemplo, realizamos uma substituição de cena completa, mas você pode substituir partes da cena alterando o "Modo de Seleção".</span><span class="sxs-lookup"><span data-stu-id="9d898-119">In this example we performed a full scene replacement but you may replace portions of your scene by changing the "Selection Mode."</span></span> <span data-ttu-id="9d898-120">Você também pode trocar de volta para cubos vermelhos selecionando "Cubos Vermelhos" na lista suspenso "Tema Selecionado" e clicando em "Aplicar" novamente.</span><span class="sxs-lookup"><span data-stu-id="9d898-120">You may also swap back to red cubes by selecting "Red Cubes" from the "Selected Theme" dropdown and hitting "Apply" again.</span></span>

> [!NOTE]
> <span data-ttu-id="9d898-121">É possível trocar qualquer tipo de ativo, como arquivos de áudio, fontes, pré-fabs, etc. O `AssetSwapUtility` executará algumas verificações de sanidade para garantir que você está trocando para tipos semelhantes.</span><span class="sxs-lookup"><span data-stu-id="9d898-121">It's possible to swap any asset type such as audio files, fonts, prefabs, etc. The `AssetSwapUtility` will perform a few sanity checks to ensure you are swapping to similar types.</span></span>
