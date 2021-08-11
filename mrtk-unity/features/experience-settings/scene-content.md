---
title: Conteúdo da cena de Realidade Misturada
description: Documentação sobre o componente de conteúdo da cena de realidade misturada
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 9980c01b47c3d7d451fda886b4645664f06f204da9967c186382878be947d64f
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115193218"
---
# <a name="mixed-reality-scene-content"></a>Conteúdo da cena de Realidade Misturada

Ao adicionar o MRTK a uma cena, um `MixedRealitySceneContent` gameobject é criado. Esse objeto serve como um local dedicado para colocar e insinuar o conteúdo da Realidade Misturada para garantir que ele seja dimensionado adequadamente em várias experiências diferentes. O gameobject tem um monobehavior **MixedRealitySceneContent** equivalente, que pode ser configurado por meio do parâmetro **Alignment Type.** Esse parâmetro pode assumir os valores a seguir.

* *AlignWithExperienceScale* – alinha o  conteúdo com base na escala da experiência de destino e no **deslocamento** de conteúdo definidos na experiência do perfil de configuração [Configurações](experience-settings.md)
* *AlignWithHeadHeight* – alinha o conteúdo à posição y da cabeça do usuário, que é o local da câmera principal.


  ![Objeto de conteúdo de cena de realidade misturada criado no Editor](../images/experience-settings/MixedRealitySceneContent.png)
