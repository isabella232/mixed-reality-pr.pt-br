---
title: Configurações de experiência
description: Documentação sobre as diferentes configurações de experiência do MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: ab3a449b064d4a1c8f2bf76154f7a25c688693e1
ms.sourcegitcommit: f338b1f121a10577bcce08a174e462cdc86d5874
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2021
ms.locfileid: "113177350"
---
# <a name="experience-settings"></a>Configurações de experiência

Um dos desafios da criação da interface do usuário para Realidade Misturada é o alinhamento entre diferentes experiências. Com o MRTK, você pode definir o e o para sua cena, configurará o seguinte para se comportar adequadamente `Target Experience Scale` para a escala de `Content Offset` destino.

- Conteúdo da cena de realidade misturada
- Sistema de limite

  ![Experiência Configurações perfil de configuração do MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>Escala de experiência de destino

A **Escala de Experiência de** Destino especifica o ambiente para o qual a experiência foi projetada. Ele pode assumir os valores a seguir.

* *OrientationOnly* – uma experiência que utiliza apenas a orientação do headset e está alinhada à gravidade. A origem do sistema de coordenadas está no nível da cabeça.
* *Seated* – uma experiência projetada para uso de sedados. A origem do sistema de coordenadas está no nível do chão.
* *Permanente* – uma experiência projetada para uso estacionário. A origem do sistema de coordenadas está no nível do chão.
* *Sala* – uma experiência projetada para dar suporte à movimentação em uma sala. A origem do sistema de coordenadas está no nível do chão.
* *Mundo* – uma experiência projetada para utilizar e mover-se pelo mundo físico. A origem do sistema de coordenadas está no nível da cabeça.

## <a name="content-offset"></a>Deslocamento de conteúdo

Esse parâmetro especifica a altura acima do chão para deslocamento do conteúdo da cena de [realidade](scene-content.md) misturada quando o tipo **de** alinhamento é definido como Alinhar com a escala **de experiência**
