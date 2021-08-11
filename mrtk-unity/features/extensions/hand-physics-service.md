---
title: Serviço de física da mão
description: documentação para usar o serviço de extensão de física manual no MRTK
author: RogPodge
ms.author: roliu
ms.date: 01/12/2021
keywords: Unity, HoloLens, HoloLens 2, Realidade misturada, desenvolvimento, MRTK,
ms.openlocfilehash: f54f8dabddba03bc279a090bf1c62b25656e64109b3b5671a4ed50d070445f14
ms.sourcegitcommit: a1c086aa83d381129e62f9d8942f0fc889ffcab0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/05/2021
ms.locfileid: "115221722"
---
# <a name="hand-physics-service"></a>Serviço de física da mão

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

### <a name="use-palm-kinematic-body"></a>Usar o corpo do Palm cinemática

Controla se o serviço tentará criar uma instância de um pré-fabricado no conjunto de Palm.

### <a name="palm-kinematic-body-prefab"></a>Pré-fabricado do corpo de Palm cinemática

Quando `UsePalmKinematicBody` está habilitado, esse é o pré-fabricado que ele criará. Assim como `FingerTipKinematicBodyPrefab` , esse pré-fabricado requer:

- Um componente rigidbody, com iscinemática habilitada
- Um colisor
- componente `JointKinematicBody`

## <a name="how-to-use-the-service"></a>Como usar o serviço

Uma vez habilitado, use `IsTrigger` a propriedade do colisor para receber eventos de colisão de todos os 10 dígitos (e Palms, se estiverem habilitados).
