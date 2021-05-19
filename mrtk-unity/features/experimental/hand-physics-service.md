---
title: Serviço de extensão de física manual
description: Descrição os serviços de extensão de física.
author: CDiaz-MS
ms.author: cadia
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 401a9d31ed3fbbe0c3e02cb95ffebb024f882fd9
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110143430"
---
# <a name="hand-physics-extension-services"></a>Distribuir serviços de extensão de física

O serviço de física manual permite eventos de colisão de corpo rígidos e interações com mãos articuladas.

## <a name="getting-started-with-hand-physics-extension-service"></a>Introdução ao serviço de extensão de física manual

Adicione o serviço de física à mão à lista de serviços de extensão e use o perfil padrão.

Uma vez habilitado, use a propriedade istrigger de qualquer colisor para receber eventos de colisão de todos os 10 dígitos (e Palms, se estiverem habilitados).

### <a name="prerequisites"></a>Pré-requisitos

- Habilitou o serviço de extensão
- Atribua um pré-fabricado apropriado ao conjunto de dedos/Palm.

## <a name="recommendations"></a>Recomendações

Embora o serviço seja padronizado para a camada "padrão", é recomendável usar uma camada separada para objetos HandPhysics. Caso contrário, pode haver colisões indesejadas e/ou raycasts imprecisas.
