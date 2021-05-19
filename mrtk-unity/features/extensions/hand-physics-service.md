---
title: Visão geral do serviço de física
description: documentação para usar o serviço de extensão de física manual no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: 751aec148d3a40da4728d2fdd60a60402b59a4de
ms.sourcegitcommit: c0ba7d7bb57bb5dda65ee9019229b68c2ee7c267
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2021
ms.locfileid: "110145087"
---
# <a name="hand-physics-extension-service"></a>Serviço de extensão de física manual

![Serviço de extensão de física manual](../images/hand-physics/MRTK_UX_HandPhysics_Main.jpg)

O serviço de física manual permite eventos de colisão de corpo rígidos e interações com mãos articuladas.

## <a name="enabling-the-extension"></a>Habilitando a extensão

Para habilitar a extensão, abra o perfil do RegisteredServiceProvider. Clique `Register a new Service Provider` para adicionar uma nova configuração. No campo tipo de componente, selecione HandPhysicsService. No campo perfil de configuração, selecione o perfil de física de mão padrão incluído com a extensão.

## <a name="profile-options"></a>Opções de perfil

### <a name="hand-physics-layer"></a>Camada física à mão

Controla a camada à qual as junções de mão instanciada serão acessadas.

Embora o serviço seja padronizado para a camada "padrão" (0), é recomendável usar uma camada separada para objetos de física de mão. Caso contrário, pode haver colisões indesejadas e/ou raycasts imprecisas.

### <a name="finger-tip-kinematic-body-prefab"></a>Pré-fabricado do corpo cinemática da dica de dedo

Controla qual pré-fabricado é instanciado em mãos. Para que o serviço funcione conforme o esperado, o pré-fabricado requer:

- Um componente rigidbody, com iscinemática habilitada
- Um colisor
- componente `JointKinematicBody`

### <a name="use-palm-kinematic-body"></a>Usar o corpo kinematic da mão

Controla se o serviço tentará insinuar um pré-fab na junção da mão.

### <a name="palm-kinematic-body-prefab"></a>Pré-fab de corpo kinematic da mão

Quando `UsePalmKinematicBody` está habilitado, esse é o pré-fab que ele insinuou. Assim como `FingerTipKinematicBodyPrefab` , esse pré-fab requer:

- Um componente rigidbody, com isKinematic habilitado
- Um colisor
- componente `JointKinematicBody`

## <a name="how-to-use-the-service"></a>Como usar o serviço

Uma vez habilitado, use a propriedade de qualquer colisor para receber eventos de colisão de todos os 10 dígitos (e as mãos, se eles `IsTrigger` estão habilitados).
