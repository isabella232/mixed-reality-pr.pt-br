---
title: SceneContent
description: Documentação sobre o componente de conteúdo da cena de realidade misturada
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: fb4f575b6846695de07decb49146a59d3da843e0
ms.sourcegitcommit: a5afc24a4887880e394ef57216b8fd9de9760004
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2021
ms.locfileid: "110647764"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="36c37-104">Conteúdo da cena de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="36c37-104">Mixed Reality Scene Content</span></span>

<span data-ttu-id="36c37-105">Ao adicionar o MRTK a uma cena, um `MixedRealitySceneContent` gameobject é criado.</span><span class="sxs-lookup"><span data-stu-id="36c37-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="36c37-106">Esse objeto serve como um local dedicado para colocar e insinuar o conteúdo da Realidade Misturada para garantir que ele seja dimensionado adequadamente em várias experiências diferentes.</span><span class="sxs-lookup"><span data-stu-id="36c37-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="36c37-107">O gameobject tem um monobehavior **MixedRealitySceneContent** equivalente, que pode ser configurado por meio do parâmetro **Alignment Type.**</span><span class="sxs-lookup"><span data-stu-id="36c37-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="36c37-108">Esse parâmetro pode assumir os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="36c37-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="36c37-109">*AlignWithExperienceScale* – alinha o  conteúdo com base na escala da experiência de destino e no deslocamento de conteúdo **definido** nas Configurações de Experiência do perfil [de configuração](experience-settings.md)</span><span class="sxs-lookup"><span data-stu-id="36c37-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="36c37-110">*AlignWithHeadHeight* – alinha o conteúdo à posição y da cabeça do usuário, que é o local da câmera principal.</span><span class="sxs-lookup"><span data-stu-id="36c37-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![Objeto de conteúdo de cena de realidade misturada criado no Editor](../images/experience-settings/MixedRealitySceneContent.png)