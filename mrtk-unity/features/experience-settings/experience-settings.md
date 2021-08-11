---
title: Configurações da experiência
description: Documentação sobre as diferentes configurações de experiência para MRTK
author: RogPodge
ms.author: roliu
ms.date: 04/13/2021
ms.localizationpriority: medium
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK
monikerRange: '>= mrtkunity-2021-05'
ms.openlocfilehash: 19d812ccfa9c0317e40dee2b7d03220848782cef955ba859a150b4f4adc8aa99
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115203238"
---
# <a name="experience-settings"></a>Configurações da experiência

Um dos desafios de criar a interface do usuário para realidade misturada está se alinhando em experiências diferentes. Com o MRTK, você pode definir o `Target Experience Scale` e o `Content Offset` para sua cena, configurar o seguinte para se comportar adequadamente para a escala de destino.

- Conteúdo da cena de realidade misturada
- Sistema de limite

  ![experiência Configurações no perfil de configuração do MRTK](../images/experience-settings/ExperienceSettings.png)

## <a name="target-experience-scale"></a>Escala de experiência de destino

A **escala de experiência de destino** especifica o ambiente para o qual a experiência foi projetada. Pode assumir os valores a seguir.

* *OrientationOnly* – uma experiência que utiliza apenas a orientação do headset e está alinhada à gravidade. A origem do sistema de coordenadas está no nível do cabeçalho.
* *Sentado* -uma experiência projetada para uso em estação. A origem do sistema de coordenadas está no nível do piso.
* Em *pé* – uma experiência projetada para uso estacionário. A origem do sistema de coordenadas está no nível do piso.
* *Sala* -uma experiência projetada para dar suporte à movimentação ao longo de uma sala. A origem do sistema de coordenadas está no nível do piso.
* *Mundo* – uma experiência projetada para utilizar e percorrer o mundo físico. A origem do sistema de coordenadas está no nível do cabeçalho.

## <a name="content-offset"></a>Deslocamento de conteúdo

Esse parâmetro especifica a altura acima do andar para deslocar o [conteúdo da cena de realidade misturada](scene-content.md) quando o **tipo de alinhamento** está definido para **alinhar com a escala de experiência**
