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
# <a name="mixed-reality-scene-content"></a>Conteúdo da cena de realidade misturada

Ao adicionar MRTK a uma cena, um `MixedRealitySceneContent` gameobject é criado. Esse objeto serve como um local dedicado para posicionar e instanciar o conteúdo da realidade misturada para garantir que ele seja dimensionado adequadamente em várias experiências diferentes. O gameobject tem um equivalente **MixedRealitySceneContent** , que pode ser configurado por meio do parâmetro de **tipo Alignment** . Esse parâmetro pode assumir os valores a seguir.

* *AlignWithExperienceScale* -alinha o conteúdo com base na **escala de experiência de destino** e no deslocamento de **conteúdo** definido na experiência do perfil de configuração [Configurações](experience-settings.md)
* *AlignWithHeadHeight* -alinha o conteúdo à posição y da cabeça do usuário, que é o local da câmera principal.


  ![Objeto de conteúdo de cena de realidade misturada criado no editor](../images/experience-settings/MixedRealitySceneContent.png)
