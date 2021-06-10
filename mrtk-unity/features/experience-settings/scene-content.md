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
# <a name="mixed-reality-scene-content"></a>Conteúdo da cena de realidade misturada

Ao adicionar o MRTK a uma cena, um `MixedRealitySceneContent` gameobject é criado. Esse objeto serve como um local dedicado para colocar e insinuar o conteúdo da Realidade Misturada para garantir que ele seja dimensionado adequadamente em várias experiências diferentes. O gameobject tem um monobehavior **MixedRealitySceneContent** equivalente, que pode ser configurado por meio do parâmetro **Alignment Type.** Esse parâmetro pode assumir os valores a seguir.

* *AlignWithExperienceScale* – alinha o  conteúdo com base na escala da experiência de destino e no deslocamento de conteúdo **definido** nas Configurações de Experiência do perfil [de configuração](experience-settings.md)
* *AlignWithHeadHeight* – alinha o conteúdo à posição y da cabeça do usuário, que é o local da câmera principal.


  ![Objeto de conteúdo de cena de realidade misturada criado no Editor](../images/experience-settings/MixedRealitySceneContent.png)