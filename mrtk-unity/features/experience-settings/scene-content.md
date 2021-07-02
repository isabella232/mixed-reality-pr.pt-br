---
title: Conteúdo da cena de realidade misturada
description: Documentação sobre o componente de conteúdo de cena de realidade misturada
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 7ed81352537bec799721b49c4e2d3d55066c5316
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177345"
---
# <a name="mixed-reality-scene-content"></a><span data-ttu-id="f139c-104">Conteúdo da cena de realidade misturada</span><span class="sxs-lookup"><span data-stu-id="f139c-104">Mixed Reality scene content</span></span>

<span data-ttu-id="f139c-105">Ao adicionar MRTK a uma cena, um `MixedRealitySceneContent` gameobject é criado.</span><span class="sxs-lookup"><span data-stu-id="f139c-105">When adding MRTK to a scene, a `MixedRealitySceneContent` gameobject is created.</span></span> <span data-ttu-id="f139c-106">Esse objeto serve como um local dedicado para posicionar e instanciar o conteúdo da realidade misturada para garantir que ele seja dimensionado adequadamente em várias experiências diferentes.</span><span class="sxs-lookup"><span data-stu-id="f139c-106">This object serves as a dedicated place to place and instantiate Mixed Reality content to ensure that it scales appropriately across many different experiences.</span></span> <span data-ttu-id="f139c-107">O gameobject tem um equivalente **MixedRealitySceneContent** , que pode ser configurado por meio do parâmetro de **tipo Alignment** .</span><span class="sxs-lookup"><span data-stu-id="f139c-107">The gameobject has an equivalent **MixedRealitySceneContent** monobehavior, which can be configured via the **Alignment Type** parameter.</span></span> <span data-ttu-id="f139c-108">Esse parâmetro pode assumir os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="f139c-108">This parameter can take on the following values.</span></span>

* <span data-ttu-id="f139c-109">*AlignWithExperienceScale* -alinha o conteúdo com base na **escala de experiência de destino** e no deslocamento de **conteúdo** definido na experiência do perfil de configuração [Configurações](experience-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f139c-109">*AlignWithExperienceScale* - Aligns the content based on the **Target Experience Scale** and **Content Offset** set in the configuration profile's [Experience Settings](experience-settings.md)</span></span>
* <span data-ttu-id="f139c-110">*AlignWithHeadHeight* -alinha o conteúdo à posição y da cabeça do usuário, que é o local da câmera principal.</span><span class="sxs-lookup"><span data-stu-id="f139c-110">*AlignWithHeadHeight* - Aligns the content to the y position of the user's head, which is the location of the main camera.</span></span>


  ![Objeto de conteúdo de cena de realidade misturada criado no editor](../images/experience-settings/MixedRealitySceneContent.png)
